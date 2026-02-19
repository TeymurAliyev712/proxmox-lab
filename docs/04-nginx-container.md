# 04 — Docker: Nginx container (port publish) + health check

## VM
- Ubuntu Server IP: 192.168.219.129
- Docker bridge: 172.17.0.1/16 (docker0)

## Run
sudo docker run -d --name webtest -p 8080:80 nginx:alpine

## Proof
### Container is running
sudo docker ps

### Nginx responded (HTTP 200)
curl -I http://localhost:8080

### Port is listening on the VM
ss -lntp | grep 8080

### Logs show the request
sudo docker logs --tail 20 webtest
