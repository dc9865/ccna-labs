## Overview
This lab examines how floating static routes provide redundancy between enterprise edge routers. A dynamic routing protocol is used for normal operations, while higher–administrative distance static routes act as backups when the primary link fails.

## Objectives
- Identify the dynamic routing protocol
- Examine routing tables on R1 and R2
- Determine path used for internal traffic
- Determine path used for Internet traffic
- Configure floating static routes
- Simulate link failure and verify failover

## Dynamic Routing Protocol
- Protocol: OSPF
- Verified with:
  - 'show ip route'

## Path Selection
- PC1 → SRV1
  - Path: PC1 → R1 → R2 → SRV1
  - Learned via OSPF
- PC1 → 1.1.1.1
  - Path: PC1 → R1 → ISPDR1 → Internet
  - Uses default static route

## Floating Static Routes
- Purpose: Provide backup path if OSPF route is lost
- Configured on R1:
  - ip route 10.0.2.0 255.255.255.0 203.0.113.1 111
- Configured on R2:
  - ip route 10.0.1.0 255.255.255.0 203.0.113.5 111
- Reason:
  - Administrative Distance 111 is higher than OSPF (110), so routes activate only during failure.

## Failure Test
- Shutdown inter-router link:
- Configured on R1:
  - interface g0/2/0
  - shutdown
- Verified with:
  - 'show ip route'
 
## Observations
- OSPF routes are preferred during normal operation
- Floating static routes are hidden
- When link fails, floating static routes appear
- Connectivity between PC1 and SRV1 remains

## Configuration
Full device configs are available in the configs folder.

