# Room — SOC Workbooks and Lookups

## What This Room Covers
Corporate resources that help L1 analysts structure and speed up alert triage — workbooks, asset inventories, and network diagrams.

---

**Room:** https://tryhackme.com/room/socworkbookslookups

---

## What Are SOC Workbooks?

Workbooks are pre-built investigation guides for specific alert types. Instead of figuring out how to investigate a phishing alert from scratch every time, you follow the workbook — same steps, same quality, every time.

Think of them as playbooks — they tell you:
- What information to collect
- What tools to use
- What questions to answer
- When to escalate

**Why they matter:** Consistency. A new analyst following a workbook produces the same quality investigation as an experienced one.

---

## Asset Inventory & Identity Lookups

During triage, you often need context about the user or system involved. Asset inventory and identity lookups answer:

| Question | Where to look |
|----------|--------------|
| Who is this user? | HR/Identity directory (Active Directory, Okta) |
| What's their role/department? | Identity store |
| Is this device managed? | Asset inventory / CMDB |
| What's the normal behavior for this host? | Baseline / asset notes |
| Is this IP internal or external? | Network diagram / asset inventory |

Getting this context fast is what separates a slow triage from an efficient one.

---

## Network Diagrams

Network diagrams show how systems are connected — which hosts are internet-facing, which are internal, which are in the DMZ.

**Why it matters for triage:**
- An alert on a DMZ host = higher risk (internet-facing)
- An alert on an internal DB server = potential lateral movement
- Knowing the network layout helps you assess severity accurately

---

## Building Investigation Workflows

The room introduces building custom workflows inside an interactive interface. A good L1 workflow looks like:

```
Alert received
    ↓
Check workbook for this alert type
    ↓
Look up user/asset context
    ↓
Check network diagram for host context
    ↓
Apply Five Ws → write report
    ↓
Escalate or close
```

---

## Key Terms

| Term | Definition |
|------|------------|
| Workbook | Pre-built investigation guide for a specific alert type |
| CMDB | Configuration Management Database — inventory of all IT assets |
| Asset Inventory | List of all devices, servers, and systems with their details |
| Network Diagram | Visual map of the network showing how systems connect |
| Lookup | Quickly retrieving user or system context during triage |

---

## My Takeaway
Workbooks and lookups are what make a SOC scalable. Without them, every analyst reinvents the wheel for every alert. With them, triage is faster, more consistent, and less dependent on individual experience.

---

*Part of my THM SOC Level 1 Notes*
*GitHub: https://github.com/vijaychouhan26/THM-SOC-L1-Notes*
*TryHackMe: https://tryhackme.com/p/Vijaychouhan*
*LinkedIn: https://www.linkedin.com/in/vijay-chouhan-1130632b7/*
