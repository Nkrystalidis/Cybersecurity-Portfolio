# Network Traffic Analysis: DNS & ICMP Incident

## Scenario
Several clients reported that they were unable to access the company website (`www.yummyrecipesforme.com`) and received a "destination port unreachable" error in their browsers. The network security team needed to investigate the incident to determine the root cause of the outage.

## Task
As a Cybersecurity Analyst, my objective was to analyze network traffic using a protocol analyzer tool (`tcpdump`) to identify which network protocol and service were affected during the incident. 

## Action
- Captured and inspected network data packets during the reported outage window (around 1:24 p.m.).
- Analyzed the initial outgoing query from the local computer to the DNS server, which was sent via the **UDP** protocol.
- Examined the server's response logs, identifying an **ICMP** echo reply returning the specific error message: *"udp port 53 unreachable"*.
- Correlated the port number (Port 53) to its corresponding service to determine the exact point of failure.
- [Network Log Analysis](tcpdump-log.png)

## Outcome & Recommendations
The network analysis revealed that the DNS service was the root cause of the outage. The browser successfully sent a UDP packet to resolve the domain name, but the DNS server returned an ICMP error indicating that Port 53 was unreachable. 

**Root Cause Analysis:** The DNS server was either offline, no service was listening on Port 53, or a misconfigured firewall was actively blocking incoming DNS traffic. 

**Next Steps:** I recommended immediately checking the firewall configuration rules to ensure Port 53 is open and contacting the system administrator to verify the operational status of the DNS server.
