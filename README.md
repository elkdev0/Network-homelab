# Amr Elkheir — Home Lab
CCNA | Network Engineering| 2026**

A hands-on enterprise-style home lab built to develop practical skills in switching, routing, VLAN design, DHCP services, and network troubleshooting using Aruba and Cisco hardware. This lab is designed to simulate real data center and enterprise network environments while building toward a career in data center operations and network engineering.

---

## Lab Overview

| Category | Details |
|----------|---------|
| Focus Areas | Routing & Switching, VLAN Segmentation, DHCP, Inter-VLAN Routing, Troubleshooting |
| Career Goal | Data Center Technician → Network Engineer |
| Current Progress | Homelab expansion, CCNA in progress |
| Platforms | Aruba 3810M, Cisco 2960X, Cisco ISR 4331, Windows Server, Packet Tracer, Draw.io |

---

## Network Topology

> _Add your Draw.io diagram export here_

```text
Internet / ISP
      |
   Cisco ISR 4331
      |
   Aruba 3810M  (Layer 3 Core / Distribution)
      |
   Cisco 2960X-24  (Access Layer)
      |
 End Devices / Future WiFi / Future Server / Future Firewall
```

---

## Hardware Inventory

### Network Infrastructure

| Device | Model | Role | Status |
|--------|-------|------|--------|
| Router | Cisco ISR 4331 | Upstream routing / future NAT / internet edge | ✅ Active |
| Core / Distribution Switch | Aruba 3810M 48-Port | Layer 3 core, inter-VLAN routing, DHCP, gateway services | ✅ Active |
| Access Switch | Cisco Catalyst 2960X-24 | Layer 2 access switch for Guest / IoT VLANs | ✅ Active |

### Servers / Virtualization

| Device | Model | Role | Status |
|--------|-------|------|--------|
| DHCP Server | Windows Server VM | Centralized DHCP services across VLANs | ✅ Active |
| Laptop Host | Windows laptop / VirtualBox | VM host for Windows Server lab services | ✅ Active |
| Future Server | TBD | DNS / Active Directory / additional services | 🔧 Planned |

### Future Additions

| Device | Role | Status |
|--------|------|--------|
| Firewall | pfSense / dedicated firewall appliance | 🔧 Planned |
| Wireless Access Point | Enterprise WiFi with SSID-to-VLAN mapping | 🔧 Planned |
| Rack Server or Dedicated Host | Expanded services / virtualization | 🔧 Planned |

---

## VLAN Design

| VLAN | Name | Subnet | Purpose |
|------|------|--------|---------|
| 10 | Corp Users | 10.15.10.0/26 | Corporate client devices |
| 20 | Guest | 10.15.20.0/27 | Guest network |
| 30 | Security | 10.15.30.0/28 | Security devices / isolated endpoints |
| 40 | Servers | 10.15.40.0/28 | DHCP server and future infrastructure services |
| 60 | IoT | 10.15.60.0/27 | IoT devices |
| 70 | DMZ | 10.15.70.0/29 | Public-facing / isolated test services |
| 100 | Management | 10.15.100.0/29 | Network device management |

---

## Core Services Implemented

### Inter-VLAN Routing
Configured inter-VLAN routing on the Aruba 3810M using SVIs, allowing segmented VLANs to communicate through the Layer 3 core switch while maintaining organized network boundaries.

### DHCP Services
Deployed centralized DHCP services using a Windows Server virtual machine in the Servers VLAN and configured DHCP relay (`ip helper-address`) on the Aruba 3810M so multiple VLANs can receive IP leases from a single server.

### Trunking
Configured 802.1Q trunking between the Aruba 3810M and Cisco 2960X to extend Guest and IoT VLANs to the access layer.

### Routed Uplink
Built a routed point-to-point uplink between the Aruba 3810M and Cisco ISR 4331 for upstream routing and future NAT / internet connectivity.

