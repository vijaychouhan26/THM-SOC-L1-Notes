# Room — Splunk: The Basics

**Room:** https://tryhackme.com/room/splunkbasics

## What is Splunk?

Splunk is a widely used enterprise SIEM that ingests log data and makes it searchable using SPL (Search Processing Language).

## Interface Components

| Component | Purpose |
|---|---|
| Search Bar | Write SPL queries |
| Time Range Picker | Filter events by time |
| Events Panel | View raw results |
| Statistics | View aggregated results |
| Visualization | Build charts and graphs |
| Sourcetype | Identify log source category |
| Index | Identify where data is stored |

## SPL Basics

SPL is Splunk's query language.

```spl
index=* "192.168.1.100"
```

Filter failed Windows logons:

```spl
index=* sourcetype=WinEventLog EventCode=4625
```

Count events by user:

```spl
index=* sourcetype=WinEventLog EventCode=4625
| stats count by user
```

## Common SPL Commands

| Command | Purpose |
|---|---|
| `stats count by X` | Count events grouped by X |
| `table field1 field2` | Display selected fields |
| `sort -count` | Sort results descending |
| `rex` | Extract values with regex |
| `dedup` | Remove duplicate values |
| `where` | Filter by condition |
| `timechart` | Chart events over time |

## Common Investigation Searches

### Failed Logins

```spl
index=* EventCode=4625
| stats count by src_ip, user
| where count > 5
| sort -count
```

### Successful Login After Failures

```spl
index=* EventCode=4625 OR EventCode=4624
| stats count by user, EventCode
```

### Suspicious Process Execution

```spl
index=* sourcetype=WinEventLog EventCode=4688
| table _time, user, process_name, parent_process
```

## Key Terms

| Term | Definition |
|---|---|
| SPL | Search Processing Language |
| Index | Storage bucket for logs |
| Sourcetype | Log source/format category |
| Field | Attribute extracted from an event |
| Pivot | Building searches from extracted fields |
| Saved Search | Stored SPL query that can run automatically |

## My Takeaway

SPL is what makes Splunk powerful for investigation. Starting with simple searches and progressively using commands such as `stats`, `table`, and `sort` builds the query patterns needed for faster SOC investigations.
