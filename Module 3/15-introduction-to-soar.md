# Room — Introduction to SOAR

**Room:** https://tryhackme.com/room/soar

**Detailed walkthrough:** https://medium.com/@chouhanvj62/tryhackme-introduction-to-soar-full-walkthrough-b8d96f0f6f7f

## What is SOAR?

SOAR stands for **Security Orchestration, Automation and Response**. It helps SOC teams reduce repetitive manual work, connect security tools, enrich alerts with additional context, and automate parts of incident response.

## Why SOC Teams Use SOAR

Traditional SOC workflows can suffer from:

- Alert fatigue
- Repetitive manual processes
- Too many disconnected security tools
- Slow investigation and response
- Communication and coordination overhead

SOAR addresses these problems by orchestrating tools and automating repeatable response workflows.

## Core SOAR Concepts

| Concept | Purpose |
|---|---|
| **Orchestration** | Connect security products and coordinate actions across them |
| **Automation** | Execute repeatable actions without manual intervention |
| **Response** | Carry out predefined incident-response actions |
| **Playbook** | Structured workflow that defines what happens when an event occurs |
| **Enrichment** | Add context to an alert using external or internal data sources |

## SOAR Playbooks

A playbook defines a repeatable workflow for handling an alert or incident. A typical workflow can look like:

```text
Alert received
      ↓
Extract indicators
      ↓
Enrich indicators with threat intelligence
      ↓
Evaluate the result
      ↓
Take response action
      ↓
Document / escalate / close
```

The important idea is consistency: the same type of alert can follow the same validated workflow instead of requiring an analyst to repeat every step manually.

## Threat Intelligence Enrichment

SOAR can integrate with threat intelligence platforms to automatically investigate indicators such as:

- IP addresses
- Domains
- File hashes
- URLs

The enrichment result can then be used as input for the next step of a playbook, such as escalating a confirmed malicious indicator or continuing the investigation when the result is inconclusive.

## SOAR and Other SOC Tools

| Tool | Role |
|---|---|
| SIEM | Collects and correlates logs and generates alerts |
| EDR | Provides endpoint telemetry and response capabilities |
| Threat Intelligence Platform | Provides context about indicators and threats |
| SOAR | Connects these systems and automates repeatable workflows |

## L1 Analyst Perspective

SOAR does not replace analyst judgment. It reduces repetitive work so analysts can spend more time on investigation and decision-making. Automated actions should be carefully designed and validated because an incorrect automated response can have a wider impact than a manual mistake.

## Key Terms

| Term | Definition |
|---|---|
| SOAR | Security Orchestration, Automation and Response |
| Orchestration | Coordinating actions between security tools |
| Automation | Executing repeatable actions automatically |
| Playbook | Structured workflow for handling an event or incident |
| Enrichment | Adding context to an indicator or alert |

## My Takeaway

SOAR is the automation layer of a modern SOC. The value is not simply making actions automatic; it is building reliable workflows that connect detection, enrichment, investigation, response, and documentation into a repeatable process.

---

*Part of my THM SOC Level 1 Notes*  
*Detailed walkthrough: [Medium — TryHackMe: Introduction to SOAR](https://medium.com/@chouhanvj62/tryhackme-introduction-to-soar-full-walkthrough-b8d96f0f6f7f)*
