---
title: "OpenMediaVault, un NAS maison : Installation"
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
Voici le début d'une série de tutoriels sur OpenMediaVault, une solution NAS "DIY" évolutive et gratuite.


## Installation

Je pars d'une installation Debian car l'image préconfiguré ne marche pas chez moi.

Donc après avoir installé une distribution Debian, il vous suffit de vous rendre sur la documentation du site d'[OpenMediaVault](https://openmediavault.readthedocs.io/en/5.x/installation/index.html).

Lancer les commandes suivantes :
installation de gnupg.
'''
sudo apt-get install --yes gnupg
'''

Ajout de la source d'openmediavault.
'sudo nano /etc/apt/sources.list.d/openmediavault.list'

'''
deb https://packages.openmediavault.org/public usul main
# deb https://downloads.sourceforge.net/project/openmediavault/packages usul main
## Uncomment the following line to add software from the proposed repository.
# deb https://packages.openmediavault.org/public usul-proposed main
# deb https://downloads.sourceforge.net/project/openmediavault/packages usul-proposed main
## This software is not part of OpenMediaVault, but is offered by third-party
## developers as a service to OpenMediaVault users.
# deb https://packages.openmediavault.org/public usul partner
# deb https://downloads.sourceforge.net/project/openmediavault/packages usul partner
'''

Installation d'openmediavault.
(ligne par ligne)
'''
export LANG=C.UTF-8
export DEBIAN_FRONTEND=noninteractive
export APT_LISTCHANGES_FRONTEND=none
sudo wget -O "/etc/apt/trusted.gpg.d/openmediavault-archive-keyring.asc" https://packages.openmediavault.org/public/archive.key
sudo apt-key add "/etc/apt/trusted.gpg.d/openmediavault-archive-keyring.asc"
sudo apt-get update
'''
(en une seul commande)
'''
sudo apt-get --yes --auto-remove --show-upgraded \
    --allow-downgrades --allow-change-held-packages \
    --no-install-recommends \
    --option Dpkg::Options::="--force-confdef" \
    --option DPkg::Options::="--force-confold" \
    install openmediavault-keyring openmediavault
'''

A APPROFONDIR
Première demande avec SMB file 'no' et configuration SMTP 'non'

il reste une seul commande a lancer 'sudo omv-confdbadm populate'

Une fois fini il vous suffit de vous rendre dans votre navigateur puis de taper l'adresse IP de votre NAS.

Le login et mot de passe par défaut sont 'admin' et 'openmediavault'