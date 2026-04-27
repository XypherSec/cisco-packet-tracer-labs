# Email Server Simulation — Cisco Packet Tracer

## Objective
Configure and simulate a functional email server
enabling users to send and receive emails across
a local area network.

## Topology
- 1x Cisco 2960-24 Switch
- 1x Server-PT (Email Server)
- 3x PCs (Email Clients — PC0, PC1, PC2)

## Server Configuration
- Domain Name: gmail.com
- SMTP Service: Enabled (Port 25)
- POP3 Service: Enabled (Port 110)

## User Accounts
| Username | Email |
|----------|-------|
| kris | kris@gmail.com |
| tech | tech@gmail.com |
| jerry | jerry@gmail.com |

## How It Works
1. PC0 composes email and sends via SMTP Port 25
2. Server0 receives and stores email in recipient mailbox
3. PC1 connects via POP3 Port 110 and retrieves email

## Protocols Used
| Protocol | Port | Purpose |
|----------|------|---------|
| SMTP | 25 | Sending emails |
| POP3 | 110 | Receiving emails |
| DNS | 53 | Resolving mail domain |

## Security Observations
- POP3 Port 110 transmits data unencrypted
- SMTP Port 25 vulnerable to open relay attacks
- No TLS/SSL encryption configured
- Real fix: Use SMTPS Port 465 and POP3S Port 995

## What I Learned
- How to configure SMTP and POP3 on a server
- How email flows between clients on a network
- Security risks of unencrypted mail protocols

## Tools Used
- Cisco Packet Tracer 9.0
