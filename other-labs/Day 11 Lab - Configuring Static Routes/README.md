# Lab 11 - Static Routing Between Multiple Routers Lab

## Overview
This lab demonstrates static routing between multiple routers to enable communication between hosts in different networks. IP addressing and default gateways were configured on end devices, IP addresses were assigned to router interfaces, and static routes were implemented so that PC1 and PC2 could successfully communicate across multiple routed networks.

## Objectives
- Configure hostnames and IP addressing on routers and PCs
- Configure default gateways on end devices
- Implement static routes on routers
- Verify end-to-end connectivity using ping
- Understand packet forwarding across multiple routers

## Topology Summary
- 3 Cisco 2911 routers (R1, R2, R3)
- 2 Cisco 2960-24TT switches (SW1 and SW2)
- 2 PCs (PC1 and PC2) located in different networks
- Multiple routed networks interconnected using Gigabit Ethernet links

## Network Segments
- 192.168.1.0/24 - PC1 LAN
- 192.168.12.0/24 - R1 <-> R2 link
- 192.168.13.0/24 - R2 <-> R3 link
- 192.168.3.0/24 - PC2 LAN

## Initial Conditions
- All routers and PCs had no pre-configurations
- No IP addresses were assigned
- No routing information existed
- No connectivity between PC1 and PC2

## Traffic Flow (PC1 Ping PC2)
1. PC1 sends an ICMP Echo Request to PC2.
2. PC1 forwards the packet to its default gateway (R1).
3. R1 forwards the packet to R2 using a static route.
4. R2 forwards the packet to R3 using a stiatc route.
5. R3 delivers the packet to PC2's local network.
6. PC2 replies with an ICMP Echo Reply, which follows the reverse path back to PC1.

## Observations
- Static routes are required for routers to reach non-directly connected networks
- Routers forward packets based on routing table entries
- End-to-end connectivity is achieved only after all required static routes are configured

## Verification
1. Routers:
  - show ip route
  - show ip interface brief
2. PCs:
  - ipconfig
  - ping [destination-ip]

## Procedure Summary
- Configured hostnames on R1, R2, and R3
  - hostname [device]
- Assigned IP addresses to all router interfaces according to the network diagram
  - interface [interface-id]
  - ip address [ip] [mask]
  - no shutdown
- Configured static IP addresses and default gateways on PC1 and PC2
- Configured static routes on R1, R2, and R3 to enable inter-network communication
  - ip route [destination-network] [subnet-mask] [next-hop]
- Verified routing tables using show commands
  - show ip route
- Successfully tested connectivity between PC1 and PC2 using ping
  - ping [destination-ip]
