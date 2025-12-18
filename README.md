# TCP_Attacks_Lab_REPORT
# TCP Attacks Lab – SYN Flood, TCP Reset, Session Hijacking

This repository contains my lab work for a Network Security exercise focused on practical TCP attacks and basic defensive mechanisms. The goal is to demonstrate how specific TCP behaviors can be abused in controlled environments, and what mitigations exist.

## Lab Topology (VMs)
- **Server:** `10.0.2.4`
- **Client:** `10.0.2.5`
- **Attacker:** `10.0.2.15` / `10.0.2.6` (depending on the task)

> Note: During the lab, correct VM networking was critical (e.g., using a NAT Network) to ensure full communication between attacker, server, and client.

## Scenarios Covered
### 1) SYN Flood Attack (DoS)
- Simulates a SYN flood against the server to exhaust the connection backlog (observed on Telnet port **23**).
- Validates the impact on legitimate client connectivity.
- Demonstrates mitigation using **SYN cookies** (enabling them reduces the effectiveness of the flood).

### 2) TCP Reset Attack – Telnet
- Uses Wireshark to observe a live Telnet TCP connection (port **23**).
- Demonstrates connection termination by injecting a forged **RST** packet.
- Emphasizes the importance of correct **sequence number** for a successful reset.

### 3) TCP Reset Attack – SSH
- Repeats the reset attack methodology on SSH (port **22**).
- Shows that encryption protects payload content, but not TCP header metadata required to craft a reset.

### 4) TCP Session Hijacking (Telnet)
- Captures relevant TCP packet details from an existing Telnet session.
- Injects a spoofed packet as if sent by the client in order to trigger server-side actions (e.g., reading a “secret” file).
- Highlights how lack of encryption + packet injection can lead to command execution within a session.

## Repository Contents (recommended)
- `TCP_ATTACK_LAB_REPORT.docx` – full report with screenshots, observations, and conclusions
- `scripts/` – lab scripts used for packet crafting (if included)
- `pcaps/` – Wireshark capture files (optional)
- `screenshots/` – evidence screenshots (optional)

## Ethical Use
This project is for **educational purposes only** and must be executed **only in an isolated lab environment** with explicit authorization. Do not use these techniques on real networks/systems.

## Tools Used
- Wireshark
- Telnet / SSH client
- Linux networking utilities
- Python (for packet crafting scripts, if included)
