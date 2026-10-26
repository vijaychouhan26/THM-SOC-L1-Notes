# Room — Wireshark: The Basics

**Path:** [TryHackMe SOC Level 1](https://tryhackme.com/path/outline/blueteam)  
**Module:** 6 — Network Traffic Analysis  
**Status:** Study reference for a module reported complete; individual challenge evidence not independently verified.

## Objective

Wireshark interface and capture/display filters.

## Core Concepts and Practical Workflow

1. Use display filters: ip.addr == 192.0.2.10.
2. tcp.port == 443.
3. dns.
4. http.
5. inspect packet details and conversations.

## SOC L1 Investigation Notes

Record capture interface, time zone, display filter and packet number when citing evidence.

### Investigation checklist

- [ ] Identify affected asset, user and time window.
- [ ] Preserve the original log, PCAP, email or lab artifact.
- [ ] Record the exact query/filter/command and evidence location.
- [ ] Consider legitimate explanations and corroborating telemetry.
- [ ] Classify the event, state confidence and recommend next action.

## Cautions and Limitations

Capture filters use BPF syntax; display filters use Wireshark syntax.

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
