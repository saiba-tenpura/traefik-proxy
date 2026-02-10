# Traefik Compose
A Traefik docker compose instance for usage in other compose setups as reverse proxy.

## Setup the network
```
docker network create \
  --driver=bridge \
  --attachable \
  --internal=false \
  proxy-network
```

## Usage
To use it in a compose setup make the following adjustments to the service which should be proxied.
```
# compose.yaml
services:
  service:
    ...
    networks:
      - proxy-network
    ...
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.service.rule=Host(`${SERVICE_URL}`)"
      - "traefik.http.routers.service.tls=true"

networks:
  ...
  proxy-network:
    external: true
```

