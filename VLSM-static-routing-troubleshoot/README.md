# Lab 15 - Enterprise VLSM Design and Static Routing Optimization

## Overview
This lab focuses on designing an IP addressing scheme using Variable Length Subnet Mask (VLSM) to minimize address wastage while ensuring scalable routing across a distributed enterprise network. It goes beyond basic configuration by implementing a "Golden Config" standard and documenting a critical routing failure and its resolution.

## Objectives
- Subnet the 192.18.5.0/24 network to satisfy each LAN's host requirement.
- Assign the first usable IP address to the PC in each LAN.
- Assign the last usable IP address to the router's interface in each LAN.
- Configure static routing so that all PCs can ping each other successfully.
- Document the configuration and troubleshooting steps.

## Topology Summary
- Routers: R1, R2 (Cisco 2911)
- Switches: SW1, SW2, SW3, SW4 (Cisco 2960)
- End Devices:
  - PC1, PC2, PC3, PC4
- Point-to-Point Links:
  - R1 G0/0/0 <-> R2 G0/0/0

## Subnetting Plan
- LAN1 (45 hosts) -> /26 -> 192.168.5.0 - 192.168.5.63
  - PC1: 192.168.5.1
  - Router R1 G0/0: 192.168.5.62
- LAN2 (64 hosts) -> /25 -> 192.168.5.64 - 192.168.5.127
  - PC2: 192.168.5.65
  - Router R1 G0/1: 192.168.5.126
- LAN3 (14 hosts) -> /28 -> 192.168.5.128 - 192.168.5.143
  - PC3: 192.168.5.129
  - Router R2 G0/0: 192.168.5.142
- LAN4 (9 hosts) -> /28 -> 192.168.5.144 - 192.168.5.159
  - PC4: 192.168.5.145
  - Router R2 G0/1: 192.18.5.158
- Point-to-Point R1 <-> R2 -> /30 -> 192.168.5.160 - 192.168.5.163
  - R1 G0/0/0: 192.168.5.161
  - R2 G0/0/0: 192.168.5.162
 
## Problem/Solution
1. PCs cannot ping across LANs
  - Symptoms: PC1 can ping PC2 but cannot ping PC3 or PC4.
  - Root cause: Missing static routes on the routers.
  - Solution: Added static routes on R1 and R2 pointing to each other's LAN subnets via the point-to-point interface.

2. IP addressing conflicts or insufficient hosts
  - Symptoms: Some PCs could not communicate with the router interface.
  - Root cause: Improper subnet mask selection or overlapping subnets.
  - Solution: Recalculated subnet masks according to host requirements. Ensured first usable IP assigned to PC and last usable IP to router interface.

3. Intermittent ping failures
   - Symptomps: Ping succeeds occasionally.
   - Root cause: Interface shutdown on routers or incorrect cable connections.
   - Solution: Verified physical connections, ensured interfaces were 'no shutdown', and verified correct IP addresses.

## Verification
1. Ping from PC1 -> PC2 -> PC3 -> PC4 to ensure full connectivity.
2. Use 'show ip route' on routers to verify routing table correctness.
3. Use 'ping' and 'traceroute' commands to verify proper routing paths.
