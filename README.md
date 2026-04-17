# Homelab-Infrastructure
This project documents my personal homelab used to simulate real-world IT environments.

The lab focus on:
- Networking
- Virtualization
- Troubleshooting
- System Design
- Fundamentals
- Learning

It is used to gain hands-on experience and reduce reliance on external services. This repo will be regular updated.

---

## Networking Evolution

### Current Network 
![Current](./images/Zco4mWxX.png)

### Future Network (Planned)
![Current](./images/Future-BasicNetwork-Diagram.png)

---

## Architecture

#### Current Architecture
The current network setup is designed to work within apartment limitations, where traditional wired infrastructure is not fully available.

- The ISP modems provides WAN connectivity via WiFi 
- The Raspberry Pi 4 functions as a router running Ubuntu server, bridging WiFi (WAN) to Ethernet (LAN).
- The Proxmox server connects via Ethernet and hosts virtual machines.
- A VLAN-aware bridge is used to segment network traffic across different environments.

 #### Future Architecture
The future network setup is designed for an 8U 10" rack, allowing all internal devices to be fully wired within the rack itself. While not all switch ports will be heavily used, having additional ports available provides flexibility for management access and wired connections, such as for gaming.

You can refer to my Homelab-Networking documentation for a detailed overview of how everything operates, including VLAN configurations and firewall setup.

##### Legend:

- Solid lines represent non-Ethernet connections
- Arrows (→) indicate wired Ethernet connections
- Dashed lines (--) represent wireless connections

##### Color Coding:

- Green: Home network and PoE devices (VLAN 10)
- Blue: Servers and services (VLAN 20)
- Yellow: Trusted management devices (VLAN 99)
- Orange: NAS (VLAN 30)
- White: Direct connections (non-VLAN)
- Red: Reserved for future expansion, such as additional devices or another switch

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
- Access point, will allow me to have two ssids
  - SSID-1: Personal trusted devices
  - SSID-2: Non trusted devices(TV will need to reach NAS)

---

### Raspberry Pi Isolations
- Setup a second router connected to the main router
- Main router will treat the pi 4 as any other devices on the network (no direct connect to switch)
- all traffic from the mini pc will only know about the Pi 4 
- Mini pc
  - Proxmox with VLAN-aware
  - Machine will be used to:
    - Spin up any linux distros
    - Experiment with networking setups
    - Run isolated malware virtual machines 

---

### NAS (Network Attached Storage)
- Build a low-power NAS using/new hardware
- Host storage services on Proxmox using Ubuntu Server
- Configure manual storage and backup solutions 

---

### Hardware Upgrades
#### Current Network
The current setup consists of a Raspberry Pi 4 and a desktop PC. This configuration is sufficient for hosting multiple virtual machines and general experimentation. However, the systems are not operated continuously (24/7), and physical space constraints limit expansion options.

#### Limitations
- Lack of continuous operation
- Space constraints prevent the use of a standard 19" rack
- Current layout relies partially on non-optimal placement and connectivity
- Planned Upgrade

To improve organization and network reliability, the infrastructure will be migrated to a 10" 8U rack.

#### Objectives
- Fit within limited living space
- Centralize equipment near the ISP modem
- Enable full Ethernet connectivity for all devices in the rack
- Reduce reliance on Wi-Fi
- Improve overall network stability and performance
- Deployment Notes
- The rack will be installed in the living room adjacent to the ISP modem
- All systems within the rack will be connected via Ethernet
- The compact 10" form factor provides a balance between scalability and space efficiency

#### Rack Design
- Access point

- 1u patch panel

- 1u Custom Router
  - thinkcentre M720q or M920q

- 1u PoE 8 port managed switch

- 2x 1u Proxmox
  - thinkcentre M720q/M920q

- 1u thinkcentre M920q (NAS Controller)
  - Pcie Riser, Sata expansion card
  - 12v Dc adapter from psu

- 1u icydock 6 bay ssd 2.5 sata

- 1u Mini pc (Dell or thinkcentre) & pi 4 router
