# Layer 2 Security Lab (DHCP Snooping, DAI, Port Security)

This lab demonstrates Layer 2 security features used to prevent common attacks such as rogue DHCP servers, ARP spoofing, and unauthorized device access.
These features are critical for securing Layer 2 networks in real-world enterprise environments.

---

## 📚 Lab Breakdown

### 🔹 Part 1 – DHCP Server & Snooping

- Configured R1 as a **DHCP server**:
  - Excluded address range (192.168.1.1 – 192.168.1.9)  
  - Set default gateway  

- Enabled **DHCP Snooping** on SW1 and SW2  
- Configured uplink interfaces as **trusted ports**  

- Verified DHCP operation:
  - Tested IP assignment using DHCP clients  
  - Identified failure due to untrusted interfaces  

- Applied necessary fixes to restore DHCP functionality  

---

### 🔹 Part 2 – Dynamic ARP Inspection (DAI)

- Enabled **DAI** on SW1 and SW2  

- Configured:
  - Trusted interfaces (uplinks)  
  - Validation checks (IP, MAC consistency)  

- Verified ARP traffic filtering:
  - Ensured only valid ARP packets are forwarded  

---

### 🔹 Part 3 – Port Security

- Configured **port security** on access interfaces  

**SW1:**
- Violation mode: Shutdown  
- Maximum MAC addresses: 1  
- Sticky learning: Disabled  
- Aging time: 1 hour  

**SW2:**
- Violation mode: Restrict  
- Maximum MAC addresses: 4  
- Sticky learning: Enabled  

- Triggered violations:
  - Connected unauthorized devices  
  - Observed switch response behavior  

---

## 🧠 Key Concepts Demonstrated

- DHCP Snooping (trusted vs untrusted ports)  
- Rogue DHCP prevention  
- Dynamic ARP Inspection (DAI)  
- ARP spoofing mitigation  
- Port security (MAC limiting, sticky MAC)  
- Violation modes (shutdown vs restrict)  
- Layer 2 attack prevention  

---

## ✅ Validation

- `show ip dhcp snooping`  
- `show ip dhcp snooping binding`  
- `show ip arp inspection`  
- `show port-security`  
- DHCP IP assignment tests  

---

## 🔍 Troubleshooting Performed

- Identified DHCP failure due to untrusted uplink ports  
- Verified DHCP Snooping bindings for DAI operation  
- Diagnosed blocked ARP packets  
- Observed port security violations and switch actions  

---

## 📌 Key Takeaway

- **DHCP Snooping** prevents rogue DHCP servers  
- **DAI** protects against ARP spoofing attacks  
- **Port Security** restricts unauthorized device access
