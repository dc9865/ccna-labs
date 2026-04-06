# EtherChannel & STP Advanced Switching Lab

This lab series demonstrates advanced Layer 2 switching concepts including EtherChannel (LACP/PAgP/static), Spanning Tree Protocol (STP), Rapid Spanning Tree Protocol (RSTP), root bridge election, port roles, and Layer 3 EtherChannel routing.

The configurations are based on multi-switch enterprise topologies with redundancy, loop prevention, and load balancing across links.

---

## 📚 Lab Breakdown

### 🔹 Part 1 – EtherChannel Configuration (L2 & L3)

- Configured **Layer 2 EtherChannel using LACP** between ASW1 and DSW1  
  - Set interfaces to trunk mode  
  - Verified aggregation using `show etherchannel summary`

- Configured **Layer 2 EtherChannel using PAgP** between ASW2 and DSW2  
  - Ensured proper negotiation mode (desirable/auto)  
  - Configured trunking on the port-channel interface  

- Configured **Layer 3 EtherChannel (static)** between DSW1 and DSW2  
  - Converted interfaces to routed ports  
  - Assigned IP addresses to Port-Channel interface  

- Configured **routing between VLAN networks (172.16.x.x) and point-to-point link (10.0.0.0/30)**  
  - Enabled communication between PCs and server  

---

### 🔹 Part 2 – STP Analysis & Optimization

- Identified the **root bridge** using:
  - Bridge priority  
  - MAC address comparison  

- Verified STP port roles using CLI:
  - Root port  
  - Designated port  
  - Non-designated (blocking) port  

- Analyzed STP behavior in complex topologies:
  - Observed impact of **shared segments (hubs)** vs point-to-point links  
  - Identified how STP selects paths based on cost  

- Optimized STP per VLAN:
  - SW1 → Primary root for VLAN1, secondary for VLAN2  
  - SW2 → Primary root for VLAN2, secondary for VLAN1  

- Tuned path selection using:
  - **Interface cost adjustments** (influences best path)  
  - **Port priority adjustments** (tie-breaker for root port selection)  

- Implemented **load balancing across redundant links**:
  - Different VLANs use different root switches  
  - Traffic distributed across multiple paths  

- Configured **PortFast and BPDU Guard** on access ports:
  - Enabled fast convergence for end devices  
  - Prevented accidental Layer 2 loops  

---

### 🔹 Part 3 – RSTP Link Types & Behavior

- Analyzed **RSTP port roles and states**:
  - Root (R)  
  - Designated (D)  
  - Alternate (blocking)  

- Identified **RSTP link types**:
  - Point-to-point (full duplex switch links)  
  - Shared (hub-connected segments)  

- Manually configured link types:
  - `spanning-tree link-type point-to-point`  
  - `spanning-tree link-type shared`  

- Determined correct link type for:
  - SW1 F0/24 → **shared (connected to hub)**  

- Understood how RSTP improves:
  - Faster convergence compared to STP  
  - Immediate transitions on edge and point-to-point links  

---

## 🧠 Key Concepts Demonstrated

- EtherChannel (LACP, PAgP, static)
- Layer 2 vs Layer 3 EtherChannel
- STP root bridge election (priority + MAC)
- Port roles (root, designated, blocking)
- Per-VLAN STP optimization and load balancing
- STP cost vs port priority tuning
- RSTP port roles and link types
- PortFast and BPDU Guard for edge security

---

## 🏗️ Topology Overview

- Multi-switch enterprise topology with redundancy  
- Dual links aggregated using EtherChannel  
- Layer 3 inter-switch connectivity via routed port-channel  
- STP-enabled loop prevention across all switches  
- VLAN-based segmentation with per-VLAN root optimization  
- Hosts and server placed across different access layers  

---

## ⚙️ Technologies Used

- EtherChannel (LACP, PAgP, static)
- Spanning Tree Protocol (STP)
- Rapid Spanning Tree Protocol (RSTP)
- VLANs & trunking (802.1Q)
- Layer 3 switching
- Static routing
- PortFast & BPDU Guard
- Cisco IOS CLI

---

## ✅ Validation Steps

- Verified EtherChannel:
  - `show etherchannel summary`
  - `show interfaces port-channel X`

- Verified STP:
  - `show spanning-tree`
  - `show spanning-tree vlan X`
  - 'show spanning-tree interface X detail'

- Verified trunking:
  - `show interfaces trunk`

- Verified routing:
  - `show ip route`
  - Ping between PCs and server  

- Verified port roles and states:
  - Root / Designated / Blocking  

---

## 📌 Key Takeaway

This lab demonstrates how enterprise networks achieve **redundancy, stability, and efficient traffic distribution**:

- **EtherChannel** → Aggregates links for higher bandwidth and redundancy  
- **STP** → Prevents loops and ensures controlled failover paths  
- **Per-VLAN root tuning** → Enables traffic load balancing across switches  
- **RSTP** → Improves convergence speed in modern networks  
