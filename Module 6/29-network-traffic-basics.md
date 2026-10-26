# Room — Network Traffic Basics

**Path:** [TryHackMe SOC Level 1](https://tryhackme.com/path/outline/blueteam)  
**Module:** 6 — Network Traffic Analysis  
**Status:** Study reference for a module reported complete; individual challenge evidence not independently verified.

## Objective

Traffic visibility, packet captures and flow metadata.

## Core Concepts and Practical Workflow

1. Understand PCAP versus NetFlow, TCP/IP layers, five-tuple, capture points, DNS/HTTP/TLS and normal baselines.

## SOC L1 Investigation Notes

Collect time range, endpoints, ports, protocols, direction and byte counts before assigning a verdict.

### Investigation checklist

- [ ] Identify affected asset, user and time window.
- [ ] Preserve the original log, PCAP, email or lab artifact.
- [ ] Record the exact query/filter/command and evidence location.
- [ ] Consider legitimate explanations and corroborating telemetry.
- [ ] Classify the event, state confidence and recommend next action.

## Cautions and Limitations

Encrypted traffic may expose metadata but not application payload.

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
