# Room — Phishing Analysis Fundamentals

**Path:** [TryHackMe SOC Level 1](https://tryhackme.com/path/outline/blueteam)  
**Module:** 5 — Phishing Analysis  
**Status:** Study reference for a module reported complete; individual challenge evidence not independently verified.

## Objective

Email header analysis, sender authentication, URL and attachment triage.

## Core Concepts and Practical Workflow

1. Check From versus Reply-To and Return-Path.
2. inspect Received hops and SPF/DKIM/DMARC results.
3. preserve original .eml.
4. identify urgency, credential-harvesting and spoofing indicators.

## SOC L1 Investigation Notes

Record message-id, sender, recipient, timestamp, URLs and hashes; distinguish suspicious indicators from confirmed compromise.

### Investigation checklist

- [ ] Identify affected asset, user and time window.
- [ ] Preserve the original log, PCAP, email or lab artifact.
- [ ] Record the exact query/filter/command and evidence location.
- [ ] Consider legitimate explanations and corroborating telemetry.
- [ ] Classify the event, state confidence and recommend next action.

## Cautions and Limitations

Do not click live suspicious links or upload sensitive emails to public scanners.

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
