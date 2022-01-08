---
title: "Installer LineageOS 14 sur votre tablette Amazon Fire 2015"
date: 2021-07-01
lastmod: 
draft: true

heroimg: images/articles-vierge.webp
#description: 
#keywords:

categories:
- android

series:
- android
- second vie
  
tags:
- lineageOS
- amazon
- fire
- ford
- austin
---
Installer LineageOS sur Amazon Fire 5th (ford)


Telecharger le paquet [amonet](https://forum.xda-developers.com/t/rom-unlocked-ford-austin-lineage-14-1-17-jan-2021.3962457/) disponnible dans ce post de XDA.

Pour la 5th il n'est pas obloigé d'ouvrir la tablette si vous avez la rom Amazon officiel inferieur ou egale a FireOS 5.3.2.

Sinon il faudra passer en micrologiciel 5.0.1 via adb sideload dans le mùode recuperation.

Si vous etes en OS superieu ou avec une tablette fire 7th alors il faudra shunter VOIR PHOTO XDA


pres requis :

dans un live CD ou dans linux.

sudo apt update
sudo add-apt-repository universe (pas obligatoire chez moi sur debian 11)
sudo apt install python3 python3-serial adb fastboot

>verifier que vous avez bien un cable autorisant le transfert de fichier et ps seulement l'limentation.
Assurez-vous que ModemManager est désactivé ou désinstallé :
Code:

sudo systemctl stop ModemManager
sudo systemctl disable ModemManager

Vous avezune 5th avec Fire OS inf ou egale a 5.3.2 alors il suffit d'eteindre la tablette, de la debrancher puis de lancer un terminal dans le dossier du fichier telecharge.

Lancer le sudo ./bootrom-step.sh

Il devrait maintenant dire Waiting for bootrom . 

Appuyer sur le bouton volume + (A gauche quand vous etes face a la tablette) puis brancher l'USB de la tablette au PC tout en maintenant le bouton appuyer.

Il vousd demande supprimer le court-circuit (si vous avez eu besoin de le faire) puis d'appuyer sur entrer

Une fois fini, vous devez voir sur votre tablette le logo Amazon avec ecrit en bas `=> HACKED FASTBOOT mode (0) - xuz, k4y0z` (les derniers chiffres peuvent changer)


>S'il se bloque à un moment donné, arrêtez-le et redémarrez le processus à partir de l'étape lancer le sudfo.


Lancer la commande 

sudo ./fastboot-step.sh


Il copie des choises sur votre tablette puis install TWRP (ca va trres vitre) Ilo redemarre ensuite en Recovery.

Il ne vous reste plus qu'a installer la roms Lineages OS 14.1 ou une autres.

Pour ma part j'ai mis la rom sur une carte MicroSD.

Dans TWRP aller dans install, puis select storage selectionner l microSD ouis cliquer sur le fichier de la roims.zip faites glisse rpour confirmer et le systeme s'installe

Une fois installer faite Wipe Cache/Davilk puis pour etre sur qu'il ne reste pas de trace de votre ancienne installtion faites retour (2x) (avec la fleche) puis wipe et format data, taper yes puis reboot system.

Vous voila maintenant avec une tablette qui a une seconde vie. 

## Sources 
[Unlock](https://forum.xda-developers.com/t/unlock-root-twrp-unbrick-downgrade-fire-7-ford-and-austin.3899860/)
[LineageOS 14.1](https://forum.xda-developers.com/t/rom-unlocked-ford-austin-lineage-14-1-17-jan-2021.3962457/)


