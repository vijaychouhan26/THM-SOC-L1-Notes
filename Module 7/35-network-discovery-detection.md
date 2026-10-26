# Room — Network Discovery Detection

**Room:** https://tryhackme.com/room/networkdiscoverydetection

## What This Room Covers

Network Discovery Detection is part of the SOC Level 1 Network Security Monitoring module. It focuses on this module covers practical defensive monitoring: network visibility, discovery, exfiltration, interception and IDS/Snort-based detection.

---

## What Is Network Discovery?

Adversaries frequently enumerate hosts, services and network configuration before further action. Discovery may appear in firewall logs, Zeek conn logs, packet captures and SIEM summaries.

## Common Scan Patterns

| Pattern | Typical Evidence |
|---|---|
| Vertical scan | One source probing many ports on one destination |
| Horizontal scan | One source probing the same port across many hosts |
| Host sweep | ICMP echo requests or connections across an address range |
| Service enumeration | Repeated connections to identify applications |
| DNS enumeration | Numerous queries for candidate hostnames |

## TCP Evidence

- `SYN`: attempt to establish a TCP connection.
- `SYN, ACK`: destination appears to accept connection.
- `RST`: often indicates rejected/closed connection or abort.
- A sequence of ports and rapid failures can be consistent with scanning.

## Example SIEM Investigation (Illustrative SPL)

```spl
index=firewall action=allowed
| stats dc(dest_port) as unique_ports count by src_ip dest_ip
| where unique_ports > 20
| sort -unique_ports
```

**Note:** Threshold `20` is merely an investigation example; calibrate to the environment. Field names depend on log ingestion.

## Workflow

1. Identify the scanning source, targets, ports and time window.
2. Count unique destinations and ports.
3. Check allow/deny results and session completion.
4. Verify whether a vulnerability scan, asset inventory or uptime monitor was authorized.
5. Look for follow-on authentication attempts or exploitation.
6. Escalate unexplained reconnaissance against sensitive assets.

## Common False Positives

- Approved security scanners
- Asset discovery and patch management
- Load balancer health checks
- Monitoring and troubleshooting

## My Takeaway

Scan detection is a pattern-analysis task. The source's purpose and authorization matter as much as the number of ports it touched.
