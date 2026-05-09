# Router DHCP Server Lab

## Overview
A Cisco Packet Tracer lab demonstrating how to configure a **router as a DHCP server**
to automatically assign IP addresses to end devices on a LAN.

---

## Network Topology
---

## Devices Used
| Device   | Model       | Role          |
|----------|-------------|---------------|
| Router1  | Cisco 2911  | DHCP Server   |
| Switch1  | Cisco 2950-24 | Layer 2 Switch |
| PC0–PC2  | PC-PT       | DHCP Clients  |

---

## Router DHCP Configuration (IOS Commands)

```bash
Router>enable
Router#config terminal

! Create DHCP Pool
Router(config)#ip dhcp pool LAN_POOL
Router(dhcp-config)#network 192.168.1.0 255.255.255.0
Router(dhcp-config)#default-router 192.168.1.1
Router(dhcp-config)#dns-server 8.8.8.8
Router(dhcp-config)#exit

! Exclude static/reserved addresses
Router(config)#ip dhcp excluded-address 192.168.1.1 192.168.1.10
```

---

## DHCP Lease Results

| Device | Assigned IP     | Subnet Mask     | Gateway     | DNS     |
|--------|-----------------|-----------------|-------------|---------|
| PC0    | 192.168.1.13    | 255.255.255.0   | 192.168.1.1 | 8.8.8.8 |
| PC1    | 192.168.1.12    | 255.255.255.0   | 192.168.1.1 | 8.8.8.8 |
| PC2    | 192.168.1.11    | 255.255.255.0   | 192.168.1.1 | 8.8.8.8 |

> IPs `.1` through `.10` were excluded for static/admin use.

---

## Screenshots

| Description | File |
|---|---|
| Network Topology | `Screenshot_2026-05-09_000452.png` |
| Router CLI DHCP Config | `Screenshot_2026-05-09_000747.png` |
| PC IP Verification | `Screenshot_2026-05-09_000931.png` |

---

## Key Concepts Demonstrated
- Router-based DHCP server configuration
- DHCP pool creation with network, gateway, and DNS
- Excluding IP ranges from DHCP assignment
- Verifying automatic IP assignment on client PCs

---

## Tools
- Cisco Packet Tracer 9.0
- Cisco IOS CLI
