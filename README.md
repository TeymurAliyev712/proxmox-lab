# Proxmox Lab (nested on VMware)

Homelab project: Proxmox VE deployed inside VMware (nested virtualization) + Ubuntu Server VM.
Goal: practice virtualization, networking, backups, and basic DevOps workflow with GitHub documentation.

## Environment
- Host OS: Windows 11
- Virtualization: VMware (nested)
- Hypervisor inside VM: Proxmox VE
- Guest VM: Ubuntu Server

## What I built
- Installed Proxmox VE and accessed the web UI
- Created Ubuntu Server VM
- Configured basic networking (bridge)
- Enabled version control/documentation via GitHub

## Lab tasks (planned / in progress)
- [ ] Document Proxmox installation steps
- [ ] VM creation (CPU/RAM/Disk)
- [ ] Network setup (vmbr0, NAT/bridge notes)
- [ ] Backups (vzdump) + restore test
- [ ] Templates / cloud-init basics
- [ ] Snapshots and rollback scenario

## Evidence
Screenshots are stored in `screenshots/`.
Notes and step-by-step docs are in `docs/`.

## How to reproduce
See `docs/01-installation.md` and `docs/02-ubuntu-vm.md`.
## Screenshots
- `screenshots/01-proxmox-dashboard.png`
- `screenshots/02-vm-list.png`
- `screenshots/03-ubuntu-network.png`
