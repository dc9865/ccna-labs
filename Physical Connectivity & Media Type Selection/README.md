# Lab 2 - Connecting Devices Lab

## Overview 
This lab focuses on connecting network devices according to labeled distances and selecting the appropriate cable types. Auto-MDIX is assumed to be disabled, requiring manual consideration of straight-through, crossover, and fiber connections. The toplogy includes multiple routers, swithces, end hosts, and a server distributed across two sites.

## Objectives 
- Connect devices according to topology labels
- Select appropriate copper or fiber cable types
- Practice cabling without reyling on Auto-MDIX
- Understandd distance-based media selection
- Verify physicial connectivity

## Topology Summary
- Left Site: PC1 -> SW3 -> SW1 -> R2 -> R1, PC2 -> SW4 -> SW2 -> R2, SW1 <-> SW2
- Right Site: PC3 -> SW7 -> SW5 -> R4 -> R3, SRV1 -> SW8 -> SW6 -> R4, SW5 <-> SW6
- Inter-Router Links: R1 <-> R3 (3km), R1 <-> R2 (50m), R3 <-> R4 (250m)

## Cable Selection Rules
Copper Straight-Through:
  - PC <-> Switch
  - Router <-> Switch
Copper Crossover:
  - Switch <-> Switch
  - Router <-> Router (short distances)
Fiber:
- Long-distance router-to-router links

## Observations
- Long-distance links require fiber connections
- Like-device copper connections require crossover cables
- Different-device copper connections require straight-through cables
