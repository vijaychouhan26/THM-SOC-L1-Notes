# Room — Wireshark: Packet Operations

**Room:** https://tryhackme.com/room/wiresharkpacketoperations

## What This Room Covers

Wireshark: Packet Operations is part of the SOC Level 1 Network Traffic Analysis module. It focuses on learning how to capture, filter and interpret network packets and extract artifacts useful for SOC alert investigations.

---

## What This Room Covers

Packet operations build on basic navigation: filtering, conversation statistics, reconstructing streams and extracting useful evidence from large captures.

## Wireshark Features

| Feature | SOC Use |
|---|---|
| Follow TCP Stream | Reconstruct a TCP application conversation where visible |
| Follow HTTP Stream | Review related HTTP transactions where decoded |
| Statistics → Conversations | Identify endpoints and byte volumes |
| Statistics → Endpoints | Count communicating hosts |
| Protocol Hierarchy | Discover traffic mix |
| Expert Information | Flag packet-level abnormalities |
| Export Objects | Extract supported protocol objects when authorized |

## Useful Filters

```wireshark
tcp.stream == 4
dns.qry.name contains "example"
http.response.code == 404
frame contains "User-Agent"
tcp.analysis.retransmission
```

Field availability depends on the decoded protocol and capture. The stream number shown above is illustrative; select the actual conversation in your PCAP.

## Following a Suspicious Stream

1. Filter to the endpoint or port of interest.
2. Select a packet in the connection.
3. Right-click → **Follow → TCP Stream**.
4. Observe client versus server content and the transport direction.
5. Switch back to packet view to validate timestamps and sequence.
6. If evidence is exported, calculate a hash and note the originating stream.

## Key Investigation Pitfalls

- TCP reassembly may not work if the capture is incomplete.
- HTTPS payload is not normally readable without lawful/authorized decryption keys.
- Retransmissions are common on unstable networks; they are not malware signatures.
- Treat exported objects as potentially dangerous and keep them isolated.

## My Takeaway

Following streams and using statistics turns a PCAP from individual packets into a reconstructable sequence of events with useful endpoints and artifacts.
