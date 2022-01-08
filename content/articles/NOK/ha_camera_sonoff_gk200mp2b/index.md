---
title: "Intégrer la camera Sonoff GK-200MP2-B ou C dans Home Assistant"
date: 2021-12-20
lastmod: 
draft: true

heroimg: /images/articles-vierge.webp
description: 


categories:
- home assistant
- domotique
- test matériel

series:
- home assistant
- test matériel
  
tags:
- sonoff
- caméra
- GK-200-MP2-C
- GK-200-MP2-B
 
keywords:
- sonoff
- caméra
- GK-200-MP2-C
- GK-200-MP2-B
---

Cela fait déja un bout de temps que j'ai cette camera Sonoff qui est un matériel grand publique , peu cher (environ 30 euros) et de bonne qualité.

Mais ce aui est surtout intéressant, c'est la possibilité de l'utiliser sans le cloud et d'y ajouter le protocole ONVIF non présent d'origine.

Bien sur pour cela il faut un hack, mais ne partez pas, c'est un simple transfert sur carte SD.

Voici la procédure.

## Connexion au réseau local.
Pour cela pas de mystère, vous êtes obligé de télécharger l'application [eWeLink - Smart Home sur le Play Store](https://play.google.com/store/apps/details?id=com.coolkit), 

>Comme l'application Tuya, vous n'êtes pas obligé de vous créer un compte, il y a une version test qui suffit a l'ajout de votre caméra sur le réseau.

>La camera ne peut s'associer que via le son, toutes les autres méthodes n'ont pas marchés pour moi.


![Ewilink App](images/ewelinkapp.jpg)![Ewilink App](images/ewelinkapp1.jpg)
![Ewilink App](images/ewelinkapp2.jpg)
![Ewilink App](images/ewelinkapp3.jpg)
![Ewilink App](images/ewelinkapp4.jpg)
![Ewilink App](images/ewelinkapp5.jpg)
![Ewilink App](images/ewelinkapp6.jpg)
![Ewilink App](images/ewelinkapp7.jpg)
![Ewilink App](images/ewelinkapp8.jpg)
![Ewilink App](images/ewelinkapp9.jpg)
![Ewilink App](images/ewelinkapp10.jpg)

Une fois que votre caméra est connectée, il vous faut récupérer l'adresse IP.
Pour cela, deux méthodes :
* Via l'interface de votre routeur,
* Via l'application eWelink (Cliquer sur votre caméra->...(en haut a gauche)->Plus de paramètres->RTSP)

## Ajout du hack
La sopurce du hack se trouve [ici](https://github.com/roleoroleo/sonoff-hack)


