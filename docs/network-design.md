# Network Design and Architecture

## 1. Design Overview

The enterprise network is designed using a hierarchical and segmented architecture to support multiple departments, centralized services, secure communication, and gateway redundancy.

The infrastructure consists of two Cisco routers, two Layer 2 switches, an Ubuntu server, and end devices distributed across six VLANs.

## 2. Network Components

| Device | Role |
|---|---|
| R1 | Primary enterprise router and HSRP gateway |
| R2 | Secondary enterprise router and HSRP gateway |
| SW1 | Primary Layer 2 access switch |
| SW2 | Secondary Layer 2 access switch |
| Ubuntu Server | Centralized DHCP and DNS services |
| End Devices | Departmental client devices |
| NAT Node | Provides external network connectivity in the lab |

## 3. Network Segmentation

Six VLANs are implemented to logically separate departmental traffic:

- VLAN 10 – Administration
- VLAN 20 – Finance
- VLAN 30 – IT
- VLAN 40 – Management
- VLAN 50 – Servers
- VLAN 60 – Guests

Each VLAN uses a dedicated /24 IPv4 subnet.


## 4. Routing Architecture

Inter-VLAN routing is implemented using router subinterfaces with IEEE 802.1Q encapsulation.

R1 and R2 provide routing for the departmental VLANs. HSRP is configured to provide virtual default gateways and gateway redundancy.

R1 is configured with a higher HSRP priority and operates as the Active router, while R2 operates as the Standby router under normal operating conditions.

The virtual gateway address for each VLAN uses the `.1` address of its respective subnet.

## 5. Switching Architecture

SW1 and SW2 provide Layer 2 connectivity to end devices and network infrastructure.

802.1Q trunk links carry traffic for the required VLANs between network devices.

Spanning Tree Protocol (STP) is used to help prevent Layer 2 switching loops.

## 6. Centralized Network Services

An Ubuntu Server is connected to VLAN 50 and provides:

- DHCP using Kea DHCP Server.
- DNS using BIND9.

DHCP relay configuration allows clients in other VLANs to obtain IP addresses from the centralized DHCP server.

## 7. Network Security

Access Control Lists (ACLs) are implemented on the routers to regulate communication between VLANs according to departmental security policies.

NAT/PAT is configured to translate internal private IPv4 addresses for external network access.

## 8. Design Considerations

The design focuses on:

- Logical network segmentation.
- Availability through gateway redundancy.
- Centralized network services.
- Controlled inter-department communication.
- Simplified network administration and troubleshooting.
