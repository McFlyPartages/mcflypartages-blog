---
title: "Comment installer Docker et Docker Compose sur un Raspberry Pi."
date: 2021-06-30
lastmod: 
draft: true

hero: images/articles-vierge.png
#description: 
#keywords:

categories:
- raspberry
- docker

series:
- docker
  
tags:
-  raspberry OS
---

Je pars du principe que vous avez déja installé Raspberry Pi OS sur votre Raspberry est changé votre mot de passe.

Connectez vous en SSH a votre Raspberry via la commande suivante puis saisissez votre mot de passe.


```
ssh pi@ip_de_votre_raspberry

```

## Installation de Docker
puis une petite mise à jour
```
sudo apt-get update && sudo apt-get upgrade
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

```
sudo usermod -aG docker pi
docker -v
```

# Installation de Docker Compose

```
sudo apt-get install python3 python3-pip python3-distutils python3-dev libffi-dev libssl-dev
sudo pip3 install docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose -v
```

# Installation de Portainer
```
sudo docker pull portainer/portainer-ce:linux-arm

docker run -d -p 8000:8000 -p 9443:9443 --name portainer \
    --restart=always \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v ~/portainer/config:/data \
    portainer/portainer-ce:linux-arm
```
connectez vous sur `ip_de_votre_rpi:9443`


>Attention : Lors de vos recherche sur docker Hub, il faut bien verifier que les images son comptatible ARM.
## Sources
https://howto.wared.fr/debian-sudo/
https://www.framboise314.fr/installer-docker-sur-raspberry-pi/
https://hub.docker.com/r/portainer/portainer-ce/tags
