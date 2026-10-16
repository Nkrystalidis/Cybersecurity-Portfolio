# Intrusion Detection System (IDS): Rule Triggers & Log Parsing with Suricata

## Scenario
As a security analyst, I was tasked with configuring the Suricata Intrusion Detection System (IDS) to monitor network traffic for suspicious HTTP requests. The objective was to validate a custom detection signature, execute the IDS against a packet capture (`sample.pcap`), verify generated alerts in `fast.log`, and parse structured event telemetry from `eve.json` using the `jq` CLI processor.

## Task
Inspect custom Suricata rule syntax, trigger detection signatures against captured network traffic, verify alerts, and filter JSON event streams by timestamps, flow IDs, protocols, and destination IPs.

---

## Action & Implementation Steps

### 1. Custom Rule Syntax Analysis
Inspected the custom detection signature defined in `custom.rules`:
```bash
cat custom.rules
```
* **Signature:**
  ```text
  alert http $HOME_NET any -> $EXTERNAL_NET any (msg:"GET on wire"; flow:established,to_server; content:"GET"; http_method; sid:12345; rev:3;)
  ```
* **Rule Breakdown:**
  * **Action & Protocol:** `alert http` generates an alert on matched HTTP traffic.
  * **Direction:** Traffic originating from `$HOME_NET` to `$EXTERNAL_NET` on any port.
  * **Rule Options:**
    * `flow:established,to_server`: Matches packets part of an established TCP connection flowing to the destination server.
    * `content:"GET"; http_method;`: Inspects the HTTP payload specifically for the `GET` request method.
    * `sid:12345; rev:3;`: Unique Signature ID and revision version.

### 2. Executing Suricata Inspection
Processed the sample packet capture file using the custom rule file with checksum verification disabled:
```bash
sudo suricata -r sample.pcap -S custom.rules -k none
```
* Suricata processed **200 packets (54,238 bytes)**, generating output files in `/var/log/suricata/` (`fast.log`, `eve.json`, `stats.log`, `suricata.log`).

### 3. Log Inspection (`fast.log`)
Examined the lightweight alert output file:
```bash
cat /var/log/suricata/fast.log
```
* **Alert 1:** `11/23/2022-12:38:34.624866 [**] [1:12345:3] GET on wire [**] [Priority: 3] {TCP} 172.21.224.2:49652 -> 142.250.1.139:80`
* **Alert 2:** `11/23/2022-12:38:58.958203 [**] [1:12345:3] GET on wire [**] [Priority: 3] {TCP} 172.21.224.2:58494 -> 142.250.1.102:80`

### 4. Advanced JSON Telemetry Parsing with `jq`
Leveraged the `jq` utility to format and extract specific alert indicators from `eve.json`:
```bash
# Pretty-print formatted JSON output
jq . /var/log/suricata/eve.json | less

# Compact extraction of core triage fields
jq -c "[.timestamp,.flow_id,.alert.signature,.proto,.dest_ip]" /var/log/suricata/eve.json
```
* Extracted specific connection flows:
  * Flow `695532248962789` destined for `142.250.1.139:80` (`opensource.google.com`).
  * Flow `726728458957928` destined for `142.250.1.102:80`.
* Filtered deep packet metadata for a single session:
```bash
jq "select(.flow_id==695532248962789)" /var/log/suricata/eve.json
```
  * **User-Agent:** `curl/7.74.0`
  * **HTTP Status Code:** `301`
  * **HTTP Hostname:** `opensource.google.com`

---

## Outcome
Successfully validated Suricata IDS rule syntax, triggered alerts against real-world packet captures, verified dual alert flows within legacy and modern log structures, and parsed JSON security telemetry via CLI data extraction. This lab demonstrates practical Blue Team proficiency in network intrusion monitoring, signature analysis, and alert triage.
