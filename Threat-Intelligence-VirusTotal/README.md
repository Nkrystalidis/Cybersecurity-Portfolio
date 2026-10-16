# Threat Intelligence Investigation: Malware Hash Analysis with VirusTotal

## Scenario
A financial services company's Security Operations Center (SOC) detected an alert regarding an employee downloading a password-protected spreadsheet from an external email. Upon opening the file, unauthorized executable files were generated on the endpoint, triggering an Intrusion Detection System (IDS) alert. The suspicious executable was isolated, and its cryptographic SHA-256 hash was extracted for threat intelligence analysis.

## Objective
Analyze the extracted file hash using **VirusTotal** to confirm maliciousness, map observable Indicators of Compromise (IoCs) across the **Pyramid of Pain**, and provide actionable threat context for containment.

---

## Investigation Findings

### 1. Artifact Verification & Reputation
* **Target File:** `bfsvc.exe` (Size: 430.00 KB)
* **SHA-256 Hash:** `54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b`
* **Security Vendor Detection Ratio:** `40 / 60` vendors flagged the artifact as malicious.
* **Community Reputation Score:** `-293` (High Confidence Malicious)
* **Threat Classification:** Trojan / Backdoor
* **Identified Malware Families:** `trojan.flagpro/fragtor`, `Backdoor:Win/FlagPro.B`

### 2. Pyramid of Pain Mapping

| Pyramid Layer | Observable Indicator | Context / Impact |
| :--- | :--- | :--- |
| **Hash Values** | `54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b` | Uniquely identifies the `bfsvc.exe` binary. Can be trivial for attackers to modify. |
| **IP Addresses / URLs** | `http://org.misecure.com/index.html` | Flagged by 14 security engines as a malicious Command & Control (C2) endpoint. |
| **Domain Names** | `org.misecure.com` | External domain leveraged for payload communication and exfiltration callbacks. |
| **Host Artifacts** | `bfsvc.exe` dropping into process execution tree | Masquerading as a legitimate Windows Boot File Servicing utility (`bfsvc.exe`) to evade user detection. |
| **Tools & Techniques (TTPs)** | Phishing attachment (password-protected spreadsheet) execution | Password protection bypasses basic email gateway sandbox scanning; dropper spawns secondary executables. |

---

## Timeline of Events
* **1:11 p.m.:** Employee receives a targeted phishing email containing a password-protected spreadsheet attachment.
* **1:13 p.m.:** The employee enters the password provided in the email body, executing the macro/dropper.
* **1:15 p.m.:** Multiple unauthorized binaries (`bfsvc.exe`) are written to disk and executed.
* **1:20 p.m.:** Host-based IDS triggers an alert on anomalous binary execution, initiating the SOC triage workflow.

---

## Remediation & Containment Actions
1. **Endpoint Isolation:** Immediately quarantine the infected workstation from the internal network segment.
2. **Hash-Based Blocking:** Add the SHA-256 digest to the Endpoint Detection & Response (EDR) blocklist.
3. **Network Perimeter Filtering:** Block outbound traffic to domain `org.misecure.com` and URL `http://org.misecure.com/index.html` across firewalls and web proxies.
4. **Credential Reset:** Force credential rotation for the affected employee due to backdoor capabilities.
5. **Security Awareness:** Update email security gateways to quarantine encrypted archive/document attachments from external sources.
