# VLAN & Inter-VLAN Routing Lab

This lab series demonstrates VLAN segmentation, trunking, router-on-a-stick (ROAS), and multilayer switching using a progressive topology.

The configurations are based on a 3-VLAN environment (Engineering, HR, Sales), with each VLAN mapped to its own subnet and gateway.

---

## 📚 Lab Breakdown

### 🔹 Part 1 – VLAN Configuration (Day 16)

- Configured IP addresses on PCs with the **last usable IP as the default gateway**
- Created VLANs:
  - Engineering
  - HR
  - Sales
- Assigned switch interfaces to the correct VLANs
- Configured multiple physical connections between R1 and SW1 (one per VLAN)
- Assigned gateway IP addresses on R1 interfaces for each VLAN
- Verified connectivity and broadcast behavior using Packet Tracer simulation mode

---

### 🔹 Part 2 – VLAN Trunking & Router-on-a-Stick (Day 17)

- Configured access ports for end devices in correct VLANs
- Configured trunk link between SW1 and SW2:
  - Allowed only required VLANs
  - Set an unused native VLAN
- Ensured VLAN consistency across switches
- Implemented **router-on-a-stick (ROAS)**:
  - Configured subinterfaces on R1
  - Assigned last usable IP addresses as gateways
- Verified full connectivity between all VLANs

---

### 🔹 Part 3 – Multilayer Switching (Day 18)

- Replaced ROAS with **Layer 3 switching**
- Configured a point-to-point Layer 3 link between SW2 and R1
- Created SVIs (Switch Virtual Interfaces) on SW2 for each VLAN
- Assigned gateway IPs to SVIs (last usable IPs)
- Configured a default route on SW2 pointing to R1
- Verified:
  - Inter-VLAN routing via SVIs
  - External connectivity (ping to 1.1.1.1)

---

## 🧠 Key Concepts Demonstrated

- VLAN creation and port assignment
- Access vs trunk port configuration
- Native VLAN and allowed VLAN control
- Router-on-a-stick (ROAS)
- Multilayer switching with SVIs
- Default gateway design using last usable IP
- Broadcast behavior within VLANs
- Transition from Layer 2 to Layer 3 switching

---

## 🏗️ Topology Overview

- Multiple VLANs (Engineering, HR, Sales)
- SW1 and SW2 connected via trunk link
- Initial routing via R1 (ROAS)
- Later transitioned to Layer 3 switching on SW2
- End devices assigned to separate VLANs and subnets

---

## ⚙️ Technologies Used

- VLANs (802.1Q)
- Trunking
- Router-on-a-stick
- Multilayer switching (SVIs)
- Static routing (default route)
- Cisco IOS CLI

---

## ✅ Validation Steps

- Verified VLAN assignment:
  - `show vlan brief`

- Verified trunk configuration:
  - `show interfaces trunk`

- Verified routing:
  - Ping between VLANs
  - `show ip route`

- Verified external connectivity:
  - Ping to `1.1.1.1`

- Observed broadcast behavior using simulation mode

---

## 📌 Key Takeaway

This lab demonstrates the evolution of inter-VLAN routing:

- **Physical router interfaces → Router-on-a-stick → Multilayer switching**

It highlights how enterprise networks move from basic Layer 2 segmentation to more scalable Layer 3 switching designs.
