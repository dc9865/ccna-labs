# Lab 06 - Ethernet LAN Switching Lab

## Overview
This lab demonstrates how Address Resolution Protocol (ARP) and MAC address learning operate in a multi-switch topology. The behavior of ARP requests, ARP replies, and ICMP traffic is analyzed when end devices initially have empty ARP tables and switches have empty MAC address tables. 

## Objectives
- Observe ARP and ICMP message flow when a ping is initiated
- Identify which devices receive braodcast and unicast frames
- Generate traffic to populate switch MAC address tables
- Verify learned MAC addresses using CLI commands
- Clear dynamic MAC address table entries on switches

## Topology Summary
- Two Cisco 2960 switches (SW1 and SW2)
- Four PCS in the same subnet (192.168.1.0/24)
- Switches connected via G0/1
- PCs connected via FastEthernet ports

## Initial Conditions
- All switches have empty MAC address tables
- All PCs have empty ARP tables

## Traffic Flow (PC1 Ping PC3)
1. PC1 sends an ARP Request (broadcast) to discover PC3's MAC address
2. Both switches flood the ARP request out all ports except the incoming port
3. PC3 responds with an ARP Reply (unicast) to PC1
4. Switches learn source MAC addresses from incoming frames
5. PC1 sends ICMP Echo Request (unicast) to PC3
6. PC3 replies with ICMP Echo Reply (unicast)

## Observations
- ARP Requests are broadcast frames
- ARP Replies are unicast frames
- Switches learn MAC addresses from source MAC fields

## Verification
- On switches:
  - 'show mac address-table'
- To clear dynamic MAC addresses:
  - 'clear mac address-table dynamic'
- On PCs:
  - 'arp -a'
