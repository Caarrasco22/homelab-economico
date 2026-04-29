# Homelab architecture

## Overview

This homelab is built around a main Proxmox VE host, a Raspberry Pi 4 used as a supporting network node and an isolated lab network managed with OPNsense.

The current architecture focuses on three goals:

1. Learn real networking and infrastructure concepts on a low budget.
2. Make internal services easy to access through local `.lab` domains.
3. Avoid unnecessary exposure to the public Internet.

## Main layers

### Main LAN

The main LAN uses the documented subnet `192.168.0.0/24`. It contains home devices, the Proxmox host, the Raspberry Pi and several internal services.

### Proxmox VE host

The Proxmox VE server is the core of the lab. It runs lightweight LXC containers and virtual machines for specific services.

Main responsibilities:

- Virtualization.
- Container and VM management.
- Snapshots and backups.
- Local storage.
- Self-hosted service testing.

### Raspberry Pi 4

The Raspberry Pi 4 acts as a supporting node for network-related services.

Current roles:

- Secondary Pi-hole.
- Nginx Proxy Manager.
- Tailscale remote access node.

### OPNsense lab network

OPNsense is used as a lab firewall/router to practice segmentation, NAT, firewall rules, DHCP per subnet and separation between network zones.

The current lab LAN is documented as `192.168.50.0/24`, with a Debian Lab VM used as a test client.
