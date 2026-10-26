# NetworkMiner and Network Forensics

**Track:** TryHackMe SOC Level 1  
**Module:** 6 — Network Traffic Analysis  
**Status:** Study notes; original room-specific evidence pending.

## Objective

Review passive network artifacts and session metadata.

## Key Concepts and Practical Workflow

Inspect Hosts, Sessions, DNS and extracted file metadata; cross-check findings in the PCAP.

## SOC L1 Investigation Steps

1. Identify the alert, affected host, time window and telemetry source.
2. Preserve original logs or captures; record the filter, query and timestamps.
3. Extract relevant IPs, ports, domains, identities, paths and other indicators.
4. Correlate another independent data source where possible.
5. Consider legitimate explanations and document uncertainty.
6. Record classification, confidence, impact and recommended escalation.

## Evidence Worksheet

| Field | Notes |
|---|---|
| Room/lab title | _Verify against completed THM room_ |
| Source log/PCAP | _Add sanitized reference_ |
| Query or display filter | _Record actual command_ |
| Timeline with timezone | _Pending_ |
| Indicators | _Pending_ |
| Verdict and reasoning | _Pending_ |

## Limitations

Handle extracted files and credentials as sensitive evidence.

## My Takeaway

An analyst's conclusion should be reproducible from observed evidence, not based on a suspicious indicator alone.

> Original revision material. No challenge flags, screenshots or personal lab results have been invented.
