# 03 — Networking (bridge)

## Goal
Provide network connectivity to VMs via a Linux bridge on Proxmox.

## Key concept
- Proxmox commonly uses a bridge interface (e.g., `vmbr0`) connected to the physical NIC.
- VMs attach to the bridge and receive L2/L3 connectivity like regular machines on the network.

## What I configured (nested lab)
- Proxmox host: bridge `vmbr0`
- Ubuntu VM: network interface attached to `vmbr0`
- Result: Ubuntu VM has network access (apt update / ping)

## Validation steps
On Ubuntu VM:
- `ip a`
- `ip route`
- `ping -c 3 1.1.1.1`
- `ping -c 3 google.com`

## Notes
In nested virtualization (VMware → Proxmox), networking works the same conceptually, but performance and NIC options may vary.
