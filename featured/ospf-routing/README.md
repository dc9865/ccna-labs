# OSPF Routing & Troubleshooting Lab

This lab demonstrates OSPF configuration, default route advertisement, metric adjustment, and real-world troubleshooting scenarios within a multi-router topology.

---

## 📚 Lab Breakdown

### 🔹 Part 1 – OSPF Configuration & Default Route

- Configured hostnames and IP addressing on all routers  
- Created loopback interfaces (Router IDs)  

- Enabled OSPF on all routers:
  - Advertised all relevant networks  
  - Configured passive interfaces where appropriate  

- Configured R1 as an **ASBR**:
  - Advertised a default route into OSPF  

- Verified:
  - OSPF neighbor adjacencies  
  - Routing table entries on R2, R3, and R4  

---

### 🔹 Part 2 – OSPF Optimization & Behavior

- Enabled OSPF directly on interfaces  
- Configured passive interfaces for non-transit networks  

- Tuned OSPF metrics:
  - Adjusted **reference bandwidth** for accurate cost calculation  

- Verified:
  - Default route propagation across the OSPF domain  
  - Routing table consistency  

- Analyzed OSPF Hello packets using simulation mode  

---

### 🔹 Part 3 – OSPF Troubleshooting

- Configured new **serial link between R1 and R2**  
  - Set clock rate and enabled OSPF  

- Identified and resolved routing issues:
  - Missing route to **10.0.2.0/24**  
  - OSPF neighbor adjacency failures  
  - External connectivity issues (8.8.8.8 unreachable)  

- Diagnosed problems using:
  - Neighbor states  
  - Interface configurations  
  - OSPF parameters  

- Examined LSDB:
  - Identified different LSA types present  

---

## 🧠 Key Concepts Demonstrated

- OSPF neighbor formation and adjacency  
- Router ID and loopback usage  
- Default route advertisement (ASBR)  
- OSPF cost and reference bandwidth  
- Passive interface configuration  
- LSA types and LSDB analysis  
- OSPF troubleshooting (adjacency, routing, reachability)  

---

## ✅ Validation

- `show ip ospf neighbor`  
- `show ip route`  
- `show ip ospf database`  
- `show ip protocols`  
- End-to-end ping tests  

---

## 🔍 Troubleshooting Performed

- Identified missing OSPF routes due to incorrect network statements  
- Resolved adjacency issues (interface mismatch / configuration errors)  
- Verified default route propagation from ASBR  
- Diagnosed reachability issues using routing tables and neighbor states  

---

## 📌 Key Takeaway

- **OSPF** dynamically builds routing tables using link-state information  
- **ASBRs** inject external routes into the OSPF domain  
- **Cost adjusting** influences path selection  
- **Troubleshooting OSPF** requires analyzing adjacencies, LSDB, and routing tables
