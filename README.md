# Enterprise Security Sandbox & Forensic Lab

## Executive Summary
This production-grade, isolated hybrid virtual network sandbox is engineered for malware triage, perimeter defense validation, and continuous telemetry collection. By enforcing strict network segmentation and host-level hardening, the architecture mirrors enterprise defensive frameworks to safely analyze volatile samples without risk to the host infrastructure or local LAN.

## Architectural Topology
The lab is built using VMware Workstation, leveraging a multi-zone configuration isolated on a custom host-only network (`VMnet2`). 

* **Perimeter Gateway / NGFW:** OPNsense 26.1.6 (Manages routing, NAT, and restrictive egress ACLs).
* **Management Node:** Windows 10 Workstation (Secure administrative endpoint).
* **Infrastructure Target:** Headless Debian 13 "Trixie" (System auditing and localized network infrastructure).
* **Malware Analysis Cell:** REMnux v7 (Isolated reverse-engineering and static/dynamic triage workspace).

---

## Phase 1: Perimeter & Baseline Infrastructure
### Network Configuration & State Persistence
To eliminate unauthorized dynamic identities, DHCP was explicitly disabled on the internal network segment (`10.0.0.0/24`). The infrastructure target (Debian 13) was provisioned with a hardcoded static network identity.

**Engineering Highlights:**
* Resolved standard Debian `NETINST` software dependency constraint by manually modifying the package management subsystem (`/etc/apt/sources.list`) to redirect from local media loops to live upstream mirrors.
* Hardened network state persistence by mapping interfaces directly within the core network configuration file.
