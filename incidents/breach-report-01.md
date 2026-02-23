# Incident Report: SQL Injection & Data Exfiltration (IR-2024-001)

## 📝 Executive Summary

On 03 November 2024, the SOC detected unauthorized database queries originating from an external IP. An attacker exploited a vulnerability in the 'User Login' form to bypass authentication and exfiltrate 500 rows of customer data.

## 🛡️ Incident Profile

* Severity: 🔴 HIGH
* Status: Resolved / Post-Mortem
* Vector: Web Application (SQLi)
* Affected Assets: Production Customer Database (DB-PROD-01)

## 🕵️ Analysis & Timeline

| Time (UTC) | Action | Description |
| :--- | :--- | :--- |
| 14:02 | Detection | SIEM flagged 50+ 'Union Select' statements in web logs. |
| 14:10 | Containment | Web server isolated from the database network. |
| 14:45 | Eradication | Vulnerable login script patched; SQL parameters implemented. |

## 🛠️ Root Cause

The login.php script was using string concatenation for SQL queries rather than Prepared Statements, allowing the attacker to inject malicious SQL commands.

## 🔓 Mitigation & Lessons Learned

1. Immediate: Implemented parameterized queries.
2. Long-term: Integrated OWASP ZAP into the GitHub Actions pipeline to scan for SQLi before every deployment.
