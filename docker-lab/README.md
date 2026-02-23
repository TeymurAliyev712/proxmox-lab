# Docker Lab (nginx + postgres + adminer + custom network)

## What we did and why

### 1) `docker pull nginx / postgres / adminer`
We downloaded ready-to-use Docker images from Docker Hub (official repositories: `library/nginx`, `library/postgres`, `library/adminer`).
An image is a read-only template (filesystem + metadata) used to create containers.

### 2) `docker network create lab-net`
We created a dedicated Docker **bridge** network.
Why: containers on the same custom network can communicate by **container/service name** (e.g., `db`, `adminer`, `web`) and remain isolated from other containers.

### 3) `docker run ... postgres:16`
We started a PostgreSQL container and passed environment variables:
- `POSTGRES_USER` / `POSTGRES_PASSWORD` / `POSTGRES_DB`

These variables are used by the image entrypoint during the first startup to initialize the database and user.

### 4) `docker network inspect lab-net`
We inspected the network to verify:
- subnet / gateway
- which containers are attached
- internal container IP addresses

This confirms the network exists and the containers are connected to it.

## How to run using Docker Compose

```bash
cd docker-lab
docker compose up -d
docker ps
