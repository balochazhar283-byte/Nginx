# Nginx + Apache2 load balancer demo

Browser -> Nginx (port 80) -> Apache2 (50/50 balancer) -> app1 / app2

## Run on EC2
    sudo systemctl stop nginx httpd 2>/dev/null   # free port 80 on the host
    docker compose up -d --build
    docker compose ps

## Test
    for i in {1..6}; do curl -s http://localhost | grep Hello; done

Open http://<EC2-PUBLIC-IP> (Security Group must allow port 80).

## Logs
    docker compose logs nginx
    docker compose logs apache

## Stop
    docker compose down
