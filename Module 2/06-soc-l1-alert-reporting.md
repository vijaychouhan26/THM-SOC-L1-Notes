# Room — SOC L1 Alert Reporting

## What This Room Covers
What happens after triage — how to document findings, escalate to L2, and communicate during incidents.

---

**Room:** https://tryhackme.com/room/socl1alertreporting

---

## Three Core Concepts

| Concept | What It Means |
|---------|--------------|
| **Alert Reporting** | Formally documenting your findings before closing or escalating |
| **Alert Escalation** | Passing a confirmed threat to L2 for deeper investigation |
| **Communication** | Coordinating with IT, HR, or management during an incident |

---

## The Five Ws — Report Framework

| W | Question |
|---|----------|
| **Who** | User, process, or account involved |
| **What** | Exact action or event sequence |
| **When** | Timestamps |
| **Where** | Host, IP, URL |
| **Why** | Your verdict and reasoning |

---

## When to Escalate to L2

- Alert indicates a major cyberattack
- Remediation required (malware removal, isolation, password reset)
- Communication with external parties needed
- You don't fully understand the alert

---

## Communication Scenarios

| Situation | Action |
|-----------|--------|
| L2 unavailable during critical alert | Call L2 → L3 → Manager |
| Compromised account — need to verify with user | Don't use Teams/email — call them |
| Sudden flood of critical alerts | Prioritize + inform L2 immediately |
| Missed attack discovered days later | Contact L2 immediately |
| SIEM logs broken | Investigate what you can, report issue to L2 |

---

## Key Terms

| Term | Definition |
|------|------------|
| SPF | Sender Policy Framework — verifies sending server is authorized for the domain |
| DKIM | DomainKeys Identified Mail — verifies email was cryptographically signed by domain |
| Escalation | Reassigning alert to L2 with a documented report |
| Webshell | Malicious script uploaded to a web server giving attacker remote access |
| AD Recon | Active Directory reconnaissance — mapping users, groups, DCs after gaining access |

---

## My Takeaway
Triage is only half the job. A well-written Five Ws report is what turns your investigation into something the whole team can act on. Escalation and communication are what prevent threats from going undetected or uncontained.

---

*Part of my THM SOC Level 1 Notes*
*GitHub: https://github.com/vijaychouhan26/THM-SOC-L1-Notes*
*TryHackMe: https://tryhackme.com/p/Vijaychouhan*
