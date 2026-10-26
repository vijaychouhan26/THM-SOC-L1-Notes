# Room — Network Security Essentials

**Room:** https://tryhackme.com/room/networksecurityessentials

## What This Room Covers

Network Security Essentials is part of the SOC Level 1 Network Security Monitoring module. It focuses on this module covers practical defensive monitoring: network visibility, discovery, exfiltration, interception and IDS/Snort-based detection.

---

## Why Network Security Monitoring Matters

Network Security Monitoring (NSM) provides evidence of what systems communicate and whether their behavior deviates from an expected baseline. Defenders review **firewall, IDS/IPS, VPN, DNS, proxy, network flow and packet-capture** data.

## Important Defensive Concepts

| Concept | Analyst Relevance |
|---|---|
| Defense in depth | Multiple controls reduce dependence on a single perimeter |
| Segmentation | Restricts east-west movement and limits breach impact |
| Least privilege | Users and services receive only required permissions |
| Secure protocols | Prefer SSH/HTTPS over plaintext protocols where suitable |
| Ingress / Egress | Incoming versus outgoing traffic direction |
| Baseline | Expected ports, hosts, protocols and traffic volumes |

## Common Monitoring Sources

| Source | Typical Information |
|---|---|
| Firewall | Rule action, src/dst, ports, protocol, time |
| VPN | User sign-in, tunnel establishment, assigned IP |
| IDS | Signature, sensor, addresses, payload matches |
| NetFlow | Connection metadata and transferred bytes |
| DNS | Queried names and resolution outcomes |
| Proxy | Requested websites, users, categories, actions |

## SOC Triage Example

An internal workstation initiates outbound traffic to an unfamiliar host on a nonstandard port:

1. Check whether the connection was allowed or blocked.
2. Identify the owning user and endpoint.
3. Compare with known business applications and historical traffic.
4. Check DNS resolution and domain reputation.
5. Correlate with EDR process creation and related alerts.
6. Record the conclusion and escalation criteria.

## Key Terms

| Term | Meaning |
|---|---|
| North-south | Traffic between internal and external networks |
| East-west | Lateral traffic inside an environment |
| IDS | Detects suspicious activity and raises alerts |
| IPS | Can actively block traffic when deployed inline |
| NAC | Network Access Control policy enforcement |

## My Takeaway

Network monitoring is useful only when I understand visibility limits and business context. A blocked connection, an unusual port and a confirmed compromise are very different findings.
