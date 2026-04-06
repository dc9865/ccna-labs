# EtherChannel & STP Advanced Switching Lab

This lab demonstrates advanced Layer 2 switching concepts including EtherChannel (LACP/PAgP/static), STP, RSTP, and Layer 3 EtherChannel routing in a redundant multi-switch topology.

---

## 📚 Lab Breakdown

### 🔹 Part 1 – EtherChannel Configuration (L2 & L3)

- Configured **L2 EtherChannel (LACP & PAgP)** between access and distribution switches  
- Configured **L3 EtherChannel (static)** between distribution switches  
- Enabled trunking on port-channels  
- Assigned IP addresses to routed port-channel interfaces  
- Verified connectivity between VLAN networks and server  

---

### 🔹 Part 2 – STP Analysis & Optimization

- Identified **root bridge** (priority + MAC)  
- Verified port roles:
  - Root, Designated, Blocking  

- Analyzed topology behavior:
  - Impact of **shared (hub) vs point-to-point links**  
  - Path selection based on cost  

- Optimized STP per VLAN:
  - SW1 → root for VLAN1  
  - SW2 → root for VLAN2  

- Tuned path selection:
  - **Interface cost**
  - **Port priority**

- Implemented **load balancing** across redundant links  

- Enabled **PortFast + BPDU Guard** on access ports  

---

### 🔹 Part 3 – RSTP Link Types & Behavior

- Verified RSTP roles:
  - Root, Designated, Alternate  

- Identified link types:
  - Point-to-point  
  - Shared  

- Configured link types manually  
- Observed faster convergence vs STP  

---

## 🧠 Key Concepts Demonstrated

- EtherChannel (LACP, PAgP, static)
- L2 vs L3 EtherChannel
- STP root election and port roles
- Per-VLAN STP load balancing
- Cost vs port priority tuning
- RSTP link types and fast convergence
- PortFast and BPDU Guard

---

## ✅ Validation

- `show etherchannel summary`
- `show spanning-tree`
- `show interfaces trunk`
- `show ip route`
- End-to-end ping tests  

---

## 🔍 Troubleshooting Performed

- Verified EtherChannel consistency (mode mismatch issues)
- Identified STP root bridge using `show spanning-tree`
- Analyzed blocked ports and path selection
- Adjusted cost/priority to influence traffic flow

---

## 📌 Key Takeaway

- **EtherChannel** increases bandwidth and redundancy  
- **STP** prevents loops and controls traffic paths  
- **Per-VLAN root tuning** enables load balancing  
- **RSTP** improves convergence speed  

These concepts reflect real-world enterprise switching design.
