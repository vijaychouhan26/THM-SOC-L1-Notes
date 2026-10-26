# Room — Network Traffic Basics

**Room:** https://tryhackme.com/room/networktrafficbasics

## What This Room Covers

Network Traffic Basics is part of the SOC Level 1 Network Traffic Analysis module. It focuses on learning how to capture, filter and interpret network packets and extract artifacts useful for SOC alert investigations.

---

## What Is Network Traffic Analysis?

Network Traffic Analysis (NTA) means capturing and reviewing communications to understand **who connected to whom, over what protocol, and what happened**. SOC analysts combine packet data with DNS, firewall, proxy and endpoint logs.

## Data Sources

| Source | Visibility | Typical Limitation |
|---|---|---|
| PCAP | Packet headers and sometimes payload | Encryption, collection point and storage |
| NetFlow/IPFIX | Flow metadata and byte counts | No full application payload |
| DNS logs | Queries and responses | Caching/encrypted DNS may hide activity |
| Proxy logs | Requested URLs, identities, actions | Varies by inspection and TLS setup |
| Firewall logs | Allowed/blocked connections | Limited payload detail |

## TCP/IP Layers for Analysts

- **Link:** MAC addresses, ARP, VLAN information
- **Internet:** Source/destination IPs, ICMP, TTL
- **Transport:** TCP/UDP ports, flags, sequence information
- **Application:** DNS, HTTP, SMTP and other protocol structures

**Five-tuple:** source IP, source port, destination IP, destination port, transport protocol.

## Typical Investigation: DNS Tunneling Suspicion

1. Identify the host with unusually frequent DNS requests.
2. Group requests by base domain, query type and time.
3. Inspect unusually long/random-looking subdomains and TXT responses.
4. Compare with expected DNS clients and approved services.
5. Correlate endpoint activity and any packet capture.

```text
Unusual DNS volume → examine query names → inspect response types
                   → identify process/host → validate exfil or C2
```

## Key Terms

| Term | Meaning |
|---|---|
| NTA | Network Traffic Analysis |
| PCAP | Recorded packet capture |
| Flow | Summarized conversation metadata |
| Beaconing | Repeated communication often showing periodic timing |
| Baseline | Expected traffic pattern used for comparison |

## My Takeaway

Network logs give visibility into connections, but a PCAP can expose much more protocol detail. The correct conclusion still depends on context, baseline and corroborating evidence.
