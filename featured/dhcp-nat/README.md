# DHCP Relay & NAT (Static, Dynamic, PAT) Lab

This lab demonstrates DHCP server/relay operation and NAT (static, dynamic, and PAT) to enable internal hosts to communicate with external networks.

---

## 📚 Lab Breakdown

### 🔹 Part 1 – DHCP Server & Relay

- Configured **DHCP pools on R2**:
  - 192.168.1.0/24 (reserved .1–.10)  
  - 192.168.2.0/24 (reserved .1–.10)  
  - Configured DNS and domain name  

- Configured **R1 as DHCP client** on WAN interface  

- Configured **DHCP relay (ip helper-address)** on R1  
  - Forwarded DHCP requests to R2  

- Verified:
  - PCs received IP addresses from remote DHCP server  

---

### 🔹 Part 2 – Dynamic NAT

- Configured NAT on R1:
  - Defined inside and outside interfaces  
  - Created NAT pool (100.0.0.1–100.0.0.2)  

- Translated internal network (172.16.0.0/24) to public IP pool  

- Verified:
  - Limited number of translations (pool exhaustion behavior)  

---

### 🔹 Part 3 – PAT (NAT Overload)

- Replaced dynamic NAT with **PAT using R1’s public IP**  

- Enabled multiple hosts to share a single public IP  

- Verified:
  - All PCs successfully reached external network  
  - NAT table shows port-based translations  

---

### 🔹 Part 4 – Static NAT

- Configured **static NAT mappings**:
  - Mapped internal hosts to fixed public IPs  

- Verified:
  - Consistent one-to-one address translation  
  - Reachability to external server (8.8.8.8)  

- Observed NAT table behavior after clearing translations  

---

## 🧠 Key Concepts Demonstrated

- DHCP server configuration  
- DHCP relay (ip helper-address)  
- NAT inside vs outside interfaces  
- Dynamic NAT (pool-based translation)  
- PAT (many-to-one translation)  
- Static NAT (one-to-one mapping)  
- NAT table behavior and limitations  

---

## ✅ Validation

- `show ip dhcp binding`  
- `show ip nat translations`  
- `show ip nat statistics`  
- `show ip interface brief`  
- End-to-end ping tests (8.8.8.8)  

---

## 🔍 Troubleshooting Performed

- Verified DHCP relay configuration for remote clients  
- Diagnosed NAT failures due to missing inside/outside assignment  
- Observed dynamic NAT pool exhaustion  
- Confirmed PAT resolves scalability limitations  

---

## 📌 Key Takeaway

- **DHCP relay** enables centralized IP address management across networks  
- **Dynamic NAT** is limited by available public IPs  
- **PAT** allows many devices to share a single public IP  
- **Static NAT** provides consistent address mapping for specific hosts

- PAT is the most commonly used NAT method in enterprise networks because it conserves public IP addresses while allowing full internet access for internal hosts.
