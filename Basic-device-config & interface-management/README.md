# Basic Device Configuration and Interface Management Lab

## Overview
This lab demonstrates basic device configuration and interface management in a small routed and switched network. I configured hostnames, IP addressing, interface speed and duplex, interface descriptions, and administratively disabled unused interfaces. The lab focuses on establishing correct Layer 1-3 connectivity and validating communication between hosts in a single subnet.

## Objectives
- Configure hostnames on R1, SW1, and SW2
- Configure IP addresses on R1, PC1, PC2, PC3, and PC4
- Manually configure speed and duplex on interfaces connected to other networking devices
- Configure interface descriptions
- Disable interfaces that are not connected to other devices
- Verify connectivity using ping and show commands

## Topology Summary
- 1 Cisco 2911 Router (R1)
- 2 Cisco 2960-24TT Switches (SW1 and SW2)
- 4 PCs in the same subnet (172.16.0.0/16)
- R1 connected to SW1 via G0/0
- SW1 connected to SW2 via G0/2 -> G0/1
- PCs connected to switches using FastEthernet ports

## Initial Conditions
- Router and switches had default hostnames
- Router interface was administratively down
- PCs had no IP configuration
- Switch interfaces used default speed/duplex and had no descriptions

## Traffic Flow (PC1 Ping PC4)
- PC1 sends an ICMP Echo Request to PC4
- Frame is forwarded from SW1 to SW2
- PC4 replies with an ICMP Echo Reply.
- Traffic successfully traverses SW2 -> SW1 -> PC1

## Observations
- All PCs successfully communicate within the same subnet
- Switches forward frames based on MAC address learning
- Router interface provides a default gateway if external routing is later required
- Interfaces with manually configured speed and duplex remain stable

## Verifcation
- Router
  - show ip interface brief
  - show running-config
- Switches
  - show interfaces status
  - show running-config
- PCs
  - ipconfig
  - ping <destination-ip>



