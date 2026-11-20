# Network Testing and Verification

## 1. Overview

This document records the verification activities performed to evaluate the functionality of the enterprise network infrastructure.

Testing focuses on VLAN operation, trunk connectivity, inter-VLAN routing, gateway redundancy, centralized network services, NAT/PAT operation, access control, and external connectivity.

## 2. Testing Summary

| No. | Test Area | Verification Method | Result |
|---|---|---|---|
| 1 | VLAN Configuration | `show vlan brief` on SW1 and SW2 | PASS |
| 2 | Trunk Links | `show interfaces trunk` on SW1 and SW2 | PASS |
| 3 | Inter-VLAN Routing | Ping between devices in different VLANs | PASS |
| 4 | HSRP Redundancy | `show standby brief` and router failover test | PASS |
| 5 | DHCP Services | Dynamic IP address allocation and lease verification | PASS |
| 6 | DNS Services | Internal and external domain name resolution | PASS |
| 7 | NAT/PAT | `show ip nat statistics`, `show ip nat translations`, and Internet connectivity test | PASS |
| 8 | ACL Security | ACL configuration inspection and Guest VLAN connectivity tests | PASS |
| 9 | Web Service | HTTP access test | NOT IMPLEMENTED |

## 3. Verification Evidence

### 3.1 VLAN Configuration

Verification was performed using `show vlan brief` on both switches.

- VLANs 10, 20, 30, 40, 50, and 60 were configured.
- All six VLANs were active on both switches.

Result: PASS.

### 3.2 Trunk Links

Verification was performed using `show interfaces trunk`.

- Trunk links were operational on both switches.
- IEEE 802.1Q encapsulation was used.
- VLANs 10, 20, 30, 40, 50, and 60 were allowed and forwarding.

Result: PASS.

### 3.3 Inter-VLAN Routing

Connectivity testing was performed between devices in different VLANs.

- VLAN 10 device successfully reached its default gateway.
- Communication between VLAN 10 and VLAN 20 was successful.

Result: PASS.

### 3.4 HSRP Gateway Redundancy

HSRP operation was verified using `show standby brief`.

- R1 operated as the Active router.
- R2 operated as the Standby router.
- R1 was configured with a higher priority.
- During the failover test, R1's interface was shut down.
- R2 successfully became Active.
- Connectivity to the virtual gateway was maintained during failover.
- R1 resumed the Active role after its interface was restored.

Result: PASS.

### 3.5 DHCP Services

The Ubuntu Server running Kea DHCP was configured to provide dynamic IP address allocation across the VLANs.

Verification confirmed that:

- A client in VLAN 10 obtained an IP address automatically.
- The assigned address was `192.168.10.100/24`.
- The default gateway was `192.168.10.1`.
- The DHCP server and DNS server were `192.168.50.10`.
- The domain name was `company.test`.

Result: PASS.

### 3.6 DNS Services

DNS resolution was tested using internal and external domain names.

- `ns1.company.test` resolved to `192.168.50.10`.
- `www.company.test` resolved to `192.168.50.20`.
- `google.com` resolved successfully.

Observation:

ICMP connectivity from the tested client to `192.168.50.10` was unsuccessful. However, DNS name resolution was successful.

Result: PASS for DNS resolution.

### 3.7 NAT/PAT

NAT/PAT operation was verified using:

- `show ip nat statistics`
- `show ip nat translations`

Verification confirmed:

- GigabitEthernet0/1 was configured as the NAT outside interface.
- Internal VLAN interfaces were configured as NAT inside interfaces.
- Dynamic PAT was configured using access-list 1 and interface overload.
- Five static SSH port forwarding translations were present.
- Dynamic translations were observed.
- NAT statistics recorded translation hits.

Internet connectivity was also verified from a Guest VLAN client.

Result: PASS.


### 3.8 ACL Security

Access control lists were verified across all six VLANs using connectivity tests and ACL inspection.

Verification confirmed:

- ACL policies were configured for VLANs 10, 20, 30, 40, 50, and 60.
- ACLs were attached to their respective VLAN interfaces.
- Traffic was permitted or denied according to the configured security policies.
- Guest VLAN access to internal private networks was restricted.
- Internet connectivity from the Guest VLAN was successful.

Result: PASS.

### 3.9 Web Service

An HTTP web service has not yet been deployed and tested in this project.

Result: NOT IMPLEMENTED.

## 4. Troubleshooting

Issues encountered during implementation and their corresponding solutions are documented in the `troubleshooting/` directory.

## 5. Conclusion

The implemented enterprise network successfully demonstrated VLAN segmentation, trunk connectivity, inter-VLAN routing, HSRP gateway redundancy, centralized DHCP and DNS services, NAT/PAT operation, and ACL-based traffic control.

Access control policies were configured and verified across all six VLANs through connectivity testing and ACL inspection.

Implementation and testing of a web service remain outstanding.
