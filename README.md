# Enterprise Network Design and Implementation

## 1. Project Overview

This project involves the design, configuration, and implementation of an enterprise network infrastructure using Cisco networking devices in GNS3.

The network is designed to support different departments within an organization through network segmentation, inter-VLAN communication, centralized services, redundancy, and access control.

## 2. Project Objectives

- Design a structured enterprise network infrastructure.
- Implement VLAN-based network segmentation.
- Configure inter-VLAN routing.
- Implement gateway redundancy using HSRP.
- Configure centralized DHCP and DNS services.
- Implement NAT/PAT for external network access.
- Apply Access Control Lists (ACLs) to control network traffic.
- Verify network connectivity and troubleshoot network issues.

## 3. Technologies and Tools

- GNS3 – Network simulation and lab environment.
- Cisco IOSv Routers.
- Cisco IOSvL2 Switches.
- Ubuntu Server.
- Kea DHCP Server.
- BIND9 DNS Server.
- Linux networking tools.

## 4. Network Features

- VLAN segmentation.
- 802.1Q trunking.
- Spanning Tree Protocol (STP).
- Inter-VLAN routing.
- HSRP gateway redundancy.
- DHCP and DNS services.
- NAT/PAT.
- ACL-based traffic filtering.

## 5. Ubuntu Server Configuration and Services

An Ubuntu Server was integrated into VLAN 50 to provide centralized network services for the enterprise infrastructure.

The server provides DHCP and DNS services and uses Netplan for network interface configuration.

### 5.1 Network Configuration

The Ubuntu Server uses a static IP address to ensure consistent network accessibility.

| Parameter | Configuration |
|---|---|
| Hostname | ubuntu-server |
| Interface | ens3 |
| IP Address | 192.168.50.10/24 |
| Default Gateway | 192.168.50.1 |
| VLAN | 50 |

Configuration file: `configs/server/network/00-installer-config.yaml`

### 5.2 DHCP Configuration

Kea DHCPv4 is configured to provide automatic IP address allocation to client devices across the enterprise VLANs.

The configuration includes:
- DHCP address pools for VLANs 10, 20, 30, 40, 50 and 60.
- Default gateway information for each VLAN.
- DNS server and domain information.
- DHCP relay support for remote VLANs.

Configuration file: `configs/server/dhcp/kea-dhcp4.conf`

### 5.3 DNS Configuration

BIND9 is configured to provide centralized DNS resolution.

The DNS configuration includes:
- Forward lookup zone: `company.test`
- Reverse lookup zone: `50.168.192.in-addr.arpa`
- DNS records for internal network devices.
- DNS forwarding to external DNS resolvers.

Configuration files are located in `configs/server/dns/`.

### 5.4 Server Configuration Directory

The Ubuntu Server configuration files are organized as follows:

- `dhcp/` – Kea DHCP configuration.
- `dns/` – BIND9 forward and reverse lookup configurations.
- `network/` – Netplan network configuration.

## 6. Network Architecture

The network consists of two routers, two Layer 2 switches, an Ubuntu server, and end devices distributed across multiple VLANs.

### Network Topology

The following diagram illustrates the enterprise network architecture, including network devices, VLAN segmentation, and interconnections.

![Enterprise Network Topology](diagrams/Enterprise_Network_Design.png)

## 7. Project Documentation

Detailed network design, configurations, testing evidence, and troubleshooting records are organized in the respective project directories.

## 8. Project Status

Network implementation and verification are documented progressively as part of this engineering portfolio.
