# Network Testing and Verification

## 1. Overview

This document records the verification activities performed to evaluate the functionality of the enterprise network infrastructure.

Testing focuses on VLAN operation, routing, gateway redundancy, centralized services, network security, and external connectivity.

## 2. Testing Summary

| No. | Test Area | Verification Method | Result |
|---|---|---|---|
| 1 | VLAN Configuration | `show vlan brief` | Pending evidence |
| 2 | Trunk Links | `show interfaces trunk` | Pending evidence |
| 3 | Inter-VLAN Routing | Ping between VLANs | Pending evidence |
| 4 | HSRP Redundancy | `show standby brief` and failover test | Pending evidence |
| 5 | DHCP Services | Check dynamically assigned IP addresses | Pending evidence |
| 6 | DNS Services | Domain name resolution test | Pending evidence |
| 7 | NAT/PAT | `show ip nat translations` | Pending evidence |
| 8 | ACL Security | Connectivity tests and ACL counters | Pending evidence |
| 9 | Web Service | Access web server using HTTP | Pending evidence |

## 3. Verification Evidence

Screenshots, command outputs, and test observations will be stored in the `evidence/` directory.

## 4. Troubleshooting

Issues encountered during implementation and their corresponding solutions are documented in the `troubleshooting/` directory.

## 5. Conclusion

The final verification results will establish whether the implemented network meets its functional, availability, and security requirements.
