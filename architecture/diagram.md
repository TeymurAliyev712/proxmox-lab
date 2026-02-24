
```markdown
# Architecture (Proxmox → Ubuntu VM → Docker Lab)

```mermaid
flowchart TB
  %% Client
  U[Your laptop browser]

  %% Host stack
  subgraph HOST[Windows 11 host]
    VMW[VMware nested virtualization]
    PVE[Proxmox VE]
    UB[Ubuntu Server VM]
    VMW --> PVE --> UB
  end

  %% Docker stack
  subgraph DOCKER[Docker on Ubuntu]
    subgraph NET[Bridge network: lab-net]
      WEB[nginx container]
      ADM[Adminer container]
      DB[(Postgres container)]
    end

    VOL[(Named volume: db_data)] --- DB
  end

  %% Traffic
  U -->|HTTP 8080| WEB
  U -->|HTTP 8081| ADM
  ADM -->|connects to DB host: db| DB

  %% Notes (optional)
  WEB -. serves static or reverse proxy .- WEB