---

## Key Projects

### Segmented Enterprise Network Build
Built a layered network using a Cisco ISR router, an Aruba 3810M multilayer switch, and a Cisco 2960X access switch to simulate an enterprise network architecture with separated user, guest, server, management, IoT, security, and DMZ zones.

### Centralized DHCP with Relay
Configured a Windows Server VM to provide DHCP scopes for multiple VLANs and implemented DHCP relay on the Aruba switch to forward DHCP requests across routed VLAN boundaries.

### VLSM-Based IP Design
Designed an efficient VLSM-based addressing plan to reduce wasted IP space while keeping subnet structure aligned to VLAN roles for simpler troubleshooting and documentation.

### Troubleshooting VMware / Virtual Networking
Resolved virtual server connectivity issues caused by adapter conflicts and duplicate IP assignments while integrating a Windows Server VM into the physical lab environment.

---

## Routing / Switching Concepts Practiced

- VLAN creation and segmentation
- Inter-VLAN routing with SVIs
- Layer 2 trunking between switches
- Routed uplinks between network devices
- DHCP scope planning
- DHCP relay (`ip helper-address`)
- VLSM subnetting
- CLI-based troubleshooting
- Port-to-VLAN mapping
- Gateway and addressing design

---

## Virtual Machines

| VM | OS | IP | Purpose |
|----|----|----|---------|
| win-server-dhcp | Windows Server 2019 | 10.15.40.10 | DHCP services for multiple VLANs |

---

## Troubleshooting Log

Real issues documented during build-out and testing:

| # | Incident | Category |
|---|----------|----------|
| 01 | DHCP conflict caused by duplicate static IP on host and VM | DHCP / IP Addressing |
| 02 | VMware bridged adapter selecting the wrong network path | Virtualization / Networking |
| 03 | DHCP relay configuration conflict with local switch DHCP | DHCP / Layer 3 |
| 04 | Incorrect subnet range entered for VLAN 40 DHCP pool | DHCP / Subnetting |
| 05 | Windows Server installation issues with wrong VM install method | Virtualization |

---

## Device Configs

```text
configs/
├── aruba-3810m.txt          # VLANs, SVIs, helper addresses, routing
├── cisco-2960x.txt          # access ports, trunk uplink, VLAN extension
├── cisco-isr4331.txt        # routed uplink, future NAT / upstream routing
└── windows-dhcp-notes.md    # DHCP scopes and server role notes
```

---

## Documentation

| Document | Description |
|----------|-------------|
| Addressing Plan | IP ranges, VLAN gateways, subnet masks |
| Port Mapping | Aruba and Cisco switch port assignments |
| DHCP Scope Reference | VLAN-to-scope mapping for Windows Server |
| Troubleshooting Log | Real issues, root cause, and resolution |
| Topology Diagram | Draw.io lab diagram |

---

## What I Learned

- How to design and document a segmented enterprise-style network
- How DHCP behaves across routed VLANs
- Why duplicate IP addressing breaks connectivity
- The difference between local DHCP on a multilayer switch and centralized DHCP on a server
- How virtual networking settings affect communication with physical infrastructure
- How to troubleshoot methodically using CLI tools and OSI model logic

---

## What's Next

- [ ] Add ACLs to control inter-VLAN traffic
- [ ] Add enterprise WiFi with SSID-to-VLAN mapping
- [ ] Add firewall integration
- [ ] Add DNS and Active Directory services
- [ ] Add NAT / internet access through the ISR 4331
- [ ] Improve documentation and sanitized device configs
- [ ] Add rack layout and physical build photos

---

## Repository Structure

```text
homelab/
├── configs/
├── diagrams/
├── docs/
├── troubleshooting/
└── README.md
```

---

## Author

**Amr Elkheir**
IT Student | Homelab Builder | Future Network Engineer

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue)](https://linkedin.com)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black)](https://github.com)
