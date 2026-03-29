# SOC Enterprise Infrastructure Lab — Phase 1

> **SecurinetsENIT** | Building Enterprise Infrastructure in a Virtualized Environment

## Overview

This repository documents the implementation of a secure, fully operational enterprise network infrastructure built inside a virtualized environment using Oracle VirtualBox. The project is **Phase 1** of a broader SOC (Security Operations Center) lab series, prepared by **SecurinetsENIT**.

The goal is to design and deploy an **Active Directory (AD)** domain, configure critical Windows services (DNS, LDAP, Kerberos), implement granular access controls through **Group Policy Objects (GPOs)** and delegation mechanisms, and reinforce network security by integrating an **IDS/IPS-based firewall** using OPNsense with Suricata.

---

## Project Team

| Name | Role |
|---|---|
| **Mouhamed Oussama Chelly** | Team Leader |
| Amir Khammar | Team Member |
| Rayen Mabsout | Team Member |
| Karim Dami | Team Member |
| Montaha Jmai | Team Member |
| Mariem Idoudi | Team Member |

---

## Network Architecture

```
         [WAN / Internet Simulation]
                    |
         [OPNsense Firewall — chelly3]
          OPNsense 25.7 (amd64)
          WAN (em0): 10.0.2.15/24  (DHCP - VirtualBox NAT)
          LAN (em1): 192.168.1.1/24
                    |
        [Internal LAN: 192.168.1.0/24]
         ____________|_____________
        |                          |
 [Domain Controller]         [Workstation]
  Windows Server 2022         Windows 10
  AD DS, DNS, LDAP,           Domain-joined client
  Kerberos KDC, GPO           for testing user access,
                              GPO enforcement
```

---

## Virtual Machines

| VM Name | Role | Operating System | Key Services |
|---|---|---|---|
| windows_server_2022 | Domain Controller | Windows Server 2022 | AD DS, DNS, LDAP, Kerberos KDC, GPO |
| Workstation-Win10 | Client Endpoint | Windows 10 | Domain-joined, GPO target |
| chelly3 | Firewall / IDS | OPNsense 25.7 (amd64) | Routing, NAT, Firewall, Suricata IDS/IPS |

**Hypervisor**: Oracle VirtualBox
**Domain**: `securinetsenit.local`

---

## Phases

| Phase | Title | Status |
|---|---|---|
| [Phase 1](phase1-setup/) | Setup and Connectivity | ✅ Completed |
| [Phase 2](phase2-active-directory/) | Core Active Directory & Services | ✅ Completed |
| [Phase 3](phase3-firewall-ids/) | Perimeter Defense & Hardening | ✅ Completed |
| Phase 4 | Advanced AD & Kerberos (ADCS, SPNs) | 🔜 Upcoming |
| Phase 5 | Attack Testing & Final Deliverables | 🔜 Upcoming |

---

## Repository Structure

```
├── phase1-setup/                   VM setup, OS install, network connectivity
│   ├── README.md
│   └── screenshots/
├── phase2-active-directory/        AD, OU structure, GPOs, delegation
│   ├── README.md
│   └── screenshots/
├── phase3-firewall-ids/            OPNsense, Suricata IDS/IPS configuration
│   ├── README.md
│   └── screenshots/
└── Specifications_document-2.pdf   Full project specification
```

---

## Key Technologies

- **Active Directory Domain Services (AD DS)** — Windows Server 2022
- **Group Policy Objects (GPOs)** — Security baselines, access control, hardening
- **DNS** — Authoritative DNS served by the Domain Controller
- **Kerberos** — Authentication protocol (KDC on DC)
- **LDAP / LDAPS** — Directory access
- **OPNsense 25.7** — Open-source firewall/router
- **Suricata** — Network IDS/IPS engine (Emerging Threats ruleset)
- **Oracle VirtualBox** — Hypervisor

---

*Prepared by SecurinetsENIT — November 2025*
