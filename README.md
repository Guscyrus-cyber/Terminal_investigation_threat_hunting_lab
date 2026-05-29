
**Terminal Investigation and Threat Hunting Lab**

This lab focuses on terminal-based network and threat-hunting investigations performed against real datasets that were generated from live network activity on a personal MacBook Pro system. During this lab, multiple firewall and network-related datasets were created from the local machine, including network connection logs, listening port information, interface configurations, and packet capture traffic. These datasets were generated using native macOS networking and packet analysis tools in order to simulate realistic SOC and network security investigation scenarios using real system activity instead of artificial sample data.
In this lab, Investigations 1 through 14 focus on analyzing the previously generated datasets using Linux and macOS terminal investigation techniques. The investigations include examining active network sessions, identifying encrypted HTTPS communication, extracting remote IP addresses, counting active connections, identifying listening to services, analyzing packet capture traffic, monitoring DNS activity, and reviewing communication patterns between the local system and external hosts. These investigations simulate the type of analysis commonly performed by SOC analysts, firewall analysts, network defenders, and incident responders during threat-hunting and network monitoring operations.
Throughout the lab, command-line investigation techniques were used to extract and analyze meaningful security information from raw datasets created on the MacBook Pro environment. The investigation process demonstrates practical cybersecurity skills including network traffic analysis, packet inspection, service enumeration, connection analysis, exposure identification, and terminal-based threat hunting. The completed investigations provide foundational experience for future advanced analysis using tools such as Wireshark, Splunk Enterprise, Zeek, Suricata, and additional SOC monitoring and detection engineering workflows.

Please refer to images 1-4 in the repository for dataset been created.

**Investigation 1 — Find Active HTTPS Connections**

Command: grep "443" mac_netstat.log
identify encrypted HTTPS traffic, 
detect outbound secure sessions, 
inspect remote IP communication. 

Please refer to image 5

**Investigation 2 — Count Established Connections**

Command: grep "ESTABLISHED" mac_netstat.log | wc -l
count active sessions, 
measure network activity.

Please refer to image 6

**Investigation 3 — Extract Remote IP Addresses**

Command: grep ESTABLISHED mac_netstat.log | awk '{print $5}'
extract foreign/remote addresses, 
identify communication targets. 

Please refer to images 7-8 in the rep[ository.

**Investigation 4 — Show Unique Remote IPs**

Command: grep ESTABLISHED mac_netstat.log | awk '{print $5}' | sort | uniq
identify distinct external systems, 
reduce duplicate traffic.

Please refer to images 9-10 in the repository

**Investigation 5 — Count Top Remote Connections**

Command: grep ESTABLISHED mac_netstat.log | awk '{print $5}' | sort | uniq -c | sort -nr
Purpose:
identify most contacted systems, 
detect repetitive connections, 
threat hunting behavior. 

Please refer to images 11-12 in the repository.

**Investigation 6 — Find Listening Ports**

Command: grep LISTEN mac_netstat.log
identify exposed services, 
identify attack surface.

Please refer to image 13 in the repository.

**Investigation 7 — Extract Only Listening Port Numbers**

Command: grep LISTEN mac_netstat.log | awk '{print $4}'
It isolates listening services.

Please refer to image 14

**Investigation 8 — Identify SSH Service**

Command: grep "\.22 " mac_netstat.log
identify SSH exposure, 
useful for brute force and SOC monitoring.

Please refer to image 15

**Investigation 9 — Identify Splunk Services**

Command: grep "8000\|8089\|9997\|8191" mac_netstat.log
identify Splunk infrastructure traffic, 
SOC platform monitoring. 

Please refer to images 16-17 in the repository.

**Investigation 10 — Count Listening Services**

Command: grep LISTEN mac_netstat.log | wc -l
count total exposed/listening services.

Refer to image 18

**Investigation 11 — Analyze Packet Capture**

Command: tcpdump -r mac_network_capture.pcap | head -20
inspect packets, 
identify protocols, 
observe live network traffic. 

Please refer to image 19

**Investigation 12 — Extract Only IP Traffic from PCAP**

Command: tcpdump -r mac_network_capture.pcap | awk '{print $3, $5}' | head
isolate communication pairs, 
source → destination analysis.

Refer to image 20

**Investigation 13 — Find DNS Traffic**

Command: tcpdump -r mac_network_capture.pcap | grep "53"
investigate DNS queries, 
domain resolution activity, 
malware DNS hunting basics. 

Please refer to image 21

**Investigation 14 — Count Packets in Capture**

Command: tcpdump -r mac_network_capture.pcap | wc -l
determine packet volume.

Please refer to image 22 in the repository


















