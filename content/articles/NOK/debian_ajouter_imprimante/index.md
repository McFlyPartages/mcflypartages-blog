---
title: "Ajouter votre imprimante sur Debian 11"
date: 2021-07-01
lastmod: 
draft: true

hero: 'images/articles-vierge.png'
#description: 
#keywords:

categories:
- linux
- informatique

series:
- Debian 11
  
tags:
- bullseye
- debian
- imprimante
---

Sur debian 11, je ne sais pas pourquoi, mais il n'y a pas de quoi configurer une imprimante par défaut, il faut donc mettre les mains dans le cambouis.

Nous allons essayer par CUPS
```
sudo apt install cups

```

Maintenant, vous avez acces à l'ajout d'imprimante.

Démarer votre imprimante puis :

* cliquer sur activité,
* rechercher `imprimnte`,
* cliquer sur `imprimante`,
* deverouiller avec le mot de passe de votre user,
* Attendez quelques instanat votre imprimante devrait apparaitre.
* * Si elle n'appatait pas, cliquer sur le bouton `ajouter une imprimante`,
* * Selectionner votre imprimante

## Sources
https://wiki.debian.org/CUPSPrintQueues


