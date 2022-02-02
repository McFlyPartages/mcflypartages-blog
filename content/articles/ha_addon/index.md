---
title: "Installer un add-on officiel ou non officiel sur Home Assistant"
date: 2022-02-02
lastmod: 
draft: false
layout: home-assistant
hero: /images/articles-vierge.webp
description: "Comment ajouter un add-on (plugin ou extension) sur Home Assistant via le store officiel et via un dépôt externe."

socialshare: true
article-ha: true

categories:
- domotique
- home assistant

series:
- home assistant
  
tags:
- add-on
- officiel
- externe
- HAOS

keywords:
- add-on
- extension
- plugin
- haos
- store officielle
- externe
---
Les add-ons permettent d’ajouter des fonctions, services ou autres à votre Home Assistant. Des services très connus et reconnus (comme Node-Red, Grafana, InfluxDB, DuckDNS, etc.) sont déjà presque configuré pour communiquer simplement avec votre système domotique.

Il existe deux types d’extensions :
* Les officielles : reconnues officiellement par Home Assistant,
* Les non-officielles : nécessitant l'ajout du dépôt GitHub en manuel.

L'installation des extensions étant toujours la même, voici les différentes méthodes.

{{< alert "Home assistant a simplifié la chose en mettant à disposition des développeurs un script générant un bouton (pour les BluePrint, Dépots, etc) qui, d'un simple clique, fait les actions à votre place. Cela nécessite simplement de saisir l'adresse de votre instance. ![Bouton Import Dépôt](img/repository_import.svg), ![Bouton Import BluePrint](img/blueprint_import.svg)""info" >}}

## Extension Officielle.
Pour les extensions officielles, il n'y a rien de compliqué.

{{< gallery folder="ajoutAddonOff" >}}

Dans Home Assistant, cliquer sur `Configuration`-> `Modules complémentaires, Sauvegardes et Superviseur` -> `Boutique des modules complémentaires`.
* Rechercher l'add-on,
* Cliquer dessus,
* Puis `INSTALLER`
![Exemple d'add-on avec DuckDNS](img/addon_duck_dns.png)

Les add-ons sont quasiment tous fait pareil.
Une fois installé vous avez quatre onglets en haut.
* **Info** : Permet de contrôler l'add-on et donne une description.
* **Documentation** : Explique son fonctionnement et ses réglages possibles.
* **Configuration** : Permet de configurer l'add-on,
* **Journal** : Vous donne les logs sur le fonctionnement de l'add-on.

Un exemple en image avec l'add-on DuckDNS.
{{< gallery folder="addonDuckDns" >}}

## Extension non officielle.

Les extensions non officielles permettent aux développeurs de mettre à disposition leur travail sans forcément attendre une validation officielle.
Cela permet de rendre Home Assistant encore plus extensible.

Pour ajouter un add-on non officiel il va falloir ajouter un nouveau dépôt dans la boutique des modules complémentaires.

Dans Home Assistant, cliquer sur `Configuration`-> `Modules complémentaires, Sauvegardes et Superviseur` -> `Boutique des modules complémentaires` ->`...` en haut à droite-> `Dépôts`. 

* Ajouter le lien du dépôt,
* Rafraichir la page via `F5` ou via `Rechercher des mises a jour` dans les `...` en haut à droite.
* Chercher maintenant l'add-on voulu et `INSTALLER`.

{{< alert "Le fonctionnement est identique à un add-on officiel." info >}}

{{< gallery folder="ajoutNouveauDepot" >}}

## Conclusion
Nous venons de mettre à disposition de notre instance une multitude de possibilités.

Nous verrons par la suite quelques add-ons indispensables.

{{< forumhacf "https://forum.hacf.fr/t/comment-installer-un-add-on-officiel-et-non-officiel/2071" "Comment installer un add-on officiel et non officiel" >}} 