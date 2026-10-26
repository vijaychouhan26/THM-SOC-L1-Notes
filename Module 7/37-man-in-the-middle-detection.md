# Room — Man-in-the-Middle Detection

**Room:** https://tryhackme.com/room/mitmdetection

## What This Room Covers

Man-in-the-Middle Detection is part of the SOC Level 1 Network Security Monitoring module. It focuses on this module covers practical defensive monitoring: network visibility, discovery, exfiltration, interception and IDS/Snort-based detection.

---

## What Is a Man-in-the-Middle Attack?

In a MITM or adversary-in-the-middle scenario, an attacker intercepts or manipulates communication between two parties. Monitoring focuses on anomalies in **ARP, DNS, network routing and TLS**.

## Common Attack Patterns

| Pattern | What a Defender Might Observe |
|---|---|
| ARP spoofing | Different MAC addresses claiming the same gateway IP |
| DNS spoofing | Unexpected answers for trusted domains |
| SSL stripping / downgrade | Unexpected plaintext HTTP or redirect behavior |
| Rogue access point | Unknown wireless network impersonating trusted SSID |
| Session interception | Suspicious session or certificate anomalies |

## Wireshark Display Filters

```wireshark
arp
arp.opcode == 2
dns
http
tls
```

## ARP Investigation Example

A workstation believes that `192.168.1.1` is its gateway. Multiple unsolicited ARP replies claim that IP belongs to different MAC addresses.

1. Identify timestamps and MAC address changes.
2. Compare with switch tables and DHCP history.
3. Check for gateway failover, virtualization or legitimate configuration changes.
4. Review surrounding DNS and HTTP/TLS behavior.
5. Determine which host, if any, sent false ARP claims.
6. Record impact and recommend network containment if justified.

## DNS and TLS Checks

- Compare observed DNS answers with trusted resolvers and known service addresses.
- Look for sudden changes in certificates or unexpected issuers.
- Remember that TLS proxying and enterprise security gateways can legitimately alter certificate paths.

## Key Terms

| Term | Meaning |
|---|---|
| ARP | Maps an IPv4 address to a link-layer address on a local network |
| ARP poisoning | Injection of false address mappings |
| TLS | Encryption and authentication protocol for network sessions |
| Rogue AP | Unauthorized wireless access point |

## My Takeaway

A gateway mapping anomaly should start an investigation, not finish it. I need to establish whether network changes were malicious and whether traffic interception occurred.
