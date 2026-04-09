# Homelab-Infrastructure-
This project documents my personal homelab used to simulate real-world IT environments.

The lab focus on:
- Networking
- Virtualization
- Troubleshooting
- System Design
- Fundamentals
- Learning

It is used to gain hands-on experience and reduce reliance on external services.

## Networking Evolution

### Current Network 
![Current](./images/Zco4mWxX.png)

### Future Network (Planned)
![Future](images/)

## Architecture

The current network setup is designed to work within apartment limitations, where traditional wired infrastructure is not fully available.

- The ISP modems provides WAN connectivity via WiFi 
- The Raspberry Pi 4 functions as a router running Ubuntu server, bridging WiFi (WAN) to Ethernet (LAN).
- The Proxmox server connects via Ethernet and hosts virtual machines.
- A VLAN-aware bridge is used to segment network traffic across different environments.

## VLAN Configuration 

| VLAN | Purpose |
| --- | --- |
| VLAN 10 | Main/Trusted Network |
| VLAN 20 | Lab/Testing |
| VLAN 50 | Services |

## Troubleshooting 

### Issue: VM had no internet access

- Checked interface configuration (`ip a`)
- Verified routing table (`ip route`)
- Tested connectivity

Resolved incorrect gateway configuration 


## Lessons Learned

- Proper routing and gateway configuration is critical 
- VLAN segmentation improves organization and security
- Structured > troubleshooting reduces time spent debugging


<p style='text-align:center;'>Documented and created by @jusstae</p>
