# 🛡️ Cybersecurity Portfolio: Practical Labs & Incident Reports

Welcome to my Cybersecurity technical portfolio. This repository contains hands-on laboratory investigations, command-line operations, network traffic analyses, and formal security assessments completed as part of my practical training and BSc (Hons) Cyber Security studies.

Each project is structured around real-world **SOC / Blue Team**, **System Administration (Linux/SQL)**, and **GRC (Governance, Risk, and Compliance)** scenarios, demonstrating practical problem-solving with industry-standard tools.

---

## 🛠️ Core Technical Competencies Demonstrated
* **Network Security & Traffic Analysis:** Packet sniffing and deep packet inspection (`Wireshark`, `tcpdump`), live traffic capture, DNS/ICMP troubleshooting, DoS (SYN Flood / Ping Flood) detection, and firewall hardening.
* **Linux System Administration & CLI:** Bash shell navigation, Identity and Access Management (IAM), file permissions (`chmod`), log parsing (`grep`, pipes), File Integrity Monitoring (`sha256sum`, `cmp`), and cryptography (`openssl` AES-256).
* **SQL for Threat Hunting (MariaDB):** Complex log filtering, temporal anomaly detection, logical operators, and multi-table correlation (`INNER`, `LEFT`, `RIGHT JOIN`) for incident response.
* **GRC & Incident Reporting:** Applying the **NIST Cybersecurity Framework (CSF)**, conducting vulnerability & risk assessments, and auditing compliance against **PCI DSS**, **GDPR**, and **SOC** standards.

---

## 📂 Portfolio Projects & Labs (Table of Contents)

### 🌐 1. Network Security & Traffic Analysis
| Project / Lab | Focus Area & Tools | Documentation |
| :--- | :--- | :--- |
| **Packet Capture with tcpdump** | Identifying interfaces (`ifconfig`, `tcpdump -D`), live traffic capture, exporting `.pcap` files, and inspecting hex/ASCII payloads. | [View Report](./Linux-Packet-Capture-tcpdump/README.md) |
| **Wireshark Deep Packet Inspection** | Analyzing `.pcap` files, filtering by IP/MAC/Port, tracing DNS queries (`udp.port == 53`), and payload inspection (`tcp contains "curl"`). | [View Report](./Wireshark-Packet-Analysis/README.md) |
| **DoS Network Analysis (SYN Flood)** | Packet header inspection, TCP 3-way handshake analysis, HTTP 504 timeout diagnosis, and SYN cookies mitigation. | [View Report](./DoS-Network-Analysis/README.md) \| [PDF](./DoS-Network-Analysis/Cybersecurity%20incident%20report.pdf) |
| **Network Traffic Analysis (DNS & ICMP)** | Investigating service outages using `tcpdump`, analyzing UDP Port 53 unreachable ICMP replies, and firewall rules. | [View Report](./Network-Traffic-Analysis/README.md) \| [PDF](./Network-Traffic-Analysis/Cybersecurity%20incident%20report%20network%20traffic%20analysis.pdf) |
| **Brute Force & Malware Injection Incident** | Sandbox dynamic analysis, tracing HTTP GET payload delivery, DNS redirection, and brute-force mitigation. | [View Report](./Malware-Injection-Incident/README.md) \| [PDF](./Malware-Injection-Incident/Malware-Injection-Incident-Report.pdf) |

---

### 🐧 2. Linux Administration, Cryptography & Auditing
| Project / Lab | Focus Area & Tools | Documentation |
| :--- | :--- | :--- |
| **Linux IAM & File Permissions** | Enforcing Principle of Least Privilege, auditing hidden files (`ls -la`), and modifying access control strings (`chmod`). | [View Report](./Linux-IAM-File-Permissions/README.md) \| [PDF](./Linux-IAM-File-Permissions/File%20permissions%20in%20Linux.pdf) |
| **Linux Security Log Analysis** | Parsing raw server logs (`grep`, piping `\|`) to detect unauthorized access attempts and audit IAM user changes. | [View Report](./Linux-Security-Log-Analysis/README.md) |
| **File Integrity Monitoring (Hashing)** | Generating SHA-256 digests (`sha256sum`), output redirection (`>>`), and byte-by-byte comparison (`cmp`) on EICAR files. | [View Report](./Linux-File-Integrity-Hashing/README.md) |
| **Data Decryption & Cryptography** | Locating hidden recovery instructions, cipher translation (`tr`), and symmetric file decryption using `openssl aes-256-cbc`. | [View Report](./Linux-Cryptography-Decryption/README.md) |

---

### 🗄️ 3. SQL Threat Hunting & Log Investigation
| Project / Lab | Focus Area & Tools | Documentation |
| :--- | :--- | :--- |
| **SQL Joins Incident Investigation** | Correlating `employees`, `machines`, and `log_in_attempts` tables using `INNER`, `LEFT`, and `RIGHT JOIN` queries. | [View Report](./SQL-Joins-Incident-Investigation/README.md) |
| **SQL Logical Operators Investigation** | Threat hunting with `AND`, `OR`, `NOT`, and `LIKE` wildcards to isolate after-hours failed logins and anomalous locations. | [View Report](./SQL-Logical-Operators-Investigation/README.md) |
| **SQL Log Filtering** | Sifting through bulk authentication logs using comparison operators (`>`, `>=`, `<`) and `BETWEEN` time windows. | [View Report](./SQL-Log-Filtering/README.md) |
| **SQL Security Investigation** | Retrieving OS patch timelines and building chronological incident timelines (`ORDER BY`) to spot brute-force patterns. | [View Report](./SQL-Security-Investigation/README.md) |

---

### 📋 4. GRC, Audits & NIST CSF Incident Reports
| Project / Lab | Focus Area & Tools | Documentation |
| :--- | :--- | :--- |
| **Botium Toys Internal Security Audit** | Comprehensive controls and compliance audit against **PCI DSS**, **GDPR**, and **SOC**, proposing RBAC & encryption. | [View Report](./Botium-Toys-Security-Audit/README.md) \| [PDF](./Botium-Toys-Security-Audit/Botium-Toys-Security-Audit.pdf) |
| **NIST CSF Incident Report (ICMP Flood)** | Applying NIST CSF core functions (*Identify, Protect, Detect, Respond, Recover*) to a volumetric DoS network outage. | [View Report](./NIST-Incident-Report-DoS/README.md) \| [PDF](./NIST-Incident-Report-DoS/Incident%20report%20analysis.pdf) |
| **Network Hardening & Risk Assessment** | Post-breach vulnerability assessment and remediation planning using ACL firewall rules, MFA, and IAM password policies. | [View Report](./Network-Hardening-Risk-Assessment/README.md) \| [PDF](./Network-Hardening-Risk-Assessment/Network-Hardening-Risk-Assessment.pdf) |
| **Threat Intelligence & Hash Analysis** | Analyzing malicious hashes (`bfsvc.exe`), C2 URLs (`org.misecure.com`), and mapping IoCs via VirusTotal & Pyramid of Pain. | [View Report](./Threat-Intelligence-VirusTotal/README.md) |
