---
title: "Retrouver le sudo dans Debian 10 et 11"
date: 2021-12-19
lastmod: 
draft: true

hero: /images/articles-vierge.webp
description: Comment retrouver la commande sudo sur Debian 10 Buster et 11 Bullseye.

categories:
- linux

series:
- Debian 11
  
tags:
- bullseye
- buster
- debian

keywords:
- sudo
- debian
- bullseye
- buster
---
Comme vous avez dû le remarquer depuis la version Debian 10 Buster, une commande avec `sudo` renvoie que `sudo` est introuvable. Et oui depuis cette version, Debian n'installe plus `sudo` par défaut. 
Voici la méthode pour retrouver cette commande.

## Installation.
Passer en `root`  puis procéder à l'installation avec les commandes suivantes :
```bash
su root
apt-get install sudo -y
```

## Ajout d'un utilisateur au groupe `sudo`.
```bash
usermod -aG sudo votre_user
```
### Tester
Reconnecter vous avec votre utilisateur puis afficher la date.
```bash
su votre_user
sudo date
```

## Conclusion
Cet article est plus un mémo qui me permet de ne pas devoir rechercher en cas de doute.

## Sources
* [HowToWared](https://howto.wared.fr/debian-sudo/)
* [Debian.org](https://wiki.debian.org/fr/sudo)