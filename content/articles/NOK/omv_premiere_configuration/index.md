---
title: "OpenMediaVault : Premiere configuration"
date: 2021-06-30
lastmod: 
draft: true

heroimg: images/articles-vierge.webp
#description: 
#keywords:

categories:
- informatique
- linux
- open media vault

series:
- OMV
  
tags:
- nas
- serveur
---

Nous venons d'installer OpenMediaVault et nous pouvons nous y connecter avec les identifiants par défaut qui sont 'admin' et 'openmediavault'.

Sans surprise nous allons changer cela mais commençons par mettre à jour OpenMediaVault.

## Mise à jour
Il vous suffit d'aller dans 'Système' puis 'Gestionnaire de mises à jour'.

Dans l'onglet 'Paramètres' cocher 'Mises à jour maintenues par la communauté.'.
Retourner dans l'onglet 'Mises à jour' puis cliquer sur 'Vérifier'.
Sélectionner tous les paquets ou seulement ceux que vous souhaitez mettre à jour puis cliquer sur 'Installer'.

Une fenêtre popup s'ouvre et affiche le suivi de la mise à jour.

## Changer le mot de passe
Pour plus de sécurité, il est obligatoire de changer le mot de passe.

Rendez-vous dans 'Système', 'Paramètres généraux' puis l'onglet 'Sécurité Administrateur'.
Rentrer votre nouveau mot de passe puis cliquer sur 'Enregistrer'.

## Gestion des disques
Rendez-vous dans 'Stockage'.
Vous avez accès à plusieurs sous-menus :
### Disques
Permet de lister vos disques présents. Mais aussi de :
* Les formater de manière rapide ou sécurisé.
* Gérer les paramètres d'énergie, acoustique, temps de ralentissement et la mise en cache.

### S.M.A.R.T
>S.M.A.R.T est une technologie disponible sur tous les disques durs permettant de surveiller et collecter en permanence des informations sur la santé du disque dur.

Onglet 'Paramètres' vous permet d'activer la surveillance, son intervalle et dans quel mode le scan peut être lancé. Personnellement j'ai choisi le mode 'Standby' recommandé.

Il est possible de régler des seuils de températures permettant d'être notifié.

Onglet 'Tests programmés' vous permet de lancer des tests régulièrement. Je ne l útilise pas alors je ne peux pas vous en dire plus.

### Gestion du RAID
Onglet 'Paramètres' vous permet d'activer la surveillance, son 
