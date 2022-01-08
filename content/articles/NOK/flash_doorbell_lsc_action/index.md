---
title: "Comment flasher la sonette LSC de chez Action et l'integrer a Home Assistant"
date: 
lastmod: 
draft: true

heroimg: images/articles-vierge.webp
#description: 
#keywords:

categories:
- home assistant

series:
- home assistant
  
tags:
- lsc
- doorbell
- action
- flash
---

blablblablbambala


Cette article est en gros une traduction d'un [fils de discussion GutHub ici](https://github.com/guino/BazzDoorbell/issues/2).

>J'ai suivi directement la [méthode ici](https://github.com/guino/BazzDoorbell/issues/13) qui permet de passer outre l'utilisation permanante de la carte SD mais qui n'est pas compatible avec toutes les versions de firmware.

Il vous faut récuperer [l'archive zip ici](https://github.com/guino/BazzDoorbell/files/5792854/ppshack2.zip)

### Ajouter votre sonette dans l'application Tuya.

Malheureusement , il faut obligatoirement passer par l'application pour pouvoir connecter la sonette a votre Wi-Fi.
Pour ma part j'utilise une [vielle tablette sous Lineage OS](../NOK%20android_lineageos_amazon_fire/index.md)(evite le pistage et le rapatriement des contactes) pour installer toutes les applications officielles en passant par le [store alternatif Aurora (Site Officiel)](https://gitlab.com/AuroraOSS/AuroraStore) ou via [F-Droid](https://f-droid.org/en/packages/com.aurora.store/) permettant l'acces au store Google sans le pistage.

>Une mise a jour vous seras surement proposé, je vous conseil de ne pas la faire cela n'apporte rien aprt, peut etre l'impossibilité d'effectuer le hack.

>Je fais, personnellement, peu de mise a jour sur les apareils que je ne veux pas utiliser avec le cloud le temps qu'un hack arrive.

### Récuperer l'adresse IP
Une fois connecté récuperer l'adresse IP de votre sonette, malheuresement la seul adresse IP fournit dans les paramettres de l'application est l'adresse externe (votre IP publique) et non l'adresse interne.

Donc il vous faut vous connecter a l'interface de votre routeur (souvent 192.168.0.1, 192.168.0.1, 192.168.1.254, 192.168.0.254).
Chercher un appareil sous un nom composé de chiffres. (ex : 060759444)

### Verifier le firmware.
Pour verifier la version du firmware installé sur votre appareil, il vous sufit de taper cette commande dans votre navigateur.
`http://admin:056565099@192.168.X.X/devices/deviceinfo`

>N'oubliez pas de repmplacer `192.168.X.X` part l'IP de votre sonette.

Vous devez avoir cela qui s'affiche (j'ai modifier des valeurs dans le doute.)

```
devname	"Smart Home Camera"
model	"Bell 8S"
serialno	"060759444"
softwareversion	"2.9.6"
hardwareversion	"BE8S_H1_V10_433"
firmwareversion	"ppstrong-c51-tuya2_lcs-2.9.6.20200628"
authkey	"HHBQXGDvFs51JQajt8OpCcETwLd5hlL57"
deviceid	"pp547b574f1aca86fb2d"
identity	"MR2007147859642153"
pid	"aaa"
WiFi MAC	"d4:d2:a6:b1:b4:5d"
```

### Faire une sauvegarde de la memoire.
>Fonctionne vec le firmware 2.9.x uniquement.

* Brancher votre carte Micro SD sur une machine linux (un live peut suffire)
* Connecter vous en root `sudo su`
* Determiner le nom de votyre carte SD `lsblk`, le resultat doit etre mmcblkX ou sdX.
* Effacer la carte SD `fdisk /dev/sdX` 
* puis `o` (la lettre) 
* puis `n` puis `p` 
* partition `1` 
* Valeur du début `32769` pour le premier secteur, puis laisser par defaut sur le dernier en tapant `entrée`.
* Taper `w` pour ecrire.

![Préparation de la carte](images/preparation_carte_sd.png)

* Verifier le partitionnage `fdisk -l /dev/sdX`, la dernière ligne de la sortie devrait montrer /dev/mmcblkXp1 ou /dev/sdX1 et sous 'Start' il devrait y avoir 32769 confirmant l'opération précédente.

![Vérifier la préparation](images/verifier_preparation_carte_sd.png)

* Formater la partition via `mkfs.vfat /dev/sdc1` NOTER bien le chiffre a la fin.
![Formater Carte SD](images/formater_carte_sd.png)

