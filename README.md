# Caddy with Advanced Configs
This is a specific caddy build that supports the below:
1. Rate Limiting
2. GeoBlocking & Control
## Usage
You can find the docker-compose configuration snippet example here:
```
  caddy:
    image: ghcr.io/giveth/mm-caddy:latest
    container_name: caddy
    restart: unless-stopped
    networks:
      - mynetwork
    ports:
      - 80:80
      - 443:443
    env_file:
      - .env
    environment:
      MY_URL = ${MY_URL:-}
      RESTRICTED_PATHS: ${RESTRICTED_PATHS:-}
      IP_WHITELIST: ${IP_WHITELIST:-}
    volumes:
      - caddy_data:/data
      - caddy_config:/config
      - ./Caddyfile:/etc/caddy/Caddyfile
```
