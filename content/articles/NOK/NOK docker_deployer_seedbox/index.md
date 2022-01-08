---
title: "Déployer une seedbox rapidement avec Docker"
date: 2021-07-01
lastmod: 
draft: true

heroimg: images/articles-vierge.webp
#description: 
#keywords:

categories:
- linux
- informatique
- docker

series:
- docker
- seedbox
  
tags:
- seedbox
- radarr
- sonarr
- lidarr
- deluge
- ombi
- jellyfin
- jackett
- traefik

---

```
version: '3.7'
services:
  deluge:
    image: lscr.io/linuxserver/deluge
    container_name: deluge
    restart: unless-stopped
    environment:
      - PUID=${PUID}
      - PGID=${PGID}
      - TZ=Europe/Paris
    volumes:
      - ${PATH_CONFIG}/deluge/config:/config
      - ${PATH_DOWNLOADS}:/downloads
    ports:
      - 8112:8112
      - 6881:6881
      - 6881:6881/udp
  
  jackett:
    image: lscr.io/linuxserver/jackett
    container_name: jackett
    restart: unless-stopped
    environment:
      - PUID=${PUID}
      - PGID=${PGID}
      - TZ=Europe/Paris
      - AUTO_UPDATE=true
    volumes:
      - ${PATH_CONFIG}/jackett/config:/config
      - ${PATH_DOWNLOADS}:/downloads
    ports:
      - 9117:9117

  sonarr:
    image: ghcr.io/linuxserver/sonarr
    container_name: sonarr
    restart: unless-stopped
    environment:
      - PUID=${PUID}
      - PGID=${PGID}
      - TZ=Europe/Paris
    volumes:
      - ${PATH_CONFIG}/sonarr/config:/config
      - ${PATH_SERIES}:/tv 
      - ${PATH_DOWNLOADS}:/downloads
    ports:
      - 8989:8989

  radarr:
    image: lscr.io/linuxserver/radarr
    container_name: radarr
    restart: unless-stopped
    environment:
      - PUID=${PUID}
      - PGID=${PGID}
      - TZ=Europe/Paris
    volumes:
      - ${PATH_CONFIG}/radarr/config:/config
      - ${PATH_FILMS}:/movies
      - ${PATH_DOWNLOADS}:/downloads
    ports:
      - 7878:7878

  lidarr:
    image: lscr.io/linuxserver/lidarr
    container_name: lidarr
    restart: unless-stopped
    environment:
      - PUID=${PUID}
      - PGID=${PGID}
      - TZ=Europe/Paris
    volumes:
      - ${PATH_CONFIG}/lidarr/config:/config
      - ${PATH_MUSIQUES}:/music
      - ${PATH_DOWNLOADS}:/downloads
    ports:
      - 8686:8686

  jellyfin:
    image: ghcr.io/linuxserver/jellyfin
    container_name: jellyfin
    environment:
      - PUID=${PUID}
      - PGID=${PGID}
      - TZ=Europe/Paris
    volumes:
      - ${PATH_CONFIG}/jellyfin/config:/config
      - ${PATH_SERIES}:/data/tvshows
      - ${PATH_FILMS}:/data/movies
    ports:
      - 8096:8096
      - 8920:8920
    restart: unless-stopped  
        
networks:
  seedbox:
    external: true

```

Installation de l'image Traefik
```
version: '3.7'
services:
  traefik:
    image: "traefik:v2.2"
    container_name: "traefik"
    restart: unless-stopped
    networks:
      - traefik_network
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock:ro
      - /home/traefik/traefik.toml:/traefik.toml:ro
      - /home/traefik/acme.json:/acme.json

networks:
  traefik_network:
    external: true
```
Reconnecter vous avec votre user via `su votre_user` puis tester avce la commande `sudo date`

## Sources
https://howto.wared.fr/debian-sudo/
https://wiki.debian.org/fr/sudo
