# Room — Phishing Emails in Action

**Path:** [TryHackMe SOC Level 1](https://tryhackme.com/path/outline/blueteam)  
**Module:** 5 — Phishing Analysis  
**Status:** Study reference for a module reported complete; individual challenge evidence not independently verified.

## Objective

Recognizing social engineering and examining suspicious messages.

## Core Concepts and Practical Workflow

1. Compare display name with actual address.
2. inspect links without opening them.
3. correlate message context with business process.
4. assess attachments and unusual requests.

## SOC L1 Investigation Notes

Build an evidence table of claimed identity, actual infrastructure, lure, requested action and impact.

### Investigation checklist

- [ ] Identify affected asset, user and time window.
- [ ] Preserve the original log, PCAP, email or lab artifact.
- [ ] Record the exact query/filter/command and evidence location.
- [ ] Consider legitimate explanations and corroborating telemetry.
- [ ] Classify the event, state confidence and recommend next action.

## Cautions and Limitations

A suspicious-looking email is not automatically malicious; document supporting evidence.

## Example Analyst Report Template

| Field | Analyst entry |
|---|---|
| Alert / case ID | _To be completed from lab evidence_ |
| Timestamp and timezone | _Not recorded_ |
| Affected asset / user | _Not recorded_ |
| Observed indicators | _Not recorded_ |
| Evidence and query | _Not recorded_ |
| Assessment | _Pending evidence review_ |
| Next action | _Pending triage_ |

## Key Takeaway

For SOC L1 work, use the topic's telemetry to move from an initial observation to a reproducible, evidence-backed assessment rather than relying on an indicator alone.

> These are original revision notes and investigation prompts, not copied room solutions. No personal screenshots, flags, or lab results have been invented.
