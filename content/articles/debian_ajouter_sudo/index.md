---
title: "Retrouver le sudo dans Debian 10 et 11"
date: 2021-12-19
lastmod:
draft: false
socialshare: true
article-ha: false

hero: /images/articles-vierge.webp
description: "Comment retrouver la commande sudo sur Debian 10 Buster et 11 Bullseye."

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
Comme vous avez dû le remarquer depuis la version 10 de Debian nommée Buster, une commande avec `sudo` renvoie que `sudo` est introuvable. Et oui depuis cette version, Debian n'installe plus `sudo` par défaut. 

Voici la méthode pour retrouver cette commande.

## Installation.
Dans un terminal, [connectez-vous en SSH](./../connexion_ssh/)

Passer en `root` (si vous êtes connecté via un utilisateur) puis procéder à l'installation avec les commandes suivantes :

```bash
su root
apt install sudo -y
```
![Installation de sudo](img/install_sudo.png)

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

![Ajout et test de la commande sudo avec l'utilisateur](img/ajout_test_utilisateur_sudo.png)

## Conclusion

Vous voilà avec la possibilité de lancer des commandes en administrateur sans pour cela changer d'user en permanence.

Cet article est plus un mémo qui me permet de ne pas devoir rechercher en cas de doute.

## Sources
* [HowToWared](https://howto.wared.fr/debian-sudo/)
* [Debian.org](https://wiki.debian.org/fr/sudo)