# Day 22 - Rapid Spanning Tree Protocol (RSTP) Lab

## Overview
This lab examines Rapid Spanning Tree Protocol (RSTP) behavior in a multi-switch topology. The root bridge is identified, port roles and states are analyzed, and RSTP link types are manually configured.

---

## Objectives
1. Identify the root bridge
2. Examine root bridge port roles
3. Determine port role/state on non-root switches without CLI
4. Verify results using CLI
5. Manually configure RSTP link types
6. Determine correct link type for SW1 F0/24

---

## Root Bridge
- Root Bridge: **SW1**
- Verified with: 'show spanning-tree'
- Reason: All switches have default priority; SW1 has the lowest MAC address.

---

## Observations
- All root bridge ports are "Designated"
- Non-root switches contain "Root Ports" and "Alternate Ports"
- RSTP converges faster than classic STP

---

## RSTP Link Types
- Switch-to-switch links -> Point-to-point
- Hub-connected link (SW1 F0/24) -> Shared
- Configured with:
  - 'spanning-tree link-type point-to-point'
  - 'spanning-tree link-type shared'
- Verified with:
  - 'show spanning-tree'

---

## 🔧 Configuration
Full device configs are available in the configs folder.

