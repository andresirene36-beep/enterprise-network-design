# Network Security Policy

## 1. Overview

Network security is implemented through VLAN segmentation and router-based Access Control Lists (ACLs).

The objective is to control communication between departments, protect centralized services, and restrict unauthorized network access.

## 2. Security Mechanisms

The following mechanisms are implemented:

- VLAN segmentation to separate departmental traffic.
- Extended ACLs to filter traffic based on source, destination, protocol, and port.
- Controlled access to centralized DHCP and DNS services.
- Restricted management access.
- Guest network traffic restrictions.
- NAT/PAT for translation of private internal addresses.

## 3. Departmental Access Control

ACL policies are configured to regulate communication between:

- Administration VLAN (10).
- Finance VLAN (20).
- IT VLAN (30).
- Management VLAN (40).
- Servers VLAN (50).
- Guests VLAN (60).

Each department is subject to its configured access policy.

## 4. Centralized Services Protection

Access to centralized network services is controlled through ACL rules.

- DHCP traffic is permitted to support automatic IP address allocation.
- DNS traffic is permitted to support domain name resolution.
- Administrative access to infrastructure is restricted according to configured policies.

## 5. Management Security

The management network is logically separated using VLAN 40.

Access to network management services is controlled through configured ACL policies.

## 6. Guest Network Isolation

Guest VLAN 60 is restricted from accessing internal organizational networks using router-based ACLs. Permitted external network access is maintained through NAT/PAT.

## 7. Security Verification

Security policies are verified through connectivity tests between VLANs and inspection of router ACL configurations and match counters.

Detailed test evidence is maintained in the `evidence/` directory.
