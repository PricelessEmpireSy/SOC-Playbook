# Incident Response Playbook: Phishing Attempt

## 1. Detection & Analysis

* **Indicators of Compromise (IoCs):**
Check for mismatched URLs, suspicious sender domains, and urgent language.

* **Header Analysis:** Examine the `X-Distribution` and `Return-Path` headers in the email.

## 2. Containment

* Block the sender's IP/Domain at the firewall.
* Disable any compromised user accounts immediately.
* Reset passwords for affected users.

## 3. Eradication & Recovery

* Remove the malicious email from all user inboxes using PowerShell or Admin tools.
* Scan the affected machines for malware/backdoors.

graph TD
    A[Phishing Email Reported] -->
B{Link Clicked?}
    B -- No --> C[Delete Email & Block Sender]
    B -- Yes --> D[Isolate Host Device]
    D --> E[Reset User Credentials]
    E --> F[Scan for Persistence]
