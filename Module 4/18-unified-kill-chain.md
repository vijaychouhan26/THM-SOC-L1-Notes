# Room — Unified Kill Chain

**Room:** https://tryhackme.com/room/unifiedkillchain

## What Is the Unified Kill Chain?

The Unified Kill Chain (UKC) was developed by Paul Pols in 2017 as an evolution of the Cyber Kill Chain and MITRE ATT&CK. It combines both frameworks into a more comprehensive model covering 18 attack phases across three macro-stages.

## Three Macro-Stages

### Stage 1 — IN (Initial Foothold)
Getting into the target environment.
- Reconnaissance, Weaponization, Social Engineering, Exploitation, Persistence, Defence Evasion, Command & Control

### Stage 2 — THROUGH (Network Propagation)
Moving through the network after getting in.
- Pivoting, Discovery, Privilege Escalation, Execution, Credential Access, Lateral Movement

### Stage 3 — OUT (Action on Objectives)
Achieving the final goal.
- Collection, Exfiltration, Impact, Objectives

## Unified Kill Chain vs Cyber Kill Chain

| | Cyber Kill Chain | Unified Kill Chain |
|---|---|---|
| Stages | 7 | 18 |
| Scope | Linear — one path | Non-linear — multiple paths |
| Integration | Standalone | Combines ATT&CK + Kill Chain |
| Focus | External attacks | Full attack lifecycle including insider threat |

## Key Terms

| Term | Definition |
|---|---|
| UKC | Unified Kill Chain — 18-phase attack model |
| Pivoting | Using a compromised host as a launchpad to reach other systems |
| Privilege Escalation | Gaining higher permissions than initially obtained |
| Lateral Movement | Moving between systems within the network |
| Exfiltration | Transferring stolen data out of the target environment |

## My Takeaway

The UKC provides a more detailed view of an attack and better reflects that real intrusions can involve repeated or non-linear activity.
