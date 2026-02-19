# 01 — Proxmox installation (nested in VMware)

## Goal
Deploy Proxmox VE inside VMware to practice hypervisor management.

## Steps
1. Created a VMware VM (nested virtualization enabled).
2. Attached Proxmox ISO and installed Proxmox VE.
3. Verified access to Proxmox Web UI.

## Notes
- Nested virtualization must be enabled in VMware settings.
- CPU virtualization (VT-x/AMD-V) required on host.
