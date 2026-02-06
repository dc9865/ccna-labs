# Day 24 - Floating Static Routing Lab

## Overview
This lab creates the network diagram based on instructions given. A branch-to-branch network is built using routers, switches, and firewalls, with an internet segment and an external attacker. The focus of this lab is correct topology creation and device placement.

## Objectives
- Build the required toplogy in Packet Tracer
- Place devices according to the diagram
- Connect all devices using automatic connection selection
- Identify network zones (inside, outside, Internet)
- Prepare topology for routing and security configuration

## Toplogy 
- New York Branch: PC1, PC2 -> SW1 -> R1 -> FW1
- Internet: FW1 -> Internet Router -> R2 -> FW2
- Tokyo Branch: FW2 -> SW2 -> SRV1, SRV2

## Devices Used
- Cisco 2911 Routers (2)
- Cisco 2960-24TT Siwtches (2)
- Cisco ASA 5505 Firewalls (2)
- PC-PT (2)
- Server-PT (2)
- Laptop-PT (Attacker) (1)

## Observations
- Each branch network is protected by a firewall
- A firewall can be placed after router and before router 
- Internet is treated as an untrusted network
- Internal users and servers are separated by switches
