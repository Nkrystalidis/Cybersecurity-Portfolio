# Network Hardening & Security Risk Assessment

## Scenario
A social media organization recently experienced a major data breach that compromised sensitive customer information, including names and addresses. A post-incident network inspection revealed four critical vulnerabilities: employees sharing passwords, a database using default admin credentials, firewalls lacking inbound/outbound traffic filtering rules, and a complete absence of Multi-Factor Authentication (MFA). 

## Task
As a Security Analyst, my objective was to conduct a security risk assessment, analyze the identified vulnerabilities, and recommend robust network hardening practices to secure the infrastructure and prevent future data breaches.

## Action
- Analyzed the organization's network architecture and assessed the risk impact of the four identified vulnerabilities.
- Mapped the vulnerabilities to corresponding security controls based on industry best practices for network hardening.
- Developed a targeted remediation plan prioritizing Identity and Access Management (IAM) and network traffic filtering to establish a defense-in-depth architecture.

## Outcome & Recommendations
To effectively mitigate the risks and harden the network, I recommended the immediate implementation of the following security controls:

1. **Firewall Rules (Access Control Lists):** Configure explicit inbound and outbound ACLs on all corporate firewalls to drop unauthorized traffic and prevent data exfiltration. This must be monitored and updated regularly.
2. **Multi-Factor Authentication (MFA):** Enforce MFA for all user accounts, especially for database administrators. This neutralizes the threat of intercepted or brute-forced passwords by requiring a secondary physical or biometric verification token.
3. **Strict Password Policies:** Implement enforced IAM policies that strictly prohibit password sharing and default credentials, combined with secure password hashing for storage.
