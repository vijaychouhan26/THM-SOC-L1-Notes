# Room — IDS Fundamentals

**Room:** https://tryhackme.com/room/idsfundamentals

## What This Room Covers

IDS Fundamentals is part of the SOC Level 1 Network Security Monitoring module. It focuses on this module covers practical defensive monitoring: network visibility, discovery, exfiltration, interception and IDS/Snort-based detection.

---

## What Is an IDS?

An Intrusion Detection System analyzes network or host activity for indicators of malicious behavior and produces alerts. **An IDS detects; an IPS can block** when configured in a prevention role.

## IDS Categories

| Type | Monitors |
|---|---|
| NIDS | Packets and traffic observed on a network segment |
| HIDS | Host-level logs, files and system behavior |
| Signature-based | Defined patterns linked to known activity |
| Anomaly-based | Activity deviating from an expected baseline |

## Signature vs Anomaly Detection

- **Signature-based:** Good at recognized patterns, but may miss novel behavior.
- **Anomaly-based:** Can reveal unusual activity, but may create more noise.
- Both approaches need tuning, asset context and validation.

## Alert Anatomy

| Field | Why It Matters |
|---|---|
| Timestamp | Correlate evidence in a common time zone |
| Signature / rule ID | Understand what fired |
| Source / destination | Identify assets and direction |
| Protocol / port | Explain the communication |
| Severity / classification | Prioritize triage, not automatic verdict |
| Packet excerpt | Validate trigger condition when available |

## SOC Alert Validation

1. Read the alert's rule and triggering fields.
2. Establish whether traffic reached its intended destination.
3. Inspect PCAP or network log evidence.
4. Verify affected asset's sensitivity and expected services.
5. Correlate endpoint logs and previous alerts.
6. Classify TP, FP or inconclusive and document rationale.

## False Positives and False Negatives

A **false positive** alert triggers on benign behavior; a **false negative** represents malicious behavior the detector misses. Tuning aims to improve fidelity without losing important detections.

## My Takeaway

An IDS signature is an investigation lead. My responsibility is to determine whether the event is relevant, corroborated and worth escalating.
