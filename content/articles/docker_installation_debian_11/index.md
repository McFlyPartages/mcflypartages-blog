---
title: "Comment installer Docker et Docker Compose sur Debian/Raspbian 11."
date: 2022-01-03
lastmod: 
draft: false
socialshare: true
article-ha: false

hero: /images/articles-vierge.webp
description: "Comment installer Docker et Docker Compose sur Debian 11 ou Raspberry Pi OS (Raspbian)."


categories:
- linux
- docker
- raspberry

series:
- docker
- debian
- raspberry
  
tags:
-  docker
-  docker compose
-  debian
-  raspbian
-  raspberry pi os

keywords:
-  docker-ce
-  docker-compose
-  debian 11
-  serveur
-  raspbian
-  raspberry pi os
-  raspberry

---
Je ne vais pas m'étendre sur le sujet, mais pour faire simple, il permet d'installer et de tester des applications sans devoir chambouler ou jouer sur la configuration brute du système.

Voici deux citations de Wikipédia.
{{< quote "Docker est une plateforme permettant de lancer certaines applications dans des conteneurs logiciels." "[Wikipédia](https://fr.wikipedia.org/wiki/Docker_(logiciel))" >}}

{{< quote "Docker est un outil qui peut empaqueter une application et ses dépendances dans un conteneur isolé, qui pourra être exécuté sur n'importe quel serveur." "[Wikipédia](https://fr.wikipedia.org/wiki/Docker_(logiciel))" >}}



Il existe deux versions de Docker :
* Docker CE pour Community Edition (celle qui nous intéresse),
* Docker EE pour Entreprise Edition.

Fin du blabla

## Installation de Docker.
Je pars du principe que vous avez déjà Debian 11 d'installé sur votre machine et que vous savez vous [connectez en SSH](../ssh_connexion/) à serveur.

{{< alert "Si vous avez déjà installé Docker il va falloir supprimer cette installation via la commande suivante `sudo apt-get remove docker docker-engine docker.io containerd runc`" info >}}

On commence par mettre à jour les paquets du système et le système lui-même.
```bash
sudo apt update && sudo apt upgrade
```

On installe les dépendances.
```bash
sudo apt install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```
Ajout de la clé GPG Docker pour Debian.
```bash
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
ou Raspbian / Raspberry Pi OS.
```bash
curl -fsSL https://download.docker.com/linux/raspbian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
Cette ligne suivante permet de choisir la version que l'on souhaite installer, nous prenons la `stable` par défaut.
```bash
echo \
 "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
 $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
Une dernière mise à jour puis l'installation de Docker.
```bash
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io
```
### Ajout d'un utilisateur.
Ajouter son utilisateur (ou un créé spécialement) au groupe `docker` puis tester votre version de Docker.
Cela permet d'éviter l'utilisation de l'user `root`, donc de sécuriser les différentes manipulations.

```bash
sudo usermod -aG docker votre_user
docker -v
```
![Ajout de l'utilisateur au groupe docker et tester la version installée](img/docker_ajout_user_test_version.png)

Docker est maintenant installé et fonctionnel.


## Installation de Portainer.
Portainer est une sorte d'interface graphique pour gérer les conteneurs Docker.
Il permet de créer des containers, et d'utiliser des fichiers Docker-compose ou Kubernetes pour créer des stacks (ensemble de conteneurs). Nous verrons cela dans d'autres articles.

Création d'un volume Docker.
```bash
sudo docker volume create portainer_data
```
Téléchargement et installation de l'image (container) Portainer
```bash
sudo docker run -d -p 8000:8000 -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```

Vérifier la version et la présence de ce dernier avec la commande `docker ps`.
![Docker PS](img/docker_ps.png)

### Première connexion.
Ouvrez votre navigateur et connectez-vous à l'interface avec `ip_de_votre_serveur:9000`
* Renseigner un  nom d'utilisateur et un mot de passe solide.
* Sélectionner `Get Started` pour se connecter à l'environnement local.
{{< gallery folder="premiere_connexion" >}}

![Page d'accueil de Portainer](img/portainer_page_acceuil.png)


## Désinstaller Docker.
Si vous souhaitez supprimer Docker (cela supprimera tous les containers installés)
```bash
sudo apt remove docker docker-engine docker.io containerd runc
```

## Conclusion.

Vous avez à présent la possibilité de tester n'importe quelle application sans devoir toucher un seul fichier de votre système.


## Sources.
* https://docs.docker.com/engine/install/debian/
* https://docs.portainer.io/v/ce-2.6/start/install/server/docker/linux