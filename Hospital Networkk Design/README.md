# Lab 01 – Hospital Network Design

## Overview

A multi-department hospital network built in Cisco Packet Tracer, demonstrating hierarchical LAN design with a central distribution switch, departmental access switches, and a single router gateway.

---

## Topology Summary

- **Router:** 2811 `Router0` — Gateway IP: `192.168.1.1`
- **Core Switch:** 2960-24TT `Switch0` — Central distribution point
- **Access Switches:** 2960-24TT `Switch1–Switch15` — One per department
- **End Devices:** PCs (`PC0–PC26`) across all departments
- **Simulation:** ICMP ping from PC0 → PC12 verified (Scenario 0)

---

## Department & Subnet Map

| Department           | Switch   | Subnet           | Hosts                          |
|----------------------|----------|------------------|--------------------------------|
| Accident & Emergency | Switch6  | 192.168.20.x     | PC0 (20.10), PC1 (20.11), PC2 (20.12) |
| Ward                 | Switch7  | 192.168.20.x     | PC3 (20.20), PC4 (20.21), PC5 (20.22) |
| Pathology            | Switch8  | 192.168.30.x     | PC6 (30.10), PC7 (30.11), PC8 (30.12) |
| Blood Bank           | Switch9  | 192.168.30.x     | PC9 (30.20), PC10 (30.21), PC11 (30.22), PC12 (30.23) |
| Laboratory           | Switch2  | —                | Connected via Switch0          |
| Medicine             | Switch1  | —                | Connected via Switch0          |
| IT / Network         | Switch5  | —                | Connected via Switch0          |
| Security             | Switch10 | 192.168.50.x     | PC20 (50.20), PC21 (50.21)    |
| Pharmacy             | Switch3  | —                | Connected via Switch0          |
| Drug Store           | Switch12 | 192.168.40.x     | PC24 (40.10), PC25 (40.11)    |
| Consultant           | Switch13 | 192.168.40.x     | PC26 (40.20)                  |
| Administration       | Switch4  | —                | Connected via Switch0          |
| HR                   | Switch14 | 192.168.10.x     | PC18 (10.10), PC19 (10.11)    |
| Finance              | Switch15 | 192.168.10.x     | PC13–PC17 (10.20–10.24)       |

---

## Network Design

```
[Router0] 192.168.1.1
     |
  [Switch0]  ← Core / Distribution Layer
  /  |  |  \  \  \  \  \
Sw1 Sw2 Sw3 Sw4 Sw5 Sw6 Sw7 ... Sw15   ← Access Layer (per dept)
 |   |   |   |   |   |   |         |
PCs PCs PCs PCs PCs PCs PCs       PCs   ← End Devices
```

### Key Design Decisions
- **Star topology** at both core and access layers (hierarchical model)
- **Single router** acts as default gateway for all subnets
- **Flat routing** — all departments reachable via Router0 at `192.168.1.1`
- **Subnets** grouped by functional area (20.x = clinical, 30.x = lab, 40.x = support, 50.x = security, 10.x = admin/finance)

---

## Lab Objectives

- [x] Design a multi-department network topology
- [x] Assign IP addresses across multiple subnets
- [x] Configure a default gateway (Router0)
- [x] Verify end-to-end connectivity via ICMP ping (PC0 → PC12)
- [ ] Configure inter-VLAN routing
- [ ] Apply ACLs to restrict cross-department access
- [ ] Add DHCP server for dynamic IP assignment

---

## Verification

The simulation panel shows:
- **Source:** PC0 | **Destination:** PC12 | **Type:** ICMP
- **Time:** 0.000s — packet delivered successfully

### CLI Verification Commands
```
! On Router0
Router# show ip interface brief
Router# show ip route

! On any PC
PC> ping 192.168.1.1
PC> ping <another_dept_PC_IP>
PC> tracert <destination_IP>
```
---

## Possible Enhancements

- Segment each department into its own **VLAN** with a Layer 3 switch
- Add a **DHCP server** on Router0 or a dedicated server device
- Implement **ACLs** — e.g., Finance should not be reachable from Ward
- Add **redundant uplinks** between access switches and core
- Include a **server farm** (DNS, HTTP, email) for hospital services
