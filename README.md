# Enterprise-Ready Network Lab Project

This project simulates a realistic **small-to-medium enterprise network**, designed, built, and tested using **Cisco Packet Tracer**. It focuses on key IT support and networking tasks such as VLAN segmentation, inter-VLAN routing, DHCP, DNS,and network diagnostics.

---

## Lab Overview

| Component              | Technology Used           |
|------------------------|---------------------------|
| Simulation Tool        | Cisco Packet Tracer       |
| Services Deployed      | DHCP, DNS, SSH, Remote Desktop |
| Network Segmentation   | VLAN 10 (Admin), VLAN 20 (Sales), VLAN 30 (Guest) |
| Routing                | Router-on-a-Stick with DHCP Relay |
| Troubleshooting Tools  | `ping`, `ipconfig`, `traceroute`, `ip a`, Packet Tracer Simulation Mode |

---

## Features & Deliverables

- Designed a subnetted IP addressing scheme for 3 departments  
- Configured VLANs on Cisco switches  
- Implemented Inter-VLAN routing using router subinterfaces  
- Deployed a centralized DHCP and DNS server  
- Used `ip helper-address` for DHCP relay across VLANs  
- Verified connectivity and correct IP assignment  
- Simulated and resolved common issues (e.g., APIPA, VLAN misconfig)  
- Documented all steps and configuration outputs  
- Captured screenshots and command output logs

---

## Network Topology

[PCs VLAN 10/20/30] → [Access Switch] → [Router (with subinterfaces)]
↑
[DHCP/DNS Server - VLAN 10]

---

## Key Configuration Snippets

### VLAN Configuration (Switch)
```bash
vlan 10
name Admin
vlan 20
name Sales
vlan 30
name Guest



interface fa0/1
switchport mode access
switchport access vlan 10

interface g0/1.10
encapsulation dot1q 10
ip address 10.0.10.1 255.255.255.0

interface g0/1.20
encapsulation dot1q 20
ip address 10.0.20.1 255.255.255.0
ip helper-address 10.0.10.100

