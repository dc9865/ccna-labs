# Lab 12 - Routed Path MAC address Analysis & ARP Behavior Lab

## Overview
This lab demonstrates the fundamental behavior of MAC address rewriting across a routed topology. While IP addresses (Layer 3) remain constant from source to destination, MAC addresses (Layer 2) change at every routing boundary.

## Objectives
- Analyze source and destination MAC addresses at each hop when traffic crosses routers
- Observe how ARP operates on a per-hop basis in a routed topology
- Verify MAC address rewriting at router boundaries
- Practice structured troubleshooting and validation using CLI and simulation mode
- Document golden configuration standards and problem/solution fixes

## Topology Summary
- Routers: R1, R2, R3 (Cisco 2911)
- Switches: SW1, SW2 (Cisco 2960)
- End Devices:
  - PC1, PC2, Pc3 in 192.168.1.0/24
  - PC4, PC5, PC6 in 192.168.3.0/24
- WAN/Point-to-Point Links:
  - R1-R2: 192.18.12.0/24
  - R2-R3: 192.168.13.0/24

## Troubleshooting & Problem/Solution Documentation
- The Problem: Initial pings from PC1 to PC4 failed in the Simulation environment, even though all IP addresses and routing protocols were correctly configured.
- Troubleshooting Steps:
  1. Verification: I checked the ARP table on PC1 (arp -a). The table was empty.
  2. Analysis: PC1 did not know the MAC address of its Default Gateway (R1 G0/0).
  3. Observation: In Simulation mode, I observed the first ICMP packet being dropped while the ARP Request was broadcasted.
  4. The "Golden Config" Fix: Ensured all interfaces were in the up/up state and verified that the Default Gateway on PC1 was set to 192.168.1.254 (R1 G0/0). Once ARP resolved, the end-to-end connectivity was established.
 
## Path Anaylsis: PC1 (192.168.1.1) -> PC4(192.168.3.1)
Below is the identification of Source and Destination MAC addresses as the packet traverses the network.
- Segment, Source MAC, Destination MAC
  A. PC1 → SW1, MAC of PC1 (F0), MAC of R1 (G0/0)
  B. SW1 → R1, MAC of PC1 (F0), MAC of R1 (G0/0)
  C. R1 → R2, MAC of R1 (G0/1), MAC of R2 (G0/0)
  D. R2 → R3, MAC of R2 (G0/1), MAC of R3 (G0/0)
  E. R3 → SW2, MAC of R3 (G0/1), MAC of PC4 (F0)
  F. SW2 → PC4, MAC of R3 (G0/1), MAC of PC4 (F0)

## Verification
To reproduce these results in Packet Tracer:
1. Enter Simulation Mode
2. Filter for ICMP and ARP.
3. Run ping 192.168.3.1 from PC1.
4. Click the PDU at each hop and inspect the Inbound/Outbound PDU Details to see the MAC addresses change.
