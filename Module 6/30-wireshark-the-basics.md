# Room — Wireshark: The Basics

**Room:** https://tryhackme.com/room/wiresharkthebasics

## What This Room Covers

Wireshark: The Basics is part of the SOC Level 1 Network Traffic Analysis module. It focuses on learning how to capture, filter and interpret network packets and extract artifacts useful for SOC alert investigations.

---

## What Is Wireshark?

Wireshark is a packet analyzer for inspecting network protocols and recorded PCAP files. It is widely used for troubleshooting, network forensics and verifying IDS alerts.

## Main Interface

| Panel | Purpose |
|---|---|
| Packet List | Time, source, destination, protocol and summary |
| Packet Details | Decoded protocol fields |
| Packet Bytes | Raw packet bytes with protocol highlights |
| Display Filter Bar | Narrow which packets are shown |

## Display Filters

```wireshark
ip.addr == 192.0.2.10
tcp.port == 443
dns
http.request
tcp.flags.syn == 1 && tcp.flags.ack == 0
```

- `ip.src` and `ip.dst` filter by direction.
- `frame.number` helps cite exact evidence.
- A **display filter** hides unrelated rows; it does not remove packets from the capture.

## Capture vs Display Filters

| Filter | Example | Applied |
|---|---|---|
| Capture (BPF) | `tcp port 443` | While recording |
| Display | `tcp.port == 443` | While inspecting |

## Practical Investigation

1. Open the PCAP and check capture time range.
2. Review **Statistics → Protocol Hierarchy**.
3. Open **Statistics → Conversations** to find important endpoints.
4. Filter by suspected source and destination.
5. Expand Ethernet, IP, TCP/UDP and application fields.
6. Note timestamps, frame numbers and relevant anomalies.
7. Preserve the original file for reproducibility.

## Key Terms

| Term | Definition |
|---|---|
| PCAP | File containing captured packets |
| Protocol dissector | Decodes network protocol fields |
| Display filter | Expression used to show selected packets |
| Capture filter | Expression limiting packets recorded |

## My Takeaway

The fastest workflow is to first understand the entire capture, then narrow to a conversation with filters rather than scrolling blindly through thousands of packets.
