# Room — SOC Metrics and Objectives

**Room:** https://tryhackme.com/room/socmetricsobjectives

---

## Why Metrics Matter

SOC performance is measured just like any other department. Metrics help identify if analysts are too slow, too overwhelmed, or missing real threats. Ignoring them leads to burnout and undetected breaches.

---

## Core Metrics

| Metric | Full Name | What It Measures |
|--------|-----------|-----------------|
| **MTTD** | Mean Time to Detect | Time between attack occurring and alert firing |
| **MTTA** | Mean Time to Acknowledge | Time between alert firing and analyst picking it up |
| **MTTR** | Mean Time to Respond | Time between alert firing and full resolution |
| **FPR** | False Positive Rate | % of alerts that turn out to be non-threats |

**Quick formula:**
- MTTR = MTTA + investigation time + remediation time
- FPR = (False Positives ÷ Total Alerts) × 100

**Example from the room:**
- Alert fired 12 min after attack → MTTD = 12
- Analyst acknowledged 10 min later → MTTA = 10
- Escalated after 6 min, L2 took 35 min to remediate → MTTR = 10 + 6 + 35 = **51 min**

---

## Alert Count — What's Normal?

- **Too many alerts** → analyst fatigue, real threats get missed in the noise
- **Zero alerts for a week** → not good either — may mean SIEM is broken or has no visibility
- **FPR above 80%** → critical threshold — too much noise, analyst trust in alerts collapses

---

## SLA — Service Level Agreement

An SLA defines the maximum time allowed to acknowledge and respond to alerts by severity. Example:

| Severity | Max Acknowledge Time |
|----------|---------------------|
| Critical | 15 minutes |
| High | 1 hour |
| Medium | 4 hours |
| Low | 24 hours |

If your team works **8/5** (business hours only) and a critical alert fires Saturday — SLA clock starts Monday. That's a major risk for 24/7 threats.

---

## How to Improve Metrics as L1

- Reduce MTTA → pick up alerts faster, don't let queue pile up
- Reduce FPR → tune detection rules, document false positives properly
- Reduce MTTR → write better reports so L2 wastes no time understanding context
- All SOC roles (L1, L2, L3, engineers) need to work together on improvement

---

## Key Terms

| Term | Definition |
|------|------------|
| SLA | Service Level Agreement — max time to respond to an alert by severity |
| MTTD | Mean Time to Detect — how long it takes the SIEM to catch an attack |
| MTTA | Mean Time to Acknowledge — how fast L1 picks up an alert |
| MTTR | Mean Time to Respond — total time from alert to resolution |
| FPR | False Positive Rate — % of alerts that are not real threats |
| Alert Fatigue | Analyst burnout from too many false positives, leading to missed real threats |

---

## My Takeaway
Metrics are what make a SOC accountable. As an L1 analyst, I directly influence MTTA (how fast I pick up alerts) and FPR (how accurately I classify them). Writing good reports reduces MTTR. Every individual action contributes to team-wide performance.

---

*GitHub: https://github.com/vijaychouhan26/THM-SOC-L1-Notes*
*TryHackMe: https://tryhackme.com/p/Vijaychouhan*
*LinkedIn: https://www.linkedin.com/in/vijay-chouhan-1130632b7/*
