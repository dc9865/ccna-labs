# VLAN & Inter-VLAN Routing Lab

This lab demonstrates VLAN segmentation, trunking, router-on-a-stick (ROAS), and multilayer switching in a progressive enterprise topology.

---

## 📚 Lab Breakdown

### 🔹 Part 1 – VLAN Configuration

- Created VLANs:
  - Engineering  
  - HR  
  - Sales  

- Assigned switch ports to correct VLANs  
- Configured PC IP addressing with **last usable IP as default gateway**  
- Configured separate physical router interfaces as gateways (one per VLAN)  
- Established one physical connection per VLAN between SW1 and R1  
- Verified connectivity and broadcast isolation  

---

### 🔹 Part 2 – VLAN Trunking & Router-on-a-Stick

- Configured trunk link between switches:
  - Allowed VLANs only  
  - Set unused native VLAN  

- Ensured VLAN consistency across switches  

- Implemented **ROAS**:
  - Configured router subinterfaces  
  - Assigned gateway IPs per VLAN  

- Verified inter-VLAN connectivity  

---

### 🔹 Part 3 – Multilayer Switching

- Replaced ROAS with **Layer 3 switching**  

- Configured:
  - SVIs for each VLAN (gateway IPs)  
  - Configured point-to-point Layer 3 link between switch and router  
  - Default route on L3 switch  

- Verified:
  - Inter-VLAN routing via SVIs  
  - External connectivity  

---

## 🧠 Key Concepts Demonstrated

- VLAN segmentation and port assignment  
- Access vs trunk configuration  
- Native VLAN and allowed VLAN control  
- Router-on-a-stick (ROAS)  
- Multilayer switching with SVIs  
- Default gateway design  
- Layer 2 → Layer 3 transition  

---

## ⚙️ Technologies Used

- VLANs (802.1Q)  
- Trunking  
- Router-on-a-stick  
- Multilayer switching  
- Static routing  
- Cisco IOS CLI  

---

## ✅ Validation

- `show vlan brief`  
- `show interfaces trunk`  
- `show ip route`  
- Inter-VLAN ping tests  
- Verified external connectivity (ping 1.1.1.1)

---

## 🔍 Troubleshooting Performed

- Verified VLAN membership and trunk consistency  
- Identified missing VLANs across switches  
- Validated ROAS subinterface configuration  
- Confirmed routing using `show ip route`  

---

## 📌 Key Takeaway

- **VLANs** segment broadcast domains  
- **ROAS** enables inter-VLAN routing via a router  
- **Multilayer switching** provides scalable, high-performance routing  

This lab demonstrates the evolution from **Layer 2 segmentation to Layer 3 switching in enterprise networks**.
