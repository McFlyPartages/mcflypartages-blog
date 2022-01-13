---
title: "Retrouver le bureau disparu après changement de fond d'écran"
date: 2022-01-13T09:04:19+01:00
lastmod: 
draft: false
socialshare: true
article-ha: false

heroimg: /images/articles-vierge.webp
description: "Retrouver l'accès au bureau, sous Debian 11, suite à un changement de fond d'écran."

categories:
- linux

series:
- debian 11
  
tags:
- debian
- rescue mode

keywords:
- debian
- rescue mode
- bureau
- fond d'écran

---

Retrouver le bureau disparu après changement de fond d'écran

La dernière fois en voulant changer le fond d'écran d'un ordinateur sous Debian 11, j'ai complètement perdu l'accès au Bureau.
Si mes souvenirs sont bons, j'essayais de me loguer, mais rien ne se lançait.

Ne désirant pas tout réinstaller, voici la manipulation effectuée.

* Redémarrer Debian
* Sélectionner `Advanced`,
* Puis `rescue mode`,
* Rentrer le mot de passe `root`,

{{< alert "Attention le verrouillage numérique est désactivé par défaut" warning >}}

Nous allons éditer le fichier de configuration de l'utilisateur dans lequel est stocké le fond d'écran utilisé.
* Ouvrir le fichier `nano /home/VOTRE_USER/.config/dconf/user`,
* Rechercher via `CTRL+W` `file:///usr/share/backgrounds/gnome/`,
* Remplacer `xxxx.xml` a la fin du lien par `wood.xml`.
* Sauvegarder `CTRL+X` puis `y`.
* Redémarrer via `reboot`.

Vous devez avoir de nouveau accès à votre bureau.