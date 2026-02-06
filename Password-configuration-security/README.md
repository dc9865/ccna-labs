# Lab 04 - Basic Device Security Lab

## Overview
This lab focuses on configuring, testing, and securing device passwords on a router and switch. Users will set unecrypted and encrypted enable passwords, verify password security, and save the configuration to ensure persistence across device reloads.

## Objectives
- Change device hostnames
- Configure an unecrypted enable password
- Test unecrypted password in user EXEC mode
- View passowrds in the running configuration
- Encrypt all current and future passwords
- Configure a more secure, encrypted enable password
- Verify password type and encryption
- Save the running confiugration to the startup configuration

## Topology
- Router: 2911 (R1)
- Switch: 2960-24TT (SW1)
- PCs: PC1, PC2, PC3 connected to SW1

## Observations
1. Change Hostnames
  - Commands:
    - R1(config)# 'hostname R1'
    - SW1(config)# 'hostname SW1'
  - Observation: Hostnames updated successfully.

2. Configure Unencrypted Enable Password
  - Commands:
    - R1(config)# enable password CCNA
    - SW1(config)# enable password CCNA
  - Observation: Devices now require 'CCNA' to enter priviledged EXEC mode.

3. Test Password
  - Command: 'enable' in user EXEC mode
  - Observation: Password accepted; user enters privileged EXEC mode.

4. View Password in Running Configuration
  - Command: 'service password-encryption'
  - Observation: All unencrpyted passwords are now encrypted in the running configuration.

5. Encrypt Passwords
  - Command: 'service password-encryption'
  - Observation: All unencrypted passwords are now encrypted in the running configuration.

6. View Encrypted Passwords
  - Command: 'show running-config'
  - Observation: Plain text passwords are replaced with type 7 encrypted strings.

7. Configure Secure Encrypted Enable Password
  - Commands: 
    - R1(config)# enable secret Cisco
    - SW1(config)# enable secret Cisco
  - Observation: Devices now use a stronger, type 5 encrypted enable secret.

8. Verify Password in EXEC mode
  - Command: 'enable'
  - Observation: 'Cisco' must be used to enter privileged EXEC mode after secret configuration.

9. Check Encryption Types
  - Commands: 'show running-config'
  - Observation:
    - Enable password: type 7 
    - Enable secret: type 5

10. Save Configuration
  - Command: 'copy running-config startup-config'
  - Observation: Configuration saved; persists after reload.

