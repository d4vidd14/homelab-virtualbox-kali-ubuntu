# VirtualBox Cybersecurity Homelab (Kali + Ubuntu)

Reproducible VirtualBox cybersecurity homelab with Kali Linux and Ubuntu: NAT + Host-Only networking, baseline snapshots, shared folders, and lab-ready documentation.

## Goal
Practice cybersecurity safely in an isolated environment and keep everything reproducible for portfolio/CV use.

## Environment
- Host OS: Windows 11 (16 GB RAM)
- Hypervisor: Oracle VirtualBox
- VMs:
  - Kali Linux (attacker / tooling)
  - Ubuntu Desktop (target / defender)

## Network Topology
Each VM uses **two network adapters**:

### Adapter 1 — NAT (Internet)
Used only for:
- system updates
- downloading tools

### Adapter 2 — Host-Only (Lab Network)
Used for:
- Kali ↔ Ubuntu communication
- scanning/testing **only inside the lab**

## IP Addresses
> Use the **Host-Only** IPs for ping, nmap, ssh, etc.

| Machine | NAT (Internet) | Host-Only (Lab) |
|--------|------------------|-----------------|
| Ubuntu | `10.0.2.15` | `192.168.56.102` |
| Kali  | `10.0.2.X` | `192.168.56.X` |

To check the current IPs on any VM:
```bash
hostname -I
ip a
ip r
