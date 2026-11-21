# Network Troubleshooting Records

This document records network issues encountered during the implementation of the Enterprise Network Design project and the solutions applied.

## Issue 01: ICMP Connectivity Blocked by Extended ACL

### Problem

Ping communication from PC6 in VLAN 30 (IT) to the Ubuntu Server (`192.168.50.10`) was unsuccessful.

### Investigation

Router ACL inspection showed that ICMP traffic was being filtered by the configured extended access control lists.

Extended ACLs are stateless. Therefore, permitting an ICMP Echo Request does not automatically permit the corresponding ICMP Echo Reply.

### Root Cause

The relevant ACL did not permit the required ICMP Echo Reply traffic.

### Solution

An ICMP Echo Reply permit rule was added to the relevant ACL to allow the required return traffic.

### Verification

- An ICMP Echo Reply permit rule was added to the relevant ACL.
- The user confirmed that the connectivity issue was resolved after the ACL modification.

### Result

RESOLVED.

### Lesson Learned

When troubleshooting connectivity through extended ACLs, both request and return traffic must be considered. ACL rules should permit only the required traffic between intended source and destination networks.
