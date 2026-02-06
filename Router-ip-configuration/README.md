# Lab 8 - IPv4 Addresses Lab

## Overview
This lab demonstrates the configuration of a Cisco router and multiple PCs across different subnets using Cisco Packet Tracer. IP addresses on router interfaces and end-devices are configured. Commands such as 'ping' and 'show' are used to enable interfaces and verify connectivity. The lab emphasizes understanding routing basics, IP addressing, and inter-network communication.

## Objectives
- Configure a router hostname and interface IP addresses.
- Enable router interfaces and configure interface descriptions.
- Assign appropriate IP addresses to PCs in different subnets.
- Verify interface status and IP configuration using 'show' commands.
- Test network connectivity using 'ping' between PCs across different subnets.

## Topology Summary
- Router: 1 Cisco Router (R1) with 3 interfaces (G0/0, G0/1, G0/2)
- Switches: 3 Cisco 2960-24TT switches (SW1, SW2, SW3)
- PCs: 3 PCs (PC1, PC2, PC3) in separate subnets

## Initial Conditions
- All router interfaces are administratively down.
- PCs are not yet configured with IP addresses.

## Traffic Flow
- PCs send ICMP ping requests to test connectivity across different subnets.
- Router forwards traffic between subnets based on interface IP configuration.

## Verifcation
From PCs
- ping 182.98.0.1
- ping 201.191.20.1

From Router
- show ip interface brief
- show running-config

## Procedure Summary
1. Configure router hostname:
   - 'R1(config)# hostname R1"
2. Use 'show ip interface brief' to view interface status and IP addresses.
3. Configure router interfaces with IP addresses and enable them:
   - R1(config)# interface g0/0
   - R1(config-if)# ip address 15.255.255.254 255.0.0.0
   - R1(config-if)# no shutdown
(Repeat for G0/1 and G0/2 with corresponding IPs.)
4. Verify interface status with 'show ip interface brief'.
5. Configure PCs with IP addresses and default gateways (router interface IPs).
6. Test connectivity:
   - Ping from PC1 -> PC2
   - Ping from PC1 -> PC3
   - Ping from PC2 -> PC3
7. Use 'show running-config' to confirm configurations.

## Expected Observations
- All pings between PCs across different subnets should succeed.
- Router interfaces should be up/up after configuration.
