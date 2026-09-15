# Room — Elastic Stack: The Basics

**Room:** https://tryhackme.com/room/elasticstackbasics

## What is the Elastic Stack?

The Elastic Stack (ELK) is an open-source log management and SIEM platform. It is widely used in smaller SOCs, home labs, and organizations that prefer open-source tooling.

### ELK Components

- **Elasticsearch** — search and storage engine
- **Logstash** — log ingestion and processing pipeline
- **Kibana** — web UI for searching and visualization
- **Beats** — lightweight endpoint agents that ship logs

## How ELK Works

```text
Endpoints (Beats agents)
    ↓
Logstash (parse, filter, enrich)
    ↓
Elasticsearch (index and store)
    ↓
Kibana (search, visualize, alert)
```

## Kibana — Key Features

| Feature | What It Does |
|---|---|
| Discover | Search and explore raw logs |
| Dashboard | Monitor through visual panels |
| Visualize | Build custom charts |
| Alerts | Create detection rules |
| SIEM App | Security investigation interface |

## KQL — Kibana Query Language

KQL is used in Kibana's search bar.

### Basic Search

```kql
event.code: 4625
```

### AND / OR Conditions

```kql
event.code: 4625 AND source.ip: "192.168.1.100"
```

### Wildcard

```kql
process.name: power*
```

### Range

```kql
event.count > 10
```

## Splunk vs Elastic

| | Splunk | Elastic Stack |
|---|---|---|
| Cost | Enterprise-focused | Open-source option |
| Query language | SPL | KQL / Lucene |
| Job market | Very common in enterprise | Common and growing |
| Setup | Managed/cloud options | Self-hosted or Elastic Cloud |
| Learning curve | Moderate | KQL is comparatively simple |

## Key Terms

| Term | Definition |
|---|---|
| Elasticsearch | Search engine that stores and indexes logs |
| Logstash | Pipeline that ingests, parses, and enriches logs |
| Kibana | Web UI for Elasticsearch |
| Beats | Lightweight log shippers |
| KQL | Kibana Query Language |
| Index Pattern | Defines which Elasticsearch indices Kibana searches |

## My Takeaway

Splunk and Elastic solve similar SOC problems with different tooling and query syntax. Learning both makes the investigation workflow more transferable across different SOC environments.
