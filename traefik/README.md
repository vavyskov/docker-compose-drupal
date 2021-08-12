# Traefik

## Environments
This Compose file contains the following environment variables:

- `TRAEFIK_VERSION` the default value is **2.2**
- `TRAEFIK_PORT` the default value is **8080**

You can set environment variables in `.env` file.

## Quick start

1. Open the terminal, navigate to the directory containing the file `docker-compose.yml` and run commands:

       docker network create frontend_network
       docker-compose up -d

   Other commands:

   - `docker-compose stop` (stop containers)
   - `docker-compose start` (start containers)
   - `docker-compose down` (destroy containers)

1. Access to Traefik: 

   - URL:
      - Docker CE: `localhost:8080` or `127.0.0.1:8080`
      - Docker Toolbox: `192.168.99.100:8080`
      - Traefik (hosts): `traefik.example.com`
   - User: `traefik`
   - Password: `traefik`

1. Optionally configure your system `hosts` file:

   - Docker CE: `127.0.0.1 traefik.example.com`
   - Docker Toolbox: `192.168.99.100 traefik.example.com`

   Path:
   - Linux: `/etc/hosts`
   - macOX: `/private/etc/hosts`
   - Windows: `C:\Windows\System32\drivers\etc\hosts`


## Network
Show IP address:

    docker network inspect frontend_network | grep IPv

## Let's Encrypt
[Traefik - Let's Encrypt](https://git-scm.com/?target=_blank)

## Custom certificates

Dynamic folder with `certificates.yml` file is the only available method to configure custom certificates!