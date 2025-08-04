**Task Title:** Scan Your Local Network for Open Ports
**Platform:** Kali Linux (VMware)

**Objective**
The objective of this task is to gain practical knowledge of network reconnaissance by scanning the local network using Nmap to discover open ports and services. This reveals how internal devices expose services and helps assess potential vulnerabilities. Optionally, the use of Wireshark enables deeper packet-level visibility.

**Tools Used**
Tool	                Purpose
Nmap	        Network scanning and port discovery
Wireshark	    Packet capture and analysis (optional)
Kali Linux	    Ethical hacking and penetration testing OS

**Network Setup**
• Operating System: Kali Linux running in VMware
• Network Interface: eth0
• Local IP: 192.168.196.128
• Subnet: /24
• Identified via: ip a

**Steps Performed**
1. Installed Nmap:
#sudo apt update
#sudo apt install nmap

2. Determined Network Range:
IP identified: 192.168.196.128
CIDR range: 192.168.196.0/24

3. Performed TCP SYN Scan:
#sudo nmap -sS 192.168.196.128/24 -oN scan_results.txt

4. Scan Result Summary:
IP Address	        Open Ports	    Services	    MAC Address
192.168.196.1	    6646/tcp	    Unknown	        00:50:56:C0:00:80 (VMware)
192.168.196.2	    53/tcp	        DNS	            00:50:56:E5:63:6F (VMware)
192.168.196.254	    None	        Filtered	    00:50:56:EC:CF:C5 (VMware)
192.168.196.128	    80/tcp	        HTTP	        Host machine (self)

5. (Optional) Packet Capture with Wireshark:
• Launched Wireshark
• Captured traffic on interface eth0
• Applied display filter: tcp.flags.syn == 1 && tcp.flags.ack == 0
• Saved as: scan_capture.pcapng (Note: should be opened using wireshark)

**Repository Files**
File Name	                    Description
scan_results.txt	        Raw Nmap output (SYN scan)
scan_capture.pcapng	        Wireshark packet capture (optional)

README.md	                Documentation of process and key learnings
