# Homelab-Infrastructure
This project documents my personal homelab used to simulate real-world IT environments.

The lab focus on:
- Networking
- Virtualization
- Troubleshooting
- System Design
- Fundamentals
- Learning

It is used to gain hands-on experience and reduce reliance on external services.

---

## Networking Evolution

### Current Network 
![Current](./images/Zco4mWxX.png)

### Future Network (Planned)
![Future](images/)

---

## Architecture

The current network setup is designed to work within apartment limitations, where traditional wired infrastructure is not fully available.

- The ISP modems provides WAN connectivity via WiFi 
- The Raspberry Pi 4 functions as a router running Ubuntu server, bridging WiFi (WAN) to Ethernet (LAN).
- The Proxmox server connects via Ethernet and hosts virtual machines.
- A VLAN-aware bridge is used to segment network traffic across different environments.

--- 

## VLAN Configuration 

| VLAN | Purpose |
| --- | --- |
| VLAN 10 | Main/Trusted Network |
| VLAN 20 | Lab/Testing |
| VLAN 50 | Services |

---

## Troubleshooting 

### Issue: VM had no internet access
- Checked interface configuration (`ip a`)
- Verified routing table (`ip route`)
- Tested connectivity

Resolved incorrect gateway configuration.

---

## Lessons Learned

- Proper routing and gateway configuration is critical. 
- VLAN segmentation improves organization and security.
- Structured troubleshooting reduces time spent debugging.

--- 

## Future Plans

### Customer Router Build 
- Build a dedicated router using low-power hardware
- Run Ubuntu Server for full control over networking
- Configure DCHP, routing, and firewall troubleshooting

**Tools**:
- Netplan
- iptables
- isc-dhcp-server

--- 

### Network Expansion 
- Implement a manged switch for improve VLAN control
- Expand network segmentation and traffic management

---

### Raspberry Pi Enhancement 
- Deploy Pi-hole for DNS-based ad blocking 
- Use Python scripts for network monitoring and automation

---

### NAS (Network Attached Storage)
  - Build a low-power NAS using/new hardware
  - Host storage services on Proxmox using Ubuntu Server
  - Configure manual storage and backup solutions 

