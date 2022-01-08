---
title: "Comment installer Arduino sur Debian 11"
date: 2021-06-30
lastmod: 
draft: true

hero: 'images/articles_vierge.webp'
#description: 
#keywords:

categories:
- arduino
- linux

series:
- debian 11
- arduino
  
tags:
- bullseye
---

Arduino est un logiciel permettant de programmer sur les arduino mais pas seulement, il peut aussi programmer les esp8266, esp32, esp01 etc etc.

Nous allons voir ici comment installer le logiciel Arduino sur Linux.

## En graphique
Rendez vous sur le site onglet software [Arduino.cc onglet software](https://www.arduino.cc/en/software) puis telecharger la version correspondante a votre systeme d'exploitation (ici [Linux 64bits version 1.8.16](https://downloads.arduino.cc/arduino-1.8.16-linux64.tar.xz) au moment ou j'écris)

![Telechargement Arduino](images/arduino_telechargement "Telechargement Arduino")


Une fois téléchargé rendez vous dans le dossier de téléchargement puis ouvrir un `terminal`.

```
tar xf arduino-1.8.16-linux64.tar.xz
```
Rendez vous maintenant dans le dossier fraîchement dézippé  avec la commande suivante
`cd arduino-1.8.16` 
puis lancer la commande suivante
```
sudo ./install.sh
```
![arduino install](images/arduino_install_sh "Installation Arduino")

Vous devez vous retrouver avec le programme Arduino dans `applications` `programmation` `arduino IDE`.

## En ligne de commande
>Cette méthode a le mérite d'installer les dépendances nécessaires en plus.

Mise à jour des paquets
```bash
sudo apt update
```
puis installation
```bash
sudo apt install Arduino
```

## Sources
[Arduino.cc](https://www.arduino.cc)
[How to install IDE on Debian](https://vitux.com/how-to-install-arduino-ide-on-debian-10/)
## Quelques sources FR
[Arduino-France](https://www.arduino-france.com)
[Forum Arduino (partie FR)](https://forum.arduino.cc/c/international/francais/49)
