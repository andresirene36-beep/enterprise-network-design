# Enterprise Network Design and Implementation

## 1. Project Overview

This project involves the design, configuration, and implementation of an enterprise network infrastructure using Cisco networking devices in a GNS3 lab environment.

The network is designed to support different departments within an organization through VLAN-based segmentation, inter-VLAN routing, centralized network services, gateway redundancy, NAT/PAT, and access control.

The project demonstrates practical network engineering concepts, configuration, testing, and troubleshooting.

## 2. Project Objectives

- Design a structured enterprise network infrastructure.
- Implement VLAN-based network segmentation.
- Configure inter-VLAN routing.
- Implement gateway redundancy using HSRP.
- Configure centralized DHCP and DNS services.
- Implement NAT/PAT for external network access.
- Configure static SSH port forwarding for remote device access.
- Apply Access Control Lists (ACLs) to control network traffic.
- Verify network connectivity and troubleshoot network issues.

## 3. Technologies and Tools

- GNS3 – Network lab environment.
- Cisco IOSv Routers.
- Cisco IOSvL2 Switches.
- Ubuntu Server.
- Kea DHCP Server.
- BIND9 DNS Server.
- Linux networking tools.
- SSH for remote device administration.

## 4. Network Features

- VLAN segmentation.
- IEEE 802.1Q trunking.
- Spanning Tree Protocol (STP).
- Inter-VLAN routing.
- HSRP gateway redundancy and failover.
- Centralized DHCP and DNS services.
- NAT/PAT overload.
- Static SSH port forwarding.
- ACL-based traffic filtering.
- Network connectivity testing and troubleshooting.

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

- DHCP address pools for VLANs 10, 20, 30, 40, 50, and 60.
- Default gateway information for each VLAN.
- DNS server and domain information.
- DHCP relay support for remote VLANs.

Configuration file: `configs/server/dhcp/kea-dhcp4.conf`

### 5.3 DNS Configuration

BIND9 is configured to provide centralized DNS resolution.

The DNS configuration includes:

- Forward lookup zone: `company.test`
- Reverse lookup zone: `50.168.192.in-addr.arpa`
- Internal DNS records.
- DNS forwarding to external DNS resolvers.

Configuration files are located in `configs/server/dns/`.

### 5.4 Server Configuration Directory

The Ubuntu Server configuration files are organized as follows:

- `dhcp/` – Kea DHCP configuration.
- `dns/` – BIND9 forward and reverse lookup configurations.
- `network/` – Netplan network configuration.

## 6. Network Architecture

The network consists of two Cisco routers, two Layer 2 switches, an Ubuntu Server, and end devices distributed across six VLANs.

The routers provide inter-VLAN routing, HSRP gateway redundancy, NAT/PAT, and traffic filtering. The switches provide VLAN segmentation and trunk connectivity.

### Network Topology

The following diagram illustrates the enterprise network architecture, including network devices, VLAN segmentation, and interconnections.

![Enterprise Network Topology](diagrams/Enterprise_Network_Design.png)

## 7. Project Documentation

Detailed project documentation is organized as follows:

- [Network Design](docs/network-design.md)
- [Project Requirements](docs/requirements.md)
- [VLAN and IP Addressing Plan](docs/vlan-ip-addressing.md)
- [Security Policy](docs/security-policy.md)
- [Network Testing and Verification Results](docs/test-results.md)

Additional resources:

- `configs/` – Router, switch, and Ubuntu Server configuration backups.
- `diagrams/` – Network topology diagrams.
- `evidence/` – Testing screenshots and verification evidence.
- `troubleshooting/` – Troubleshooting records and solutions.

## 8. Project Status

The enterprise network infrastructure has been implemented and tested in the GNS3 lab environment.

Verified functionality includes:

- VLAN configuration and trunk connectivity.
- Inter-VLAN routing.
- HSRP gateway redundancy and failover.
- Centralized DHCP and DNS services.
- NAT/PAT and static SSH port forwarding.
- ACL configuration and connectivity testing across all six VLANs.

Web server deployment and HTTP service testing have not yet been implemented.

