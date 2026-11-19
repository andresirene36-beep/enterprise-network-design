# VLAN and IP Addressing Plan

## 1. Overview

The enterprise network uses VLAN segmentation to separate departmental traffic. Each VLAN is assigned a dedicated IPv4 subnet using a /24 network mask.

## 2. VLAN Allocation Table

| VLAN ID | VLAN Name | Network Address | Subnet Mask | HSRP Gateway |
|---|---|---|---|---|
| 10 | ADMINISTRATION | 192.168.10.0 | 255.255.255.0 | 192.168.10.1 |
| 20 | FINANCE | 192.168.20.0 | 255.255.255.0 | 192.168.20.1 |
| 30 | IT | 192.168.30.0 | 255.255.255.0 | 192.168.30.1 |
| 40 | MANAGEMENT | 192.168.40.0 | 255.255.255.0 | 192.168.40.1 |
| 50 | SERVERS | 192.168.50.0 | 255.255.255.0 | 192.168.50.1 |
| 60 | GUESTS | 192.168.60.0 | 255.255.255.0 | 192.168.60.1 |

## 3. Router Interface Addressing

Each router uses a dedicated IP address on the corresponding VLAN subinterface.

| VLAN | R1 Address | R2 Address | HSRP Virtual IP |
|---|---|---|---|
| 10 | 192.168.10.2 | 192.168.10.3 | 192.168.10.1 |
| 20 | 192.168.20.2 | 192.168.20.3 | 192.168.20.1 |
| 30 | 192.168.30.2 | 192.168.30.3 | 192.168.30.1 |
| 40 | 192.168.40.2 | 192.168.40.3 | 192.168.40.1 |
| 50 | 192.168.50.2 | 192.168.50.3 | 192.168.50.1 |
| 60 | 192.168.60.2 | 192.168.60.3 | 192.168.60.1 |

## 4. Server Addressing

| Service | IP Address | VLAN |
|---|---|---|
| Ubuntu DHCP/DNS Server | 192.168.50.10 | 50 |
| Web Server | 192.168.50.20 | 50 |

## 5. DHCP Allocation

Dynamic IP address allocation is provided by the centralized Kea DHCP server.

- DHCP address pool: 192.168.X.100 – 192.168.X.200 for applicable client VLANs.
- Subnet mask: 255.255.255.0.
- Default gateway: Corresponding HSRP virtual IP.
- DNS server: 192.168.50.10.
- DNS domain: company.test.

Server addresses are statically assigned outside the DHCP client allocation range.

## 6. Addressing Design Considerations

- Each department has its own IPv4 subnet.
- HSRP virtual IP addresses are used as client default gateways.
- Router interface addresses are reserved for infrastructure.
- Server addresses are statically assigned.
- DHCP provides automatic address allocation to client devices.
