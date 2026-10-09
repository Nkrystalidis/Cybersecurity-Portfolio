# NIST Incident Report Analysis: DoS ICMP Ping Flood

## Scenario
A multimedia company offering web and graphic design services experienced a critical security event. A malicious actor launched a Denial of Service (DoS) attack via an ICMP ping flood, overwhelming the company's internal network. The attack exploited an unconfigured firewall, causing all network services to stop responding and completely halting internal operations for two hours.

## Task
As a Cybersecurity Analyst, my objective was to analyze the security event using the National Institute of Standards and Technology (NIST) Cybersecurity Framework (CSF). The goal was to document the incident lifecycle, identify the vulnerabilities, and integrate the analysis into a comprehensive security strategy to prevent future recurrences.

## Action (NIST CSF Application)
- **Identify:** Traced the root cause to an unconfigured firewall allowing unmitigated ICMP packets to overwhelm internal network resources.
- **Protect:** Hardened the network by implementing firewall rate-limiting for ICMP packets, enabling source IP verification to drop spoofed addresses, and deploying an IDS/IPS system.
- **Detect:** Configured network monitoring software to proactively detect abnormal traffic patterns and volumetric anomalies.
- **Respond:** Contained the attack by blocking incoming ICMP packets and temporarily offlining non-critical services to stabilize the network.
- **Recover:** Restored critical network services to full operational capacity within a two-hour window and verified network integrity.

## Outcome
The immediate incident response successfully neutralized the DoS attack and restored business continuity. The subsequent network hardening measures and IDS/IPS deployment have significantly fortified the organization's perimeter against future volumetric network attacks.
