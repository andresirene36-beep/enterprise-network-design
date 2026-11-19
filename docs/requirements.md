# Network Requirements Analysis

## 1. Introduction

The purpose of this project is to design and implement a structured enterprise network infrastructure that supports communication between different organizational departments while maintaining network security, reliability, and centralized services.

## 2. Functional Requirements

The network must support the following requirements:

1. **Department Segmentation:** Separate organizational departments using VLANs.
2. **Inter-VLAN Communication:** Allow controlled communication between different VLANs.
3. **Gateway Redundancy:** Provide high availability through HSRP using two routers.
4. **Dynamic IP Address Allocation:** Automatically assign IP addresses to end devices using DHCP.
5. **Domain Name Resolution:** Provide DNS services through a centralized DNS server.
6. **Internet Connectivity:** Provide external network access through NAT/PAT.
7. **Traffic Control:** Apply ACLs to restrict or permit traffic according to security policies.
8. **Network Management:** Provide a dedicated management VLAN.

## 3. Network Segmentation Requirements

The network is divided into six VLANs:

| VLAN | Department | Network |
|---|---|---|
| 10 | Administration | 192.168.10.0/24 |
| 20 | Finance | 192.168.20.0/24 |
| 30 | IT | 192.168.30.0/24 |
| 40 | Management | 192.168.40.0/24 |
| 50 | Servers | 192.168.50.0/24 |
| 60 | Guests | 192.168.60.0/24 |

## 4. Availability Requirements

- Two routers provide gateway redundancy using HSRP.
- Switching infrastructure supports VLAN trunking and Spanning Tree Protocol.
- Network services are centralized on the server infrastructure.

## 5. Security Requirements

- VLANs must be logically separated.
- ACLs must enforce departmental communication policies.
- Guest network access must be restricted according to the configured security policy.
- Management access must be controlled.

## 6. Expected Outcome

A functional enterprise network infrastructure that supports departmental connectivity, centralized network services, gateway redundancy, traffic control, and external network access.
