# Room — Introduction to SIEM

**Room:** https://tryhackme.com/room/introtosiem

## What is a SIEM?

SIEM (Security Information and Event Management) is a central SOC platform that collects logs across an environment, correlates events, and generates alerts when suspicious patterns are detected.

### Two Core Functions

- **SIM — Security Information Management:** Long-term log storage and compliance.
- **SEM — Security Event Management:** Real-time monitoring and alerting.

## How SIEM Works

```text
Log Sources → Ingestion → Normalization → Correlation → Alert → Analyst
```

Common log sources include firewalls, endpoints, web servers, applications, identity providers, cloud platforms, EDR, and antivirus tools.

**Normalization** converts different log formats into a common structure. **Correlation rules** apply detection logic across events and trigger alerts when conditions are met.

## What an L1 Analyst Does in a SIEM

- Monitor the alert dashboard
- Search logs to investigate alerts
- Correlate events across multiple sources
- Extract IOCs such as IPs, hashes, and domains
- Document findings and close or escalate alerts

## SIEM vs EDR

| | SIEM | EDR |
|---|---|---|
| Scope | Entire environment | Endpoints |
| Data | Logs from many sources | Deep endpoint telemetry |
| Detection | Correlation rules | Behavioral + IOC |
| Response | Primarily alerting | Host isolation, process termination, etc. |
| Examples | Splunk, Elastic, QRadar | CrowdStrike, SentinelOne, Defender |

## Key Terms

| Term | Definition |
|---|---|
| SIEM | Centralized log collection and security alerting |
| Log Ingestion | Collecting and importing logs |
| Normalization | Standardizing log formats |
| Correlation Rule | Detection logic that triggers an alert |
| Dashboard | Interface showing alerts and security status |
| Query | Search command used to find events |

## My Takeaway

The SIEM is the starting point for many SOC investigations. Understanding how logs are ingested, normalized, correlated, and searched helps an analyst understand why alerts fire and how to investigate them effectively.
