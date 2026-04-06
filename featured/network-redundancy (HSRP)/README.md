# First Hop Redundancy (HSRP) & STP Alignment Lab

This lab demonstrates gateway redundancy using HSRP and its integration with STP to achieve optimal traffic flow and high availability in a multi-switch topology.

---

## 📚 Lab Breakdown

### 🔹 Part 1 – HSRP Configuration & Failover

- Verified initial connectivity to external network (8.8.8.8)  

- Configured **HSRPv2 on R1 and R2**:
  - Set virtual IP (VIP) as default gateway  
  - Increased R1 priority (active)  
  - Decreased R2 priority (standby)  
  - Enabled preemption  

- Verified:
  - PCs use VIP as default gateway  
  - ARP table maps VIP to HSRP virtual MAC  

- Tested failover:
  - Shut down R1 → R2 becomes active  
  - Restored R1 → preemption returns it to active  

---

### 🔹 Part 2 – HSRP & STP Optimization

- Configured HSRP on distribution switches (DSW1 / DSW2)

- Aligned **HSRP with STP root roles** per VLAN:

**VLAN 10**
- DSW1 → HSRP active & STP root  
- DSW2 → HSRP standby & STP secondary  

**VLAN 20**
- DSW2 → HSRP active & STP root  
- DSW1 → HSRP standby & STP secondary  

- Verified:
  - Traffic follows optimal Layer 2 path  
  - No unnecessary cross-switch forwarding  

---

## 🧠 Key Concepts Demonstrated

- HSRP (active/standby roles)  
- Virtual IP and virtual MAC behavior  
- Preemption and failover handling  
- Default gateway redundancy  
- STP root bridge alignment with HSRP  
- Per-VLAN load balancing  

---

## ✅ Validation

- `show standby`  
- `show standby brief`  
- `show spanning-tree`  
- `arp -a` (on PCs)  
- Ping tests to external network  

---

## 🔍 Troubleshooting Performed

- Verified VIP mapping to HSRP virtual MAC  
- Confirmed failover during active router shutdown  
- Ensured preemption restores primary router  
- Validated STP root alignment with HSRP roles  

---

## 📌 Key Takeaway

- **HSRP** provides gateway redundancy and failover  
- **Preemption** ensures the preferred router regains control  
- **STP alignment with HSRP** prevents suboptimal traffic paths  
