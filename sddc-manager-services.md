# SDDC Manager Core Services - Quick Reference

## Purpose

This document provides a practical reference for key VMware Cloud Foundation (VCF) services involved in bring-up, lifecycle, and operational troubleshooting.

---

## Why This Matters

In many VCF issues, the UI only shows the symptom.

The actual root cause is often tied to a backend service that is:

- stopped
- unhealthy
- timing out
- unable to reach a dependency
- failing due to configuration or trust issues

Understanding the service roles helps speed up troubleshooting.

---

## Core Services

### 1. domainmanager

**Primary role:**  
Handles domain lifecycle orchestration.

### Common responsibilities:
- Management Domain creation
- Workload Domain deployment
- Host commissioning / expansion
- NSX deployment coordination
- vCenter task orchestration

### What to check:
- service health
- domain creation failures
- workload domain workflow failures
- orchestration task breakdowns

### Common log location:
```bash
/var/log/vmware/vcf/domainmanager/
