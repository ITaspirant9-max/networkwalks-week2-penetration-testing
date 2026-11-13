# W2-PM5 – Zenmap Based Network Scanning

## Objective
Perform network scanning and host discovery using Zenmap and Nmap in a controlled VirtualBox lab environment.

## Environment
- Operating System: Kali Linux 2026.2
- Virtualization: Oracle VirtualBox
- Network Interface: eth0
- Network Type: VirtualBox NAT Network

## Network Configuration
- Kali IP Address: 10.0.0.2
- Subnet: /24
- Network Range: 10.0.0.0/24
- Broadcast Address: 10.0.0.255

## Tasks Performed

### Task 1 – Zenmap Installation
Verified Zenmap installation.

Command:
command -v zenmap

Result:
Zenmap found at /usr/bin/zenmap

### Task 2 – Local IP and Subnet
Identified the local IP address and subnet.

Command:
ip -4 addr show eth0

Result:
IP: 10.0.0.2/24
Network: 10.0.0.0/24

### Task 3 – Live Host Discovery
Used Zenmap with the Ping scan profile to discover live hosts on the lab subnet.

Target:
10.0.0.0/24

Equivalent Nmap command:
nmap -sn 10.0.0.0/24

Result:
3 live hosts discovered.

### Task 4 – Live Host Count
Counted the discovered hosts.

Result:
3 live hosts.

### Task 5 – IP Addresses
Recorded the discovered IP addresses:

- 10.0.0.1
- 10.0.0.3
- 10.0.0.2

### Task 6 – MAC Addresses
Recorded the available MAC addresses:

- 10.0.0.1 – 52:54:00:12:35:00
- 10.0.0.3 – 52:54:00:12:35:00
- 10.0.0.2 – 08:00:27:5a:87:bc

Note: Nmap reported the same MAC address for 10.0.0.1 and 10.0.0.3.

### Task 7 – Network Topology
Created the network topology using Zenmap and exported it as a PDF.

File:
W2-PM5-Network-Topology.pdf

## Project Files

- task1-zenmap.txt
- task2-ip-subnet.txt
- task3-live-hosts.txt
- task4-host-count.txt
- task5-ip-addresses.txt
- task6-mac-addresses.txt
- task7-topology-export.txt
- W2-PM5-Network-Topology.pdf
- Screenshots/

## Conclusion
Successfully performed host discovery, identified three live hosts, recorded IP and MAC addresses, and exported the network topology.

All scanning was conducted within the assigned VirtualBox lab network.
