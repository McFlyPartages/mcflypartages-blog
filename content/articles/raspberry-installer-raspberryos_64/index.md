---
title: "Installer Raspberry OS 64bits (Raspbian) sur Raspberry Pi."
date: 2022-03-05
lastmod: 
draft: true
socialshare: true
article-ha: false

heroimg: /images/articles-vierge.webp
description: 

categories:
- raspberry
- debian
- linux

series:
- raspberry
- debian
  
tags:
- raspbian
- raspberry os

keywords:
- raspbian
- raspberry os
- 64bits
- linux
- raspberry pi

---

{{< gallery folder="infos" >}}

HA
{{< ha/userha "user" haoff >}}
{{< haautoconfig bp "url" >}}
Simple lien : 
{{< forumhacf "lien_vers_forum" "Titre_du_post">}} 
Multi liens : 
{{< multiforumhacf >}}
    {{< forumhacf "lien_vers_forum" "Titre_du_post">}}
    {{< forumhacf "lien_vers_forum" "Titre_du_post">}}
{{< /multiforumhacf >}}


Enfin, Raspberry Pi OS 64 Bits est disponnible officielement, il etait temps.

**Quelles differences pour nous ?**
Beaucoup, car avec l'arrivée du Raspberry Pi 4 et ses 4 ou 8Go de RAM la version officelle en 32 Bits ne permettait pas d'exploiter pleinement notre Single Board Computer (SBC) plus communement appelé nano ordinateur.
Alors oui, les 4 ou 8 Go etaient reconnus par la version 32bits via un systeme de memoire etendu, mais cela ne permet pas a une application seul d'utiliser plus de 3Go de RAM. Ok c'est assez rare sur une Raspberry.

N'avoir qu'une version 32 Bits bride le devellopement, car il y a de moins en moins de systeme en 32 bits et donc beaucoup de logiciels ou applications sont développés uniquement en 64 bits (ce qui oblige les communautés de devellopeurs sur Raspberry a forcer le maintient de la version 32 Bits).

Allez passons a l'installation.

{{< alert ¨La version 64 Bits est compatible avec plusieur versions du Raspberry (4, 3A+, 3B, 3B+, 400,CM3, CM3+, CM4, Zero 2 W).¨ info >}}

**Materiels :**
* Raspberry Pi (+ Alimentation),
* Carte Micro SD,
* [Balena Etcher](https://www.balena.io/etcher/) ou [Raspberry Pi Imager](https://www.raspberrypi.com/software/)

{{< alert ¨Pour ma part j'utilise Balena Etcher car il me sert aussi pour d'autres images¨ info >}}

## Récuperer l'image 64 Bits.
Pour cela rien de compliqué, rendez vous sur le [site officiel Raspberry Pi](https://www.raspberrypi.com/software/operating-systems/#raspberry-pi-os-64-bit)(liens direct vers l'OS en 64Bits)

Sinon une fois arrivé sur le site :
* menu `software`,
* Cliquer sur `See all download options`. 

![Raspberry OS 64 Bits](img/raspberry_os_64_bits.png)

* Récuperer la version Lite (pour un serveur).
* Transferer l'image vers votre MicroSD [via Balena Etecher](??? ARTICLE BALENA ETCHER) ou Raspberry Pi Imager.


