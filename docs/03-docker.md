# 03 — Docker installed & verified (inside Ubuntu VM)

## Goal
Install Docker on Ubuntu VM running inside Proxmox and verify it works by running a container.

## Proof
Command:
- `sudo docker run docker.io/library/hello-world:latest`

Result:
- Docker pulled the image successfully and printed `Hello from Docker!`.

## Why this matters
This confirms:
- networking inside the VM works
- Docker engine is installed and running
- we can deploy workloads (containers) on top of our virtualized lab
