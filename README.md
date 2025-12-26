# homelab-virtualbox-kali-ubuntu
Reproducible VirtualBox cybersecurity homelab with Kali Linux and Ubuntu: NAT + Host-Only networking, baseline snapshots, shared folders, and lab-ready documentation.

# VirtualBox Cybersecurity Homelab (Kali + Ubuntu)

This repository documents my local cybersecurity homelab built with VirtualBox.  
It is designed to practice safely in an isolated environment while keeping the setup reproducible and portfolio-ready.

## Lab Goals
- Build a safe, isolated environment for learning ethical hacking and basic blue-team tasks
- Use clean baselines (snapshots) to reset quickly after experiments
- Keep every step documented so the lab can be reproduced on another machine

## Environment
- Host OS: Windows 11
- Virtualization: VirtualBox
- VMs:
  - Kali Linux (attacker / tooling)
  - Ubuntu (target / defender)

## Network Topology
Each VM uses **two network adapters**:

1) **Adapter 1: NAT**
- Purpose: Internet access for updates/tools
- Notes: Not used for attacking other machines

2) **Adapter 2: Host-Only**
- Purpose: Isolated lab network (Kali ↔ Ubuntu)
- Notes: All security testing happens only on this network

Example Host-Only subnet (typical VirtualBox default): `192.168.56.0/24`

## Quick Checks
### On Kali
```bash
ip a
ip r
ping -c 2 1.1.1.1
