# Network Traffic Analysis: Deep Packet Inspection with Wireshark

## Scenario
As a security analyst, I was tasked with investigating network traffic generated during a web browsing session. By analyzing a packet capture file (`sample.pcap`) in Wireshark, the objective was to identify the communicating hosts, inspect protocol headers across the OSI layers, trace DNS resolutions, and search packet payloads for specific command-line utility indicators.

## Task
Utilize Wireshark display filters and deep packet inspection to isolate specific IP addresses, MAC addresses, UDP/TCP ports, and cleartext payload strings within captured network traffic.

## Action & Wireshark Filters Applied

### 1. Protocol Identification & Baseline Inspection
- Loaded `sample.pcap` into Wireshark and analyzed the initial traffic flow, identifying **SSH**, **TCP**, **DNS**, and **ICMP** (`Echo (ping) request`) packets.

### 2. IP & MAC Address Traffic Filtering
Isolated traffic associated with specific hosts at both the Network (Layer 3) and Data Link (Layer 2) levels using the following display filters:
```text
ip.addr == 142.250.1.139
ip.src == 142.250.1.139
ip.dst == 142.250.1.139
eth.addr == 42:01:ac:15:e0:02
Inspected Packet 64 (172.21.224.2 ➔ 142.250.1.139), verifying the underlying TCP protocol operating over Source Port 49652 and Destination Port 80 (HTTP).
3. DNS Query & Resolution Analysis
Filtered for UDP-based Domain Name System traffic to trace domain resolution:

Plaintext
udp.port == 53
Expanded the Domain Name System (query) and Answers subtrees, confirming that the client queried opensource.google.com, which resolved to the IP address 142.250.1.139.

4. TCP Header & Payload Inspection
Filtered for standard unencrypted web traffic and searched the packet payload for specific user-agent/command indicators:

Plaintext
tcp.port == 80
tcp contains "curl"
Conducted deep packet inspection on the initial HTTP/TCP packet destined for 169.254.169.254, extracting key header metrics:

Frame Length: 54 bytes

IPv4 Header Length: 20 bytes

Time to Live (TTL): 64

Isolated HTTP requests initiated via the curl command-line tool using payload string matching.

Outcome
Successfully reconstructed the network session, mapped the DNS resolution of opensource.google.com (142.250.1.139), extracted Layer 2–4 header metrics, and detected automated curl web requests within the packet payloads. This lab demonstrates practical Blue Team proficiency in Wireshark display filtering and packet-level forensic analysis.