Si vous avez un firmware 2.9.x, dézippez et copiez ce fichier [ppsMmcTool.txt](https://github.com/guino/BazzDoorbell/files/5726163/ppsMmcTool-getflash.zip) à la racine de la carte SD.

* Récupération du frimware `dd if=/dev/sdc of=flash.bin skip=1 bs=512 count=32768`, votre fichier `flash.bin` sera envoyé vers `Dossier personnel` et fait environ 16Mo.
![Récuperation Firmware](images/recuperation_firmware.png)

* Verifier le firmware via binwalk `binwalk -M -e flash.bin` (pour installer binwalk `apt install binwalk`). Vous devez voir u-boot, uImage et cramfs/jffs ainsi que d'autres.
  
### Manipulations

>La partie qui suit est un copier coller traduit du [Github officiel](https://github.com/guino/BazzDoorbell/issues/2) pour que vous puissiez avoir la manip en fonction de votre firmware.

Pour le firmware 2.7.x vous devez utiliser les informations sur ce projet à la place : https://github.com/guino/Merkury720.

Note spéciale pour le firmware 2.9.0 : ce firmware est un peu plus délicat pour faire fonctionner RTSP (mjpeg/snap fonctionnent de la même manière), donc si vous avez cette version, vous devez utiliser le [#13](https://github.com/guino/BazzDoorbell/issues/13) avec les fichiers/étapes fournis par @DanTLehman ici : https://github.com/DanTLehman/orion_sc008ha.

Pour 2.9.x, vous devriez pouvoir utiliser les étapes ici ou dans [#13](https://github.com/guino/BazzDoorbell/issues/13) (les deux méthodes devraient fonctionner).

Note spéciale pour le firmware 2.10.0 : Ce firmware (et les plus récents) ont le port 80 fermé par défaut -- donc pour utiliser les liens http://admin:05656... ci-dessous, vous devez `CLIQUER DROIT` sur ce lien : https://github.com/guino/Merkury720/raw/main/ppsFactoryTool.txt sélectionner `Enregistrer sous...` et enregistrer ce fichier à la racine de la carte SD. EDITER le fichier (évitez de copier/coller son contenu) et modifiez uniquement le ssid et le mot de passe car le fichier nécessite un format spécifique pour fonctionner. Lorsque l'appareil détecte le fichier (dans le bon format), il déconnecte et reconnecte le wifi (au ssid spécifié) et ouvre le port 80 pour que les liens http://admin:05656... fonctionnent.

Note spéciale pour le firmware 4.0.x : Ce firmware (et les plus récents) ont le port 80 fermé par défaut -- donc pour utiliser les liens http://admin:05656... ci-dessous vous devez `CLIQUER DROIT` sur ce lien : https://github.com/guino/Merkury720/raw/main/ppsFactoryTool.txt sélectionner `Enregistrer sous...` et enregistrer ce fichier à la racine de la carte SD. EDITER le fichier (évitez de copier/coller son contenu) et modifiez uniquement le ssid et le mot de passe car le fichier nécessite un format spécifique pour fonctionner. Lorsque l'appareil détecte le fichier (dans le bon format), il déconnecte et reconnecte le wifi (au ssid spécifié) et ouvre le port 8090 pour que les liens http://admin:05656... fonctionnent mais vous devez ajouter :8090 à chaque URL, par exemple : http://admin:056565099@192.168.x.x:8090/devices/deviceinfo.


Maintenant pour ma part j'ai procéder avec la méthode sans carte SD [#13](https://github.com/guino/BazzDoorbell/issues/13) (les deux méthodes devraient fonctionner)

### Procédure

Lancer la commande suivante :
`http://admin:056565099@ip/proc/self/root/etc/init.d/S90PPStrong`

Vous devez avoir :
```
MTDNUM=`cat /proc/cmdline | sed 's/.*ppsAppParts=\([0-9]\).*/\1/'``

# Débogage
MTDNUM=5
```

>Si la ligne `MTDNUM=5` et commenté (donc `#MTDNUM=5`) alors les deux methodes marcheront (avec ou sans carte SD).

Lancer la commande suivante :
`http://admin:056565099@192.168.XXX.XXX/proc/cmdline`

Vous devez avoir ce genre de ligne 
```
mem=37M console=ttyAMA0,115200n8 mtdparts=hi_sfc:192k(bld)ro,64k(env)ro,64k(enc)ro,64k(sysflg)ro,3136k(sys),4352k(app),320k(cfg) ppsAppParts=5 ppsWatchInitEnd
```
Copier cette ligne car elle va être utile pour la suite (et pour revenir au parametres d'origine).

>Si vous n'obtenez aucune réponse, ou une réponse très différente, arrêtez maintenant, il y a des chances que vous utilisiez la mauvaise IP ou que cela ne fonctionne pas pour votre appareil

Ouvrez l'archive précedement télechargé, puis ouvrir le fichier `env`.

Je vous conseil (apres avoir perdu du temps a cause de l'éditeur gEdit ou NotePad ++) de l'ouvrir avec un editeur hexadecimal, il y en a en [ligne ici](https://hexed.it)

![Fichier ENV en HEXA avant](images/fichier_env_hexa_avant.png)

Verifier que la ligne relever plus haute apparait de maniere complete puis:
* Supprimer `\00.` apres `";eval".`.
* Ajouter `00` a la fin apres `0A`.

![Fichier ENV en HEXA aprés](images/fichier_env_hexa_apres.png)

>La partie après bootargs= doit être la même que celle que vous avez obtenue à l'étape 1 (de votre appareil) sans AUCUN CHANGEMENT.

Copiez maintenant lmestrois fichiers a la racine de votre carte MicroSD

>verifier qu'il n'y a pas de fichier 'upgrade.bin'.

Ejectez proprement (via démonter) votre carte.

Eteignez l'appareil puis insérez la carte MicroSD contenant les 3 fichiers dans ce dernier.

Avec un trombone, rester appuyer sur le `reset` tout en branchant l'alimentation (alim d'orignine ou cable USB) puis :
* Maintenez toujours le `reset` pendant 5 secondes,
* Laisser l'appareil démarrer normalement.

Une fois l'appareil de nouveau dispo dans votre application. Verifier avec la commande `http://admin:056565099@192.168.XXX.XXX/proc/cmdline`

Dans le fichier `env` vous devez avoir ceci maintenant :

```
mem=37M console=ttyAMA0,115200n8 mtdparts=hi_sfc:192k(bld)ro,64k(env)ro,64k(enc)ro,64k(sysflg)ro,3136k(sys),4352k(app),320k(cfg) ppsAppParts=5 ppsWatchInitEnd - ip=${T//_/$'\x20'} : ::::;T=\"sleep_5;mkdir_-p_/mnt/mmc01;mount_-t_vfat_/dev/mmcblk0p1_/mnt/mmc01;/mnt/mmc01/initrun. sh&\";eval mtdparts=hi_sfc:192k(bld)ro,64k(env)ro,64k(enc)ro,64k(sysflg)ro,3136k(sys),4352k(app),320k(cfg) ppsAppParts=5 ppsWatchInitEnd

```

7-Maintenant, allez à l'adresse suivante : http://admin:056565099@192.168.X.X/proc/self/root/mnt/mmc01/hack, 'done' doit appraitre.

### Patcher le `ppsapp`.
Rendcez vous [ici](https://github.com/guino/ppsapp-rtsp/issues/1) puis telecharger le `ppsapp` correspondant à votre sonette (chez moi ppstrong-c51-tuya2_lcs-2.9.6.20200628) puis noter les `adress` du `snap.cgi` et `play.cgi` (0x0047494c et 0x0477404 chez moi)

Allez sur [https://www.marcrobledo.com/RomPatcher.js/](https://www.marcrobledo.com/RomPatcher.js/)
>Ne pas activer le mode créateur.

![Macrobledo Interface](images/macrobledo_interface.png)
* Dans `Fichier ROM` selectionner votre ppsapp original sous /home/app/ppsapp sur la carte MicroSD,
* Dans `Fichier Patch` sélectionnez le fichier zip que vous avez téléchargé,
* Cliquer sur `Appliquer le patch`,
* Récuperer le fichier patcher (normalement ppsapp-rtsp ou ppsapp)
* Renommer le en ppsapps SANS extension (si besoin),
* Verifier que la taille est identique a l'originale,


Dans votre carte MicroSD
* Copier votre `ppsapp` patché a la racine de votre carte MicroSD
* Dans le dossier `cgi-bin`, ouvrir les fichiers `snap.cgi` et `mjpeg.cgi` puis ajouter l'adresse recuperée plus haut sans le `0x` du début ensuite le fichier `play.cgi` en insérant l'adresse correspondante.
* 

* Ejecter proporement la carte MicroSD
* Inserer dans la sonnnette puis la mettre en route,
* Attendez deux fois le son de démarrage
* Acceder au flux via rtsp:192.168.X.X:8554 (avec un sacré retard chez moi MAIS avec le son), http://user:password@192.168.XXX.XXX:8080/cgi-bin/mjpeg.cgi, http://user:password@192.168.XXX.XXX:8080/cgi-bin/snap.cgi
>Le fichier `play.cgi` permet de lancer un son different sur l sonnette via la commande `https://user:password@192.168.XXX.XXX/cgi-bin/play.cgi?/home/sound/dingdong.wav` plus d'info [ici](https://github.com/guino/BazzDoorbell/wiki/%5BHow-to%5D-Play-custom-sounds-trough-your-bell-speaker.).

### Acces hors cloud.
La discussion se trouve [ici](https://github.com/guino/BazzDoorbell/issues/4#issuecomment-740644879).

>**SEULEMENT** avec le firmware `ppstrong-c51-tuya2_lcs-2.9.6.20200628`. Pour les autres firmware, il y a la methode pour patcher [ici](https://github.com/guino/BazzDoorbell/issues/4#issuecomment-742596905) mais je n'ai pas du tout regardé.

Pour les chanceux, il suffit seulement de 
* Récuperer le `ppsapp` déja patché [ici](https://github.com/guino/BazzDoorbell/files/5672301/ppsapp-rtsp4.zip),
* Dézipper,
* Rennomer le fichier en `ppsapp` (sans extension),
* Remplacer celui présent a la racine (je n'ai pas eu besoin de le flashé, .... bizarre).


### Activcer le MQTT
Activer le MQTT permet de recevoir l'appuie sur le bouton ou une détection de mouvement.

La discussion est [ici](https://github.com/guino/BazzDoorbell/issues/4#issuecomment-740644879) 

* Récupérer [`mqtt_log_pazrser.zip`](https://github.com/guino/BazzDoorbell/files/5671106/mqtt_log_parser.zip) puis décompresser le.
* Coller les deux fichiers à la racine de votre carte Micro SD
* Ouvrir `log_parser.sh`,
  ![log_parser.sh Modification du broker MQTT](images/log_parser_sh.png)
* Remplacer l'IP `192.168.2.143` (ligne 33 et 36) par celle de votre broker.

```
            #echo "motion detected"
            /mnt/mmc01/mosquitto_pub -h 192.168.2.143 -m "detected" -t home/doorbell/motion
```
et 
```
            #echo "doorbell push button"
            /mnt/mmc01/mosquitto_pub -h 192.168.2.143 -m "pushed" -t home/doorbell/button
```

>Vous pouvez aussi remplacer `motion` et `button` par les valeurs que vous voulez.
Ouvrir le fichier `custom.sh` qui se trouve a la racine de votre carte MicroSD
* Commenter la ligne `/mnt/mmc01/ppsapp &`
* Ajouter en dessous `/mnt/mmc01/ppsapp 2>&1 | /mnt/mmc01/log_parser.sh /dev/null &`

Ca doit donner ca.
```
  #/mnt/mmc01/ppsapp &
  /mnt/mmc01/ppsapp 2>&1 | /mnt/mmc01/log_parser.sh /dev/null &
```

Il vous reste a verifier via MQTTExploreur pour verifier que votre sonette remonte en MQTT.

#### Remettre d'origine
Pour remettre votre camera a l'origine.
* Etendre votre sonnette,
* Sortir et supprimer le contenu de votre carte MicroSD,
* Modifier le fichier `env` en mettant seuelemnt `bootargs=mem=36 console=ttyAMA0,115200n8` en faisant attention a faire correspondre votre `mem=XX` avec celui que vous aviez a l'origine.
* N'oubliez pas d'ajouter `0A` et `00` apres `115200n8` via l'éditeur hexadecimal.
* Copier le fichier `env` et `ppsMmcTool.txt` (pas besoin du `initrun.sh`)
* Insérer la carte MicroSD,
* Maintenir `RST` puis allimenter la sonette tout en maintenant `RST` pendant 5 secondes.
* Verifier avec `http://admin:056565099@192.168.XXX.XXX/proc/cmdline` si vous avez exactement la même ligne que celle sauvegardé lors du flash.
* Vérifier que cette adresse ne renvoit rien `http://admin:056565099@192.168.X.X/proc/self/root/mnt/mmc01/hack`

Voila votre sonnette est d'origine.

#### Sources
* [Sujet sans carte SD](https://github.com/guino/BazzDoorbell/issues/13)
* [Sujet Principal (avec carte SD)](https://github.com/guino/BazzDoorbell/issues/2)
* [Sauvegarde](https://github.com/guino/BazzDoorbell/issues/11)
* [Patch ppsapp](https://www.marcrobledo.com/RomPatcher.js/)
* [Hors cloud](https://github.com/guino/BazzDoorbell/issues/4#issuecomment-740644879)
