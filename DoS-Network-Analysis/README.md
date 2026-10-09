# Network Traffic Analysis: DoS SYN Flood Attack

## Scenario
A travel agency's web server experienced a sudden outage, preventing employees and customers from accessing the sales webpage. Automated monitoring systems generated alerts indicating server timeouts. The incident required immediate network traffic analysis to identify the threat, mitigate the attack, and restore regular business operations.

## Task
As a Cybersecurity Analyst, my objective was to use a packet sniffer (Wireshark/tcpdump) to capture and analyze network packets in transit, diagnose the root cause of the connection timeout errors, and implement an immediate mitigation strategy.

## Action
- Analyzed TCP/HTTP logs and identified a massive spike in incoming traffic originating from a single unfamiliar IP address.
- Examined the packet headers and discovered a continuous flood of **TCP SYN requests** without the corresponding ACK responses.
- Diagnosed the event as a **Direct Denial of Service (DoS) SYN flood attack**, which was exhausting the server's resources and causing legitimate traffic to be dropped (HTTP 504 Gateway Time-out).
- Took the server offline temporarily to clear the half-open connections and recover system resources.
- Configured the corporate firewall to block the malicious IP address, immediately halting the attack.

## Outcome & Recommendations
The immediate firewall block successfully restored access to the web server for all legitimate users. However, relying solely on static IP blocking is a temporary fix, as threat actors can easily spoof different IP addresses to bypass the block.

**Strategic Next Steps:** 
To prevent future SYN flood attacks, I recommend implementing **SYN cookies** at the firewall or load balancer level. This mechanism allows the server to avoid allocating resources until the final ACK packet is received, effectively neutralizing resource exhaustion attacks while keeping the server responsive to legitimate clients.
