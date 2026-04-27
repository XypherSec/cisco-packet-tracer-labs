# DHCP Server Lab — Cisco Packet Tracer

## Objective
Configure a dedicated DHCP server to automatically
assign IP addresses to client PCs on a LAN.

## Topology
- 1x Cisco 2960-24 Switch
- 1x Server-PT (DHCP Server)
- 3x PCs (DHCP Clients)

## IP Addressing Results
| Device | IP Assigned   | Method |
|--------|--------------|--------|
| PC0    | 192.168.1.12 | DHCP   |
| PC1    | 192.168.1.11 | DHCP   |
| PC2    | 192.168.1.10 | DHCP   |

## Protocols Used
| Protocol | Port | Purpose |
|----------|------|---------|
| DHCP | 67/68 | Automatic IP assignment |

## What I Learned
- How to configure a Server-PT as a DHCP server
- How DHCP automatically assigns IPs to clients
- How to verify successful IP assignment

## Tools Used
- Cisco Packet Tracer 9.0
