# Room — Network Security Essentials

**Path:** [TryHackMe SOC Level 1](https://tryhackme.com/path/outline/blueteam)  
**Module:** 7 — Network Security Monitoring  
**Status:** Study reference for a module reported complete; individual challenge evidence not independently verified.

## Objective

Monitoring perimeter and internal traffic.

## Core Concepts and Practical Workflow

1. Distinguish IDS/IPS, NIDS/HIDS, segmentation, firewall logs and sensor placement.
2. establish expected traffic patterns.

## SOC L1 Investigation Notes

Triage alerts with source, destination, protocol, signature, time and asset criticality.

### Investigation checklist

- [ ] Identify affected asset, user and time window.
- [ ] Preserve the original log, PCAP, email or lab artifact.
- [ ] Record the exact query/filter/command and evidence location.
- [ ] Consider legitimate explanations and corroborating telemetry.
- [ ] Classify the event, state confidence and recommend next action.

## Cautions and Limitations

Detection signatures require context and tuning.

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
