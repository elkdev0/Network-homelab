# 🖧 Amr Elkheir — Home Lab

> **Aspiring Network Engineer | CCNA in Progress | April 2026**  
> A hands-on enterprise-style home lab built to develop real-world networking, data center, and troubleshooting skills.

---

## 📋 Lab Overview

| Category | Details |
|----------|---------|
| **Focus Areas** | Routing & Switching, VLANs, Network Troubleshooting, Virtualization |
| **Current Role** | Access Control Officer — Data Center Environment |
| **Goal** | Transition into Data Center Technician → Network Engineer |
| **Tools Used** | Cisco hardware, Aruba switch, GNS3, VMware/VirtualBox |

---

## 🗺️ Network Topology

This lab simulates a small enterprise/data center environment, including:

- Layer 3 switching
- VLAN segmentation
- Inter-VLAN routing
- Router-based services (DHCP, NAT)
- Virtual machines for services

---

## 🖥️ Hardware Inventory

### Network Devices

| Device | Model | Role |
|--------|-------|------|
| Router | Cisco ISR 4331 | Routing, NAT, DHCP |
| Layer 3 Switch | Aruba 3810M | Inter-VLAN routing |
| Access Switch | Cisco Catalyst 2960X | Access layer switching |
| Additional Switch | Cisco WS-C3850 | High-speed switching (10G capable) |

### Virtualization & Systems

| System | Role |
|--------|------|
| Windows Server 2019 VM | DHCP, DNS (planned/active) |
| Windows 10 VM | Management workstation |
| GNS3 | Network simulation and testing |
| VirtualBox / VMware | Virtualization platform |

---

## 🔀 VLAN Design

| VLAN | Purpose | Example Use |
|------|---------|-------------|
| 10 | Users | PCs / client devices |
| 20 | Servers | Windows Server VM |
| 30 | Management | Device access (SSH, configs) |

---

## ⚙️ Key Networking Concepts Implemented

### 🔹 Inter-VLAN Routing
- Configured on Aruba 3810M (Layer 3 switch)
- Allows communication between VLANs
- Used SVIs (Switched Virtual Interfaces)

### 🔹 Trunking (Cisco ↔ Aruba)
- Configured trunk links between switches
- Aruba uses "tagged" VLAN terminology instead of Cisco trunk commands
- Ensured VLAN consistency across devices

### 🔹 DHCP Configuration
- Implemented DHCP on the Router (ISR 4331) **or** Windows Server 2019 VM
- Used scopes per VLAN
- Tested automatic IP assignment across networks

### 🔹 NAT (Network Address Translation)
- Configured on router
- Allows internal devices to access external networks
- Simulates real-world internet access behavior

### 🔹 OSPF (Dynamic Routing)
- Configured between routers in lab
- Tested route propagation
- Practiced troubleshooting adjacency issues

---

## 🚀 Key Projects

### 🌐 Full Network Deployment
- Built a complete network from scratch using physical + virtual devices
- Designed VLAN structure and IP addressing scheme
- Connected multiple switches and a router into a cohesive topology

### 🛠️ Troubleshooting Real Issues

Worked through real-world problems including:

- VLAN mismatch between switches
- DHCP not assigning IPs
- VM network adapter bridging issues
- Routing misconfigurations

**One major fix:**
> Disabled VMware virtual adapters (VMnet1 & VMnet8) to allow proper bridging to the physical network — resolved an incorrect subnet assignment issue.

### 💻 Virtualization Setup
- Installed Windows Server 2019 in a VM
- Configured networking manually
- Tested bridging vs. NAT adapter modes
- Practiced server-based networking services

---

## 🧠 Skills Gained

- ✅ VLAN configuration & troubleshooting
- ✅ Inter-VLAN routing (Layer 3 switching)
- ✅ Cisco ↔ Aruba interoperability
- ✅ DHCP & IP addressing
- ✅ NAT and routing fundamentals
- ✅ VM networking (bridging, adapters)
- ✅ Real-world troubleshooting mindset

---

## 🔍 Troubleshooting Approach

I follow a structured approach based on the **OSI model**:

| Layer | Focus |
|-------|-------|
| **1 — Physical** | Cables, ports, link lights |
| **2 — Data Link** | VLANs, trunking |
| **3 — Network** | IP addressing, routing |
| **4+ — Transport/App** | Services like DHCP |

This method helps quickly isolate and resolve issues in complex environments.

---

## 🗺️ What's Next

- [ ] Add firewall (ASA or similar)
- [ ] Implement Active Directory on Windows Server
- [ ] Add WiFi access point
- [ ] Expand into automation (Python / Ansible)
- [ ] Practice BGP and advanced routing

---

## 💡 Why This Lab Matters

This lab is designed to go beyond theory — every configuration and issue solved builds real experience directly applicable to:

- 🏢 Data Center Technician roles
- 🌐 Network Engineering roles
- ☁️ AWS / cloud infrastructure environments

---

*Built and maintained by **Amr Elkheir** — learning by doing, one packet at a time.*
