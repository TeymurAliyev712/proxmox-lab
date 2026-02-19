# 05 — External Access Test (Host → VM → Container)

## Goal
Verify that the containerized web server is accessible from the host machine.

## Setup
- VM IP: 192.168.219.129
- Container: nginx (alpine)
- Port mapping: 8080 (host) → 80 (container)

## Test
Opened in browser:
http://192.168.219.129:8080

## Result
- Nginx default page successfully loaded
- HTTP 200 response confirmed

## Conclusion
End-to-end networking works:
Host → VM → Docker container → Nginx
