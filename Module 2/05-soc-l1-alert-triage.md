# Room — SOC L1 Alert Triage

## What This Room Covers
How a Tier 1 SOC analyst systematically triages incoming alerts — from the moment an alert fires to the decision of escalating or closing it.

---

## The Alert Triage Process

When an alert comes in, a L1 analyst follows this systematic approach:

```
Alert Received
      ↓
Is it a Real Threat or False Positive?
      ↓
Classify the Alert (TP / FP / TN / FN)
      ↓
Check IOCs (IP, domain, hash, URL, email)
      ↓
Verify IOCs using VirusTotal / Threat Intel / SIEM logs
      ↓
Determine Severity
      ↓
Escalate to Tier 2 (if real) OR Close the Alert (if false positive)
```

---

## Alert Classification

Every alert must be classified into one of four categories:

| Classification | What It Means | Action |
|---------------|---------------|--------|
| **True Positive (TP)** | Alert fired AND it's a real threat | Escalate to Tier 2 |
| **False Positive (FP)** | Alert fired BUT it's not a real threat | Close with notes |
| **True Negative (TN)** | No alert AND no real threat | Nothing to do |
| **False Negative (FN)** | No alert BUT a real threat existed | Detection gap — needs tuning |

> False Negatives are the most dangerous — the system missed a real attack. They are usually discovered during post-incident reviews.

---

## IOCs — What to Look For

When triaging an alert, these are the Indicators of Compromise to extract and investigate:

| IOC Type | Example |
|----------|---------|
| **IP Address** | Suspicious source IP connecting to internal systems |
| **Domain** | Malicious domain in DNS logs or proxy logs |
| **File Hash** | MD5/SHA256 of a suspicious file or executable |
| **URL** | Link in a phishing email or found in web proxy logs |
| **Email Address** | Sender address in a phishing attempt |

---

## How to Verify IOCs

Once IOCs are extracted, verify them using:

| Tool / Source | What It Helps With |
|--------------|-------------------|
| **VirusTotal** | Check if a file hash, IP, domain, or URL is flagged as malicious |
| **Threat Intel Feeds** | Cross-reference IOCs against known threat actor infrastructure |
| **SIEM Logs** | Check if the same IOC appeared elsewhere in the environment |
| **Previous Tickets** | See if this IOC was investigated before — context from past incidents |

---

## Key Terms

| Term | Definition |
|------|------------|
| Triage | Systematic evaluation of an alert to determine if it's real and how severe |
| IOC | Indicator of Compromise — evidence that a system may have been attacked |
| True Positive | A real threat that correctly triggered an alert |
| False Positive | A benign event that incorrectly triggered an alert |
| Threat Intel | Information about known attacker tactics, tools, and infrastructure |
| Escalation | Passing a confirmed alert to Tier 2 with context and findings |

---

## My Takeaway
Triage is not guesswork — it's a repeatable process. Every alert gets the same systematic treatment: classify, extract IOCs, verify, decide. The goal is to be fast AND accurate. A missed True Positive means a real attack goes undetected. Too many False Positives and analysts get overwhelmed with noise.
