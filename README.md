
# Homelab Setup with Docker

My personal homelab configuration with docker. Includes traefik, pihole, portainer, dashy, mysql, phpmyadmin, grafana, nextcloud and uptime-kuma.

---

## Requirements

You need to have docker and docker compose installed. It was tested and run on Ubuntu 20.04 LTS and Docker Version 23.0.1.

---

## Docker Installation

### Docker & Docker-Compose installation

I installed docker using the bash script:

    curl -fsSL https://get.docker.com -o get-docker.sh
    sh get-docker.sh

And insalled docker-compose with:

    apt install docker-compose

---

## Vars

You can cutimize everything tourght the ".env"-File. Keep in mind to create the directories on the docker host before deploying the service.

---

## Pereperation for Deploying services

First make sure the directories in the ".env"-File exits. To access the Services with the DNS-Name you need to create a A/AAAA-Record first (not required for PiHole and Traefik).

My personal deploying order:

1. Traefik
2. Pihole
3. Create A-Name Records by accessing "http://\<docker-host-ip>:8080/admin/"
4. Deploy other Services
5. Access Services over your DNS-Name

---

## Deploying the Services

To deploy a service go into the directory e.g. "00-traefik" and run:

    docker compose --env-file ./path/to/env/file/.env up -d

---

## Roadmap

More Services to add:

- Loggin (something like a ELK stack or Graylog)
- Network Monitoring (NTOPNG)
- Documentation (something like Dokuwiki/Mediawiki)
- Watchtower (update Docker Services)
- Backup (Maybe a own build docker Container wich Backups the docker app data)
- And more useful docker apps (node-red/n8n, gitea, jenkins, ...) in the future

---

## Smarthome

I personal run Homebrige on a diffrent host and since HomeAssistant in docker has some limitations with plugins i would deploy it direct to the docker host (not in a container) or on a diffrent host.
