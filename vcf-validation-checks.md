# VCF Bring-Up Validation Checks

## Purpose

This document captures common validation areas to review before and during VMware Cloud Foundation (VCF) bring-up.

These checks help reduce deployment failures and improve Day 0 readiness.

---

## Core Validation Areas

### 1. DNS Resolution
Validate:

- Forward DNS for all ESXi hosts
- Reverse DNS for all ESXi hosts
- vCenter FQDN resolution
- NSX Manager FQDN resolution
- SDDC Manager / Cloud Builder name resolution

Common issue:
- Forward or reverse lookup failures causing bring-up validation errors

---

### 2. NTP Synchronization
Validate:

- ESXi hosts are pointed to the correct NTP source
- Cloud Builder time is synchronized
- vCenter / NSX appliances use consistent time sources

Common issue:
- Time drift causing certificate, trust, or deployment failures

---

### 3. Network Reachability
Validate:

- Management gateway reachability
- ESXi host management vmkernel connectivity
- Required Layer 3 / routed path reachability
- VLAN assignment and trunking
- MTU consistency where required

Common issue:
- Gateway or routed network validation failures during bring-up

---

### 4. ESXi Host Readiness
Validate:

- Correct ESXi version / build
- Hostnames match DNS
- Management IPs assigned correctly
- NIC speed and physical uplink readiness
- Storage devices visible and usable

Common issue:
- Host configuration mismatches or unsupported hardware findings

---

### 5. vSAN Readiness
Validate:

- Eligible cache / capacity devices detected
- Correct disk claim expectations
- Storage visibility across all hosts
- HCL / ESA / Hybrid expectations understood

Common issue:
- Disk role mismatches or unsupported storage configurations

---

### 6. NSX Deployment Readiness
Validate:

- NSX management IP plan
- DNS / NTP reachability for NSX appliances
- Overlay VLAN / transport planning
- Edge uplink planning
- MTU alignment for overlay traffic

Common issue:
- NSX deployment failures tied to transport, MTU, or IP planning issues

---

### 7. Offline Depot / Bundle Validation
Validate:

- Correct depot metadata staging path
- Manifest accessibility
- Certificate trust
- Bundle compatibility
- Release metadata visibility

Common issue:
- Cloud Builder unable to retrieve supported releases or validate bundles

---

## Recommended Pre-Check Mindset

Before running bring-up, validate these first:

1. DNS
2. NTP
3. Gateway reachability
4. Host build / hardware readiness
5. Storage visibility
6. NSX IP / transport readiness
7. Offline depot accessibility (if offline deployment)

---

## Practical Reality

Most VCF bring-up failures are not caused by “VCF being broken.”

They are usually caused by:

- DNS issues
- Time sync issues
- network misconfiguration
- unsupported hardware assumptions
- storage / disk readiness issues
- bad input data in the deployment workbook

---

## Summary

Good bring-up outcomes usually come down to disciplined pre-validation.

The more effort spent validating infrastructure before deployment, the less time is lost during bring-up troubleshooting.
