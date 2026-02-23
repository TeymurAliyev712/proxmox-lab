# Architecture (Proxmox → Ubuntu VM → Docker Lab)

```mermaid
flowchart TB
    A[Windows 11 Host] --> B[VMware (nested)]
    B --> C[Proxmox VE]
    C --> D[Ubuntu Server VM]

    subgraph Docker on Ubuntu
      N[Docker bridge network: lab-net]
      W[nginx container (web)\nports: 8080->80]
      P[postgres:16 container (db)\ninternal:5432]
      AD[adminer container\nports: 8081->8080]
      W --- N
      P --- N
      AD --- N
    end

    D --> W
    D --> P
    D --> AD

    U[Your laptop browser] -->|http://VM_IP:8080| W
    U -->|http://VM_IP:8081| AD
    AD -->|connects to db via name "db"| P
