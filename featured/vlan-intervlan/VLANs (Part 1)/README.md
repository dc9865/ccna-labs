# Lab 16 - Inter-VLAN Routing and VLSM Address Management

## Overview
This lab demonstrates the implementation of a segemented network using VLANS and a Router-on-Interfaces approach. The focus is on applying VLSM to a specific address block (10.0.0.0/24) to create distinct broadcast domains for Engineering, HR, and Sales departments. 

## Objectives
1. Subnetting: Divide the 10.0.0.0/24 block into three /26 subnets to follow departmental requirements.
2. End-Device Configuration: Assign the first usable IP addresses to PCs and configure the last usable IP as the default gateway.
3. Layer 2 Segmentation: Configure VLANS 10, 20, and 30 on the switch and assign phyical ports accordingly.
4. Inter-VLAN Routing: Configure three physical interfaces on R1 to act as the gateway for each respective VLAN.
5. Validation: Utilize Simulation Mode to observe broadcast doamin boundaries and verify end-to-end connectivity.

## Topology Summary
- Router: R1 (Cisco 2911) 
- Switch: SW1 (Multi-port Bridge)
- VLANS: 
  - VLAN 10: Engineering
  - VLAN 20: HR
  - VLAN 30: Sales

## Subnetting & Addresing Plan
All subnets utilize a /26 mask (255.255.255.192), providing 62 usable host addresses per subnet.

  VLAN, Department, Subnet ID, IP Range, Gateway (Last Usable)
  10, Engineering, 10.0.0.0/26, .1 - .62, 10.0.0.62
  20, HR, 10.0.0.64/26, .65 - .126, 10.0.0.126
  30, Sales,10.0.0.128/26, .129 - .190, 10.0.0.190

## Configuration Highlights
Switch (SW1)
- Created and named VLANs 10 (Engineering), 20 (HR), and 30 (Sales).
- Assigned all departmental interfaces to their respective access VLANs.
  - VLAN 10: PC ports (F3/1, F4/1) and Router uplink (G0/1).
  - VLAN 20: PC ports (F5/1, F6/1) and Router uplink (G1/1).
  - VLAN 30: PC ports (F7/1, F8/1) and Router uplink (G2/1).
- By placing the router's physical interfaces into the same access VLANs as the PCs, each interface effectively joins into the correct broadcast domain to serve as the default gateway.

Router (R1)
- Interface G0/0: Assigned 10.0.0.62 (Gateway for Engineering)
- Interface G0/1: Assigned 10.0.0.126 (Gateway for HR)
- Interface G0/2: Assigned 10.0.0.190 (Gateway for Sales)
- Pre-configuration: 'no shutdown' command was applied to all interfaces.

## Troubleshooting & Observations
Problem #1
- Problem: When sending a broadcast ping from PC1, only PC2 receives it.
- Root Cause: VLANs successfully segment broadcast domains. The router does not forward Layer2 broadcasts between interfaces.
- Solution: Confirmed that the design is working as intended to reduce network congestion.

Problem #2
- Problem: PCs could not ping their gateway even with correct IP settings.
- Root Cause: The switchports connected to the Router were left in the default VLAN 1.
- Solution: Moved Switch ports G0/1, G1/1, and G2/1 into VLANS 10, 20, and 30.

## Verification
- Ping Test: Successful ICMP echo requests between PC1 (Eng.) and PC5 (Sales).
- Show Commands:
  - 'show vlan brief' on SW1 to verify port assignments.
  - 'show ip route' on R1 to verify all three subnets are "Directly Connected".


