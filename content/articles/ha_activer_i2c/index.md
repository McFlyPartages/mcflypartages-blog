---
title: "Activer l'I2C sur Home Assistant OS"
date: 2022-02-02
lastmod: 
draft: false
hero: /images/articles-vierge.webp
description: "Comment activer l'I2C sur Home Assistant OS sur un Raspberry Pi via l'add-on HAOS I2C Configurator de Adamoutier"

socialshare: true
article-ha: true

categories:
- domotique
- home assistant

series:
- home assistant
  
tags:
- i2c
- HassOS I2C Configurator
- add-on ha
- HAOS
- supervised
- Raspberry Pi

keywords:
- i2c
- HassOS I2C Configurator
- add-on ha
- HAOS
- supervised
- Raspberry Pi
---

{{< quote "I2C (Inter-Integrated Circuit) est un bus informatique qui a émergé de la « guerre des standards » lancée par les acteurs du monde électronique. Conçu par Philips pour les applications de domotique et d’électronique domestique, il permet de relier facilement un microprocesseur et différents circuits, notamment ceux d’un téléviseur moderne : récepteur de la télécommande, réglages des amplificateurs basses fréquences, tuner, horloge, gestion de la prise péritel, etc. " "[Wikipédia](https://fr.wikipedia.org/wiki/I2C)" >}}

En gros il a l'avantage de pouvoir faire passer plusieurs capteurs ou infos sur un nombre de fils restreint et c'est le protocole qui gère l'ordre d'envoi des capteurs pour éviter que deux capteurs parle en même temps. Cela a l'avantage de ne nécessiter que deux câbles :
* Un SDA (Serial Data) pour les datas,
* Un SCL (Serial Clock) pour l'horloge plus bien sur l'alimentation.

Il est présent aussi sur certain boitier de Raspberry (Ex: Argon One) mais vous pouvez aussi vous en service pour récupérer les infos d'un montage sur votre Raspberry exécutant Home Assistant OS.


### Activer l'I2C
{{< ha/userha "adamoutier" haoff >}} nous a concocté un add-on simplifiant grandement l'activation de la liaison I2C, nommé HAOS i2C Configurator. Il est disponible à partir d'[un dépôt externe](#URL ARTICLE ADDON).

![Add-on HAOS i2C Configurator](img/addon_haos_i2c_configurator.png)

* Ajouter le dépôt externe via l'image ci-dessous ou manuellement. Adresse du dépôt https://github.com/adamoutler/HassOSConfigurator
LIENS HA AJOUT DEPOT
* Recharger les dépôts ou faites `F5`,
* Installer l'add-on HAOS i2C Configurator,
* Désactiver le `Protection Mode`
![I2C Configurator](img/haos_i2c_confgurator_parametre.png)
* Une alerte apparait, c'est normal,
![Alerte Protection Mode](img/mode_protection_alerte.png)
* Cliquer sur `DEMARRER`.
* Vérifier les logs de l'add-on et du superviseur.
{{< gallery folder="log1" >}}
* Redémarrer deux fois l'hôte.
![Log de l'add-on après](img/log_addon_apres_redemarrage.png)
* Vérifier la présence d'I2C dans la liste de matériel `Configuration'-> `Modules complémentaires, Sauvegardes et Superviseur` -> Onglet `Système` -> Fenêtre `Host` `...` en bas à droite-> `Matériel`.
![Présence I2C dans la liste des matériels](img/liste_materiel_i2c.png)

Vous pouvez redémarrer l'add-on pour confirmer.
![Confirmer via l'add-on](img/log_relance_addon_i2c_configurator.png)

Vous pouvez maintenant désinstaller l'add-on.

### Sources
* [Sujet HA Off addon Hassos I2C Configurator](https://community.home-assistant.io/t/add-on-hassos-i2c-configurator/264167)
* [GitHub Hassos I2C Configurator](https://github.com/adamoutler/HassOSConfigurator)