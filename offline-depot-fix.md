# VCF 9.0.2 Offline Depot Fix - Cloud Builder Notes

## Problem

During VMware Cloud Foundation 9.0.2 bring-up, Cloud Builder failed to properly validate and consume the offline depot metadata.

Observed issues included:

- `Could not retrieve supported releases`
- `No release data found for version 9.0.2.0`
- `Component version null is not compatible with release version 9.0.2.0`
- UI / depot communication errors
- Redirects and access issues when testing depot paths

---

## Root Cause

The issue was related to how the offline depot metadata was being served through nginx on the Cloud Builder appliance.

By default, nginx redirected `/depot` requests to `/ui`, which prevented Cloud Builder from properly consuming the metadata and manifest files required for validation.

There were also permission and path issues that prevented proper access to the metadata files.

---

## Key Fixes Applied

### 1. Offline metadata staging path
Offline metadata had to be unzipped into the following location:

```bash
/opt/vmware/vcf/offline-depot/
