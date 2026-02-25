# Docker Lab (nginx + postgres + adminer + custom network)

## What we did and why

### 1) `docker pull nginx / postgres / adminer`
We downloaded ready-to-use Docker images from Docker Hub (official repositories: `library/nginx`, `library/postgres`, `library/adminer`).

An image is a read-only template (filesystem + metadata) used to create containers.

---

### 2) `docker network create lab-net`
We created a dedicated Docker **bridge** network.

Why:
- Containers on the same custom network can communicate by **container/service name**
- They are isolated from other containers

---

### 3) `docker run ... postgres:16`
We started a PostgreSQL container and passed environment variables:

- `POSTGRES_USER`
- `POSTGRES_PASSWORD`
- `POSTGRES_DB`

These variables are used by the image entrypoint during the first startup to initialize the database.

---

### 4) `docker network inspect lab-net`
We inspected the network to verify:

- subnet / gateway
- which containers are attached
- internal container IP addresses

This confirms the network exists and the containers are connected to it.

---

## How to run using Docker Compose

```bash
cd docker-lab
docker-compose up -d
docker ps
```

---

## Additional Details (Commands + Explanation)

### Docker network

```bash
docker network create lab-net
docker network inspect lab-net
```

---

### Running containers

#### PostgreSQL

```bash
docker run -d --name db --network lab-net \
  -e POSTGRES_PASSWORD=StrongPass123! \
  -e POSTGRES_USER=appuser \
  -e POSTGRES_DB=appdb \
  postgres:16
```

#### Adminer

```bash
docker run -d --name adminer --network lab-net -p 8081:8080 adminer:latest
```

#### Nginx

```bash
docker run -d --name web --network lab-net -p 8080:80 nginx:latest
```

#### Checking containers

```bash
docker ps
```

---

## How to reproduce (run the same lab)

> Goal: run PostgreSQL + Adminer + Nginx on a custom Docker network (lab-net)  
> Adminer connects to Postgres using hostname "db"

### Where do these images come from?

Official Docker Hub images:
- nginx → docker.io/library/nginx
- postgres → docker.io/library/postgres
- adminer → docker.io/library/adminer

---

### 1) Pull images

```bash
docker pull nginx:latest
docker pull postgres:16
docker pull adminer:latest
```

---

### 2) Create network

```bash
docker network create lab-net
docker network ls
```

(Optional)

```bash
docker network inspect lab-net
```

---

### 3) Run PostgreSQL

```bash
docker run -d --name db --network lab-net \
  -e POSTGRES_USER=appuser \
  -e POSTGRES_PASSWORD=StrongPass123! \
  -e POSTGRES_DB=appdb \
  postgres:16
```

---

### 4) Run Adminer

```bash
docker run -d --name adminer --network lab-net -p 8081:8080 adminer:latest
```

Open in browser:
http://<VM_IP>:8081

Login:
- System: PostgreSQL
- Server: db
- Username: appuser
- Password: TAPass123!
- Database: appdb

---

### 5) Run Nginx

```bash
docker run -d --name web --network lab-net -p 8080:80 nginx:latest
```

Open in browser:
http://<VM_IP>:8080

---

### 6) Check containers

```bash
docker ps
```
