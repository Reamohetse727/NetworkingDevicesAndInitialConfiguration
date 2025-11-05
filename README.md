# Multi-LAN Packet Tracer Lab
![The network environment](images/lookup.png)

## Project Overview

This project simulates a small-scale network environment using Cisco Packet Tracer. It consists of four separate Local Area Networks (LANs), each with two PCs and a switch, interconnected through central routers. The objective is to practice network design, IP addressing, and device configuration in a controlled lab setting.

---

## Network Topology

The network consists of the following components:

- **LAN 1:** 2 PCs connected to Switch1
- **LAN 2:** 2 PCs connected to Switch2
- **LAN 3:** 2 PCs connected to Switch3
- **LAN 4:** 2 PCs connected to Switch4
- **Routers:** 2 Cisco routers to interconnect LANs

**IP Addressing Scheme:**

| LAN  | Subnet          | Router Gateway  |
|------|----------------|----------------|
| LAN1 | 192.168.10.0/24 | 192.168.10.1   |
| LAN2 | 192.168.20.0/24 | 192.168.20.1   |
| LAN3 | 192.168.30.0/24 | 192.168.30.1   |
| LAN4 | 192.168.40.0/24 | 192.168.40.1   |

**Router-to-Router Link:**  
- Subnet: 10.0.0.0/30  
- Router1: 10.0.0.1  
- Router2: 10.0.0.2  

---

## Components Used

- Cisco Packet Tracer  
- Cisco 1941 Routers  
- Cisco Switches (PT model)  
- PCs (PT Desktop)

---

## Installation / Setup Instructions

1. **Download Packet Tracer**  
   - Ensure Cisco Packet Tracer is installed (version 8.x recommended).  
   - Download from the official Cisco Networking Academy website: [https://www.netacad.com/](https://www.netacad.com/)

2. **Open the Project File**  
   - Open the `.pkt` file included in this repository.  
   - The file contains all switches, PCs, and routers pre-placed according to the topology.

3. **Configure Routers**  
   - Open the CLI of each router and configure interfaces with the IP addresses specified in the IP addressing table.  
   - Use the `no shutdown` command to activate each interface.  
   - Example configuration for Router1 (LAN1 & LAN2):  

   ```bash
   enable
   configure terminal
   interface GigabitEthernet0/0
    ip address 192.168.10.1 255.255.255.0
    no shutdown
   exit
   interface GigabitEthernet0/1
    ip address 192.168.20.1 255.255.255.0
    no shutdown
   exit
   interface GigabitEthernet0/2
    ip address 10.0.0.1 255.255.255.252
    no shutdown
   exit
   ip routing
   end
   copy running-config startup-config

   - Repeat a similar configuration for Router2 (LAN3 & LAN4).
4. **Configure Switches**
   - Assign hostnames and configure passwords for console and enable mode.
   - Example Switch1 configuration:
   ```bash
   enable
   configure terminal
   hostname Switch1
   enable secret cisco123
   line console 0
       password console123
       login
   exit
   service password-encryption
   banner motd # Authorized Access Only #
   end
   copy running-config startup-config

   - Repeat for Switch2, Switch3, and Switch4 with unique hostnames.
5. **Connect Devices**
   - Connect PCs to their respective switches using copper straight-through cables.
   - Connect each LAN to the router using a copper straight-through cable.
   - Connect Router1 and Router2 using a copper crossover cable on the designated GigabitEthernet ports.
6. **Assign IP Addresses to PCs**
   - Each PC should have a static IP according to the IP addressing table, with the router interface as the default gateway.

**Notes**
- Ensure all router interfaces are activated with no shutdown.
- The configuration ensures proper segmentation of all LANs while allowing inter-router communication.
- All passwords, banners, and hostnames are configured for clarity and security.

**Author**
   **Reamohetse Ntetshe**

**License**
This project is provided for educational purposes and is free to use and modify.
```yaml
   ---
   If you want, I can **also add “Code Blocks” for all router and switch commands in GitHub-style formatting** so that when you push it to GitHub, it looks clean with monospaced       formatting and syntax highlighting.  
   Do you want me to do that next?

