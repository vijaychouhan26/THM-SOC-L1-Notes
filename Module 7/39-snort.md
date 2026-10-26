# Room — Snort

**Room:** https://tryhackme.com/room/snort

## What This Room Covers

Snort is part of the SOC Level 1 Network Security Monitoring module. It focuses on this module covers practical defensive monitoring: network visibility, discovery, exfiltration, interception and IDS/Snort-based detection.

---

## What Is Snort?

Snort is an open-source network intrusion detection/prevention engine. It can analyze live traffic or recorded PCAPs using rules and logging. Configuration and CLI switches vary between Snort 2 and Snort 3.

## Snort Rule Structure

```text
action protocol src_ip src_port -> dst_ip dst_port (options)
```

| Element | Example | Purpose |
|---|---|---|
| Action | `alert` | Generate an alert |
| Protocol | `tcp` | Match TCP packets |
| Source | `any any` | Any source IP and port |
| Direction | `->` | Match source-to-destination |
| Destination | `$HOME_NET 80` | Protected hosts on TCP/80 |
| Options | `msg`, `content`, `sid`, `rev` | Metadata and matching |

## Example Rule (Version-Dependent)

```snort
alert tcp any any -> $HOME_NET 80 (msg:"Lab HTTP GET"; flow:to_server,established; http_method; content:"GET"; sid:1000001; rev:1;)
```

For Snort 3 this example uses an HTTP sticky buffer. **Always validate compatibility in the installed lab version before running rules.** Local `sid` values need to avoid conflicts.

## Useful Snort 3 Command

```bash
sudo snort -q -l /var/log/snort -i lo -A alert_fast -c /etc/snort/snort.lua
```

| Flag | Meaning |
|---|---|
| `-q` | Quiet output |
| `-l` | Logging directory |
| `-i` | Network interface |
| `-A alert_fast` | Fast alert format |
| `-c` | Configuration file |

In this example `lo` means the loopback interface; substitute the correct capture interface when required. This form is not a universal Snort 2 instruction.

## Analyst Workflow

1. Review rule SID, message, protocol, addresses and ports.
2. Locate the related alert and PCAP/traffic.
3. Determine what content or condition caused the match.
4. Compare with expected business traffic and known benign triggers.
5. Adjust test detection logic only in an authorized lab.
6. Document accuracy, false positives, and any escalation.

## Key Terms

| Term | Definition |
|---|---|
| SID | Unique Snort rule identifier |
| REV | Rule revision |
| HOME_NET | Configured protected address range |
| PCAP | Packet capture file |
| NIDS | Network intrusion detection system |

## My Takeaway

Understanding why a Snort rule matched is more useful than memorizing the alert text. A strong analyst can explain the rule, reproduce the detection and verify its context.
