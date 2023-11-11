# Docker Compose Traefik Setup

## Setup the network
```
docker network create \
  --driver=bridge \
  --attachable \
  --internal=false \
  proxy-network
```
