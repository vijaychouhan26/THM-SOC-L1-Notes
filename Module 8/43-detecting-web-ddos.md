# Room — Detecting Web DDoS

**Room:** https://tryhackme.com/room/detectingwebddos

## What This Room Covers

Detecting Web DDoS is part of the SOC Level 1 Web Security Monitoring module. It focuses on this module teaches defenders to interpret HTTP and server-side evidence to identify attempted web exploitation, malicious uploads, web shells and denial-of-service activity.

---

## What Is DDoS?

Distributed Denial of Service attempts to overwhelm a target service's network or application resources. SOC and operations teams correlate network behavior with availability and latency.

## Main Categories

| Layer | Typical Pattern | Useful Telemetry |
|---|---|---|
| L3 / L4 | Floods of IP, UDP or TCP traffic | Flow, firewall, network counters |
| L7 | High request volume to expensive web endpoints | Web access, WAF, CDN, application APM |
| Connection exhaustion | Large volume of incomplete or sustained connections | SYN/backlog metrics and server state |

## Detection Signals

- Requests per second far above the historical baseline
- Many source IPs requesting a single endpoint
- Burst of connection attempts or 429/503 responses
- Increase in origin latency and resource saturation
- Significant CDN/WAF challenge or block rates
- User-reported availability incidents

## Example Investigation Table

| Metric | Baseline | During Event |
|---|---|---|
| Requests per second | Record expected range | Record observed spike |
| HTTP 5xx rate | Record normal level | Record actual errors |
| Unique client IPs | Record normal distribution | Check concentration/spread |
| Average response latency | Record typical response | Check service degradation |

## Practical Investigation

1. Establish the start time and which service endpoints suffered.
2. Query volume by minute and URL path.
3. Compare IP, ASN, region and user-agent distribution.
4. Check cache hit rates and upstream errors where available.
5. Confirm actual service impact with operations metrics.
6. Coordinate mitigation (CDN/WAF/rate limiting) under approved procedures.
7. Re-evaluate whether normal users remain affected.

## False Positives

Popular launches, flash sales, bot crawlers and authorized load tests can create high traffic. High request volume is evidence of abnormal demand, not automatically an attack.

## My Takeaway

A DDoS verdict combines unusual demand **and** service impact/context. Operational coordination is essential because blocking can harm legitimate users.
