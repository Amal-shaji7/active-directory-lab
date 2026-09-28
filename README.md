# Active Directory Lab — Identity, Access & Network Fundamentals

A hands-on lab built to understand Active Directory from the ground up: Domain Services, Identity Lifecycle, Access Control, Group Policy, and how it all depends on correct network and DNS configuration underneath. AD sits at the center of how most organizations manage identity, access, and endpoints, making it genuinely useful ground for IT Support, IAM, SOC, and broader security roles alike. Along with working with a ticketing system, which would set realistic support scenarios to practice applying that knowledge in the way it is used on a daily basis.

This isn't a checklist of features clicked through in isolation; every piece here was built by hitting a real, often unplanned problem and diagnosing it.

---

## Environment

| Component | Role | Details |
|---|---|---|
| Windows Server 2022 | Domain Controller | AD DS, DNS, static IP 192.168.1.10 |
| OPNsense | Firewall / Gateway | LAN 192.168.1.1, WAN internet-facing |
| Windows 10 Pro | Client (Desktop1) | Domain-joined, RSAT installed, IP 192.168.1.100 |
| Windows 10 Pro | Client (Desktop2) | Domain-joined, IP 192.168.1.101 |
| Spiceworks Cloud Help Desk | Ticketing system | Full incident/request lifecycle tracking |

**Domain:** `homelab.loc`

---

## What's in this repo

| Folder | Covers |
|---|---|
| [`01-environment-setup`](01-environmental-setup/README.md) | VM build, networking, hypervisor configuration |
| [`02-active-directory`](02-active-directory/README.md) | Domain setup, OU design, users, groups |
| [`03-least-privilege-delegation`](03-least-privilege-delegation/README.md) | Delegated admin rights, share/printer permission tiers |
| [`04-group-policy`](./04-group-policy) | GPO-based restrictions and software deployment |
| [`05-file-shares`](./05-file-shares) | Departmental share setup and NTFS/share permissions |
| [`06-printer-deployment`](./06-printer-deployment) | Centralized printer setup and access control |
| [`07-remote-access-tools`](./07-remote-access-tools) | RDP, Remote Registry, Remote Assistance |
| [`08-troubleshooting-scenarios.md`](./08-troubleshooting-scenarios.md) | Full incident writeups, linking back to relevant folders |
| [`09-ticketing-system`](./09-ticketing-system) | Full ticket lifecycle tracking for every scenario above |

---

## Core concepts covered


| Area | Covers |
|---|---|
| **Active Directory Domain Services** | Forest/domain setup, OU design, security groups |
| **Identity Lifecycle Management** | Provisioning, deprovisioning, account expiration, lockouts |
| **Least-Privilege Access Control** | Scoped delegation, tiered file/printer permissions |
| **Group Policy** | Restriction policies, software deployment, troubleshooting |
| **DNS** | Domain resolution, conditional forwarding, dependency on network topology |
| **Network Fundamentals** | Firewall/gateway configuration, routing, static IP management |
| **Remote Administration** | RDP, Remote Registry, Remote Assistance, and the distinct permission model each requires |
| **Incident & Change Tracking** | Full ticket lifecycle from report to resolution |
