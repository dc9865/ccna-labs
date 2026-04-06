# Access Control Lists (ACLs) & Traffic Filtering Lab

This lab demonstrates the use of standard and extended ACLs to enforce network policies, along with OSPF to provide full connectivity between multiple subnets.

---

## 📚 Lab Breakdown

### 🔹 Part 1 – Extended ACLs (Traffic Filtering)

- Configured **extended ACLs** to enforce specific traffic policies:

  - Block traffic from 172.16.2.0/24 → PC1  
  - Deny DNS access from 172.16.1.0/24 → SRV1  
  - Deny HTTP/HTTPS access from 172.16.2.0/24 → SRV2  

- Applied ACLs on appropriate interfaces (close to source)  

- Verified:
  - Allowed and denied traffic behaves as expected  

---

### 🔹 Part 2 – OSPF & Standard ACLs

- Configured **OSPF between R1 and R2**:
  - Enabled full connectivity across all networks  

- Configured **standard and named ACLs** on R2:

  - Only PC1 and PC3 can access 192.168.1.0/24  
  - Block 172.16.2.0/24 → 192.168.2.0/24  
  - Block 172.16.1.0/24 → 172.16.2.0/24  
  - Block 172.16.2.0/24 → 172.16.1.0/24  

- Verified:
  - Routing works correctly via OSPF  
  - ACL policies enforce traffic restrictions  

---

## 🧠 Key Concepts Demonstrated

- Standard vs Extended ACLs  
- Traffic filtering based on:
  - Source IP  
  - Destination IP  
  - Protocol (DNS, HTTP, HTTPS)  

- ACL placement (near source vs destination)  
- Named ACLs vs numbered ACLs  
- Interaction between routing (OSPF) and security (ACLs)  

---

## ⚙️ Technologies Used

- Extended ACLs  
- Standard ACLs  
- Named ACLs  
- OSPF  
- Cisco IOS CLI  

---

## ✅ Validation

- `show access-lists`  
- `show ip interface`  
- `show ip route`  
- End-to-end ping and service testing (DNS, HTTP/HTTPS)  

---

## 🔍 Troubleshooting Performed

- Verified ACL placement to avoid unintended blocking  
- Identified implicit deny behavior  
- Ensured OSPF routing was functioning before applying ACLs  
- Tested application-layer traffic (DNS, HTTP) to confirm filtering  

---

## 📌 Key Takeaway

- **Extended ACLs** provide granular traffic control (protocol + destination)  
- **Standard ACLs** filter based on source IP only  
- **ACL placement** is critical to avoid unintended traffic drops  
- **Routing + ACLs** must be configured together to ensure both connectivity and security  
- Extended ACLs should be placed as close to the source as possible to minimize unnecessary traffic, while standard ACLs are typically placed closer to the destination.
