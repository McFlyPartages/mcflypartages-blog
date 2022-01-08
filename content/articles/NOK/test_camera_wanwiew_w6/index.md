---
title: "Test de la Caméra Wanswiew W6 et intégration dans Home Assistant"
date: 2021-07-01
lastmod: 
draft: true

heroimg: images/articles-vierge.webp
#description: Protocole ONVIF & Abordable
#keywords:

categories:
- domotique
- home assistant
- test matériel

series:
- home assistant
- test matériel
  
tags:
- caméra
- wanswiew
- w6
- onvif
---

Voici mon premier test matériel qui je l'espère ne sera pas le dernier.

>Avant toute chose : Je ne suis pas sponsorisé pour ce test, c'est du matériel que j'ai acheté moi même et pour moi.

Je cherchais une camera extérieur, peu cher, compatible simplement avec Home Assistant et si possible sans cloud. Je me suis donc naturellement tourné vers le protocole ONVIF pour la facilité d'integration, mais par contre je pense qu'un produit sans cloud en 2021, il v falloir abandonner (pour un prix raisonnable).


>**Protocole ONVIF :** C'est un protocole permettant de normaliser le fonctionnement d'une camera d'un constructeur à l'autre.

>**Déconnecter le cloud :** Pour se passer du cloud en 2021 deux solutions peuvent exister :
>* Flasher l'appareil avec un firmware alternatif,
>* Couper l'accès internet a ces appareils. 
>Nous y reviendrons peut être dans un autre article.

## Caractéristiques
* Vidéo FHD 1080P,
* Vision nocturne,
* Audio bidirectionnel,
* Accès à distance,
* IP66 : Protection intégrale contre les poussières et contre les forts jets d'eau de toutes directions,
* Connexion Wi-Fi 2.4 GHz & Ethernet,
* Protocole RTSP et ONVIF
* Stockage Cloud et **SD ???**,
* Fonctionne avec Alexa,
* Alimentation 220v (sans terre) d'environ 2,40m,
* Connectique (indissociable de la caméra) d'environ 35cm (Alim, Reset, Ethernet).

## Déballage
Pour le déballage rien de particulier, la camera est fourni avec sont support orientable et de lots de fixation pour béton.
Il y a aussi de quoi rendre étanche la connexion via ethernet

>**Ethernet :** Seul un cable fait maison sans habillage passera dans le capuchon étanche.

## Application
Sans grosse surprise, il est obligatoire de passer par l'application pour connecter votre camera a votre réseaux **Wi-Fi Ethernet???**

L'application a utiliser est [Wansview Cloud](https://play.google.com/store/apps/details?id=net.ajcloud.wansviewplus&hl=fr).
Vous êtes obligé de créer un compte mais vous pouvez le supprimer facilement via l'application.

## Utilisation

Detection de mouvement bonne plus de XXm
Il est possible de sélectionner une zone pour la detection de mouvements.
En sensibilité normale elle détecte les moustique et autres insecte volant.



## Integration Home Assistant
L'ajout dans Home Assistant se fait sans difficulté grave a l'integration native "ONVIF".

Il vous suffit de vous rendre dans 'configuration' 'integration' '+' puis cherche 'ONVIF'.

Après une exploration de votre réseau, l'integration devrait trouver votre camera.

Il vous suffit de la sélectionner, de rentrer login et mot de passe configurés dans l'application puis de valider.

Votre camera est intégré.

## Sources
* [Documentation Officiel Home Assistant (EN)](https://www.home-assistant.io/integrations/onvif/)

