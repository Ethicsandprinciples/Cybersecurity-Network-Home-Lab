# Lab 3: Live Packet Capture & Protocol Analysis with tcpdump

## Objective
Utilize `tcpdump` on Linux to capture live network traffic, analyze ICMP/DNS protocol layers, filter specific ports and flags, and write raw packet streams to `.pcap` files for offline analysis.

## Infrastructure & Topology
* **Analysis Endpoint:** Debian 12 (LAN)
* **Traffic Sources:** ICMP (8.8.8.8), DNS (Port 53), HTTP
* **Tools:** `tcpdump`, `dig`, `ping`

## Execution Steps
1. **ICMP Traffic Capture:** Executed `sudo tcpdump -i any icmp -n` to capture echo requests and replies while issuing ping commands.
2. **Protocol Filtering & Header Analysis:** Executed `sudo tcpdump -i any port 53 -n -v` to capture verbose UDP DNS queries generated via `dig example.com`.
3. **PCAP File Generation:** Wrote 20 raw network frames to disk using `sudo tcpdump -i any -c 20 -w lab3_traffic.pcap`.
4. **Offline Packet Reading:** Verified `.pcap` integrity by parsing the file using `tcpdump -r lab3_traffic.pcap -n`.

## Screenshots
![ICMP Echo Capture](images/lab3_icmp_capture.png)
*Figure 1: Live tcpdump capture displaying ICMP echo requests and replies.*

![Verbose DNS Capture](images/lab3_dns_headers.png)
*Figure 2: Verbose tcpdump output inspecting UDP port 53 header flags and packet lengths.*

![PCAP Read Back](images/lab3_pcap_read.png)
*Figure 3: Saved packet capture file (lab3_traffic.pcap) read back and parsed via tcpdump.*
