---
title: "Installer le boitier Argon One sur Home Assistant et le controler"
date: 2021-07-01
lastmod: 
draft: true
layout: home-assistant
hero: /images/articles-vierge.webp
description: "Ajouter et commander son boitier Argon One M.2 avec Home Assistant"

socialshare: true
article-ha: true

categories:
- domotique
- home assistant

series:
- home assistant
  
tags:
- argon
- Argon One Add-on
- HassOS I2C Configurator
- add-on ha

keywords:
- Argon
- Argon One Add-on
- HassOS I2C Configurator
- add-on ha
---



{{< alert "Message **danger**" success >}}
{{< quote "Message **citation**" "artiste **anonyme**" >}}
{{< gallery folder="infos" >}}


Pré requis :
* Boitier Argon One ou Argone ONE extension
* Activer mode Avancé (pour installer l'add-on Terminal & SSH)


### Activer l'I2C
@adamoutioer nous a concocter un add-on simplifiant grandement l'activation de la liason I2C.

IMAGE addon_Hassos_I2C_Configurator.png

Il faut ajouter le `repositories` puis installer l'add-on

Dans Home Assistant, cliquer sur `Supervisor`-> `Add-on Store` -> `…` bouton (en haut à droite)-> `Repositories`. 
Ajouter ce `repositories`.
[![Open your Home Assistant instance and show the add add-on repository dialog with a specific repository URL pre-filled.|197x28](https://camo.githubusercontent.com/9e0c22cf56020b6ad057d06b87690b7a3ae14d8ada8b16a51abf6e8ab97df755/68747470733a2f2f6d792e686f6d652d617373697374616e742e696f2f6261646765732f73757065727669736f725f6164645f6164646f6e5f7265706f7369746f72792e737667)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Fadamoutler%2FHassOSConfigurator)

Puis installer l'add-on **HassOS I2C Configurator**

Il n' y a pas de configuration juste le besoin de désactiver le `Protection Mode`

IMAGE protection_mode_ha.gif

### Sources
[Argon One Add-on](https://community.home-assistant.io/t/argon-one-active-cooling-addon/262598)
[Sujet HA Off addon Hassos I2C Configurator](https://community.home-assistant.io/t/add-on-hassos-i2c-configurator/264167)
[GitHub Hassos I2C Configurator](https://github.com/adamoutler/HassOSConfigurator)