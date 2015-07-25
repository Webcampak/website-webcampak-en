---
layout: page
subheadline: "Tech"
title: "Projet WiTo – « webcam » Wi-Fi haute qualité – 8"
date: 2009-12-04 07:30:36+00:00
teaser: "_Comme présenté précédemment, l’objectif de ce petit projet est de  connecter un vieil appareil photo à Internet pour faire office de Webcam  haute qualité (et autonome)._"
header:
    image_fullwidth: "header_typewriter.jpg"
    caption: Image by Florian Klauer
    caption_url: "http://florianklauer.de/"
image:
    thumb:  typewriter_thumb.jpg
    homepage: homepage_typewriter.jpg
categories:
    - tech
comments: false
show_meta: true
---
Nous avons donc, après quelques péripéties, un système autonome  capable d'envoyer à intervalles régulier des photos sur Internet._ _

Vous trouverez ci-dessous la méthode expliquée pas à pas pour mettre  en place ce système._ _

**1- Restauration en cas de crash**

Avant toute chose, il est toujours bon de détailler une procédure de  restauration en cas de gros soucis.

La procédure pour restaurer une fonera crashée est détaillée ici: [http://wiki.fon.com/wiki/Firmware_Restore](http://wiki.fon.com/wiki/Firmware_Restore)

Nous avons eu quelques difficultés avec le logiciel tftp sous Linux  et avons donc installé le logiciel atftp. Nous lançons alors les  commandes suivantes :

<code>
# atftp 192.168.1.6
tftp> connect 192.168.1.6
tftp> verbose
tftp> trace
tftp> mode octet
tftp> put 20091008_FON2303_2.3.0.0_Restore.bin
</code>

**2- Configuration de la Fonera 2.0n**

Installez tout d'abord le firmware de développement et connectez vous  sur la Fonera en SSH.

Commencez par formater une clef usb : dans notre cas nous avons  choisi de créer deux partitions, une partition de 500mo pour les  logiciels et le système, et une partition de 1.5 go pour servir de  tampon pour les photos.

La création de la table de partition se fait à l'aide de l'outil  fdisk et de la commande:

<code>
root@Fonera:~# fdisk /dev/sda
Command (m for help): p

Disk /dev/sda: 2021 MB, 2021654528 bytes
63 heads, 62 sectors/track, 1010 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x6b736964

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         151      294872   83  Linux
/dev/sda2             152        1010     1677627   83  Linux
</code>

La commande p vous affichera la table de partition. Utilisez la  commande "d" pour supprimer des partitions existantes et la commande "n"  pour créer une nouvelle partition. Une fois toutes les modifications  terminées utilisez la commande "w" pour sauvegarder.

Votre table de partition est maintenant créer, il suffit de formater  les partition.

<code>
root@Fonera:~# mkfs.ext3 /dev/sda1
root@Fonera:~# mkfs.ext3 /dev/sda2
</code>

Vous aurez des détails complémentaires affichés à l'écran.

Ensuite nous préparons les répertoires ou sera montée la clef usb.

<code>
root@Fonera:~# mkdir /opt
root@Fonera:~# mkdir /pictures
root@Fonera:~# mount /dev/sda1 /opt/
root@Fonera:~# mount /dev/sda2 /pictures/
</code>

Nous pouvons maintenant nous pencher sur la configuration de opkg (le  gestionnaire de paquets).
Commencez par éditer le fichier /etc/opkg.conf

<code>
dest root /
dest ram /tmp
lists_dir ext /var/opkg-lists
src snapshots2  http://downloads.openwrt.org/kamikaze/8.09.2-RC2/rb532/packages/
dest usb /opt
option force_space
</code>

Remplacer les champs pour obtenir un résultat tel que présenté  ci-dessus.
Utilisez ensuite les commandes suivantes pour initialiser opkg :

<code>
root@Fonera:~# mkdir /usr/lib/opkg
root@Fonera:~# opkg update
root@Fonera:/pictures# opkg update
Downloading  http://downloads.openwrt.org/kamikaze/8.09.2-RC2/rb532/packages//Packages
Connecting to downloads.openwrt.org (78.24.191.177:80)
Packages             100%  |**************************************************************************|    699k 00:00:00 ETA
Updated list of available packages in /var/opkg-lists/snapshots2
Signiture check for snapshots2 skipped because GPG support was not  enabled in this build
root@Fonera:/pictures#
</code>

Opkg téléchargera la liste des toutes les applications disponibles,  une liste que vous pouvez obtenir en tapant "opkg list" dans la console.

Nous pouvons ensuite débuter l'installation des logiciels gphoto2 et  wput (alternative plus légère à lftp) :

<code>
root@Fonera:~# opkg install gphoto2
root@Fonera:~# opkg install -dest usb wput
</code>

Les logiciels nécessaires sont maintenant installés.

La version de gphoto2 disponible (2.4.1) est assez ancienne et  dispose d'un support des appareils photos un peu plus approximatif que  les versions plus récentes.

Pour que le système fonctionne nous devons spécifier le modèle  d'appareil photo pour s'assurer une compatibilité correcte.

Tout d'abord connectez votre appareil photo, allumez le (en mode  lecture pour le notre), ensuite nous allons détecter le modèle de  l'appareil.

<code>
root@Fonera:~# gphoto2 --auto-detect
Model                          Port
----------------------------------------------------------
Canon Digital IXUS 50 (normal mode) usb:
Canon Digital IXUS 50 (normal mode) usb:001,005
</code>

Comme vous pouvez le constater l'appareil est détecté comme un "Canon  Digital IXUS 50 (normal mode)" à la place d'un "Canon PowerShot A520  (PTP mode)"

Vérifiez la dénomination exacte du pilote de votre appareil photo  grâce à la commande :

<code>
root@Fonera:/pictures# gphoto2 --list-cameras | grep 520
"Canon PowerShot A520 (PTP mode)"
"Nikon Coolpix 5200 (PTP mode)"
</code>

Nous listons tous les modèles de caméra contenant le nombre 520.

Nous pouvons maintenant passer au script. Plusieurs modifications ont  été effectuées depuis nos tests initiaux sur PC. Copiez le script  suivant sur votre fonera 2.0n :

<code>
#!/bin/sh
######################################
######## CONFIGURATION START #########
######################################
capturedir="/pictures/";
logdate=`echo $(date +%d) $(date +%B) $(date +%Y) - $(date +%k):$(date  +%M)`

export PATH=/bin:/sbin:/usr/bin:/usr/sbin:/opt/usr/bin:/opt/opt/bin
export LD_LIBRARY_PATH=/lib:/usr/lib:/opt/lib:/opt/opt/lib:/opt/usr/lib

# PARAMETRES CAMERA

capturecamera="Canon PowerShot A520 (PTP mode)"captureport="usb:"
captureimgfilter="img_*.jpg"
capturedefaultname="VirtualObject"

# PARAMETRES FTP
ftpserver="ftp.wwwwwwwww.com";
ftpuser="wwwwwwwww";
ftppassword="wwwwwwwww";
ftpdir="/webtest/";
ftparchivedir="/webtest/archive/";

Init="no"
CaptureStd="yes";
######################################
######## CONFIGURATION STOP ##########
######################################

######################################
######## MOUNT ##########
######################################
mount /dev/sda1 /opt/
mount /dev/sda2 /pictures/

if [ "$Init" = "yes" ] ; then
echo "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
echo "xxxx    INITIALISATION    xxxx"
echo "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
rm ${capturedir}* -r
fi

if [ "$CaptureStd" = "yes" ] ; then
#echo "xxxxxxxxxxxxxxxxxxxxxxxxxxx"
#echo "xxxx   CAPTURE PHOTO   xxxx"
#echo "xxxxxxxxxxxxxxxxxxxxxxxxxxx"
echo "${logdate} xxxxxxxxxxxxxxxxxxxxxxxxxxx" >>  ${capturedir}webcap.log
echo "${logdate} xxxx   CAPTURE PHOTO   xxxx" >>  ${capturedir}webcap.log
echo "${logdate} xxxxxxxxxxxxxxxxxxxxxxxxxxx" >>  ${capturedir}webcap.log
cd ${capturedir}
#echo "Delete --> Suppression photos precedentes (si existantes)"
echo "${logdate} Delete --> Suppression photos precedentes (si  existantes)" >> ${capturedir}webcap.log
rm ${capturedir}${captureimgfilter}
/usr/bin/gphoto2 --camera="${capturecamera}" --set-config  /main/settings/capturetarget=1 --port="${captureport}" --debug  --debug-logfile=${capturedir}webcap.log
/usr/bin/gphoto2 --camera="${capturecamera}" --capture-image  --port="${captureport}" --debug --debug-logfile=${capturedir}webcap.log
#echo "gphoto2 --camera="${capturecamera}" --capture-image  --port="${captureport}""
echo "${logdate} gphoto2 --camera="${capturecamera}" --capture-image  --port="${captureport}"" >> ${capturedir}webcap.log
/usr/bin/gphoto2 --camera="${capturecamera}" -P --port="${captureport}"   --debug --debug-logfile=${capturedir}webcap.log
/usr/bin/gphoto2 --camera="${capturecamera}" -D --port="${captureport}"  -R --debug --debug-logfile=${capturedir}webcap.log
dispdate=$(date +%Y%m%d%k%M)
printdate=`echo $(date +%A) $(date +%d) $(date +%B) $(date +%Y) - $(date  +%k) h $(date +%M)`
mv ${capturedir}${captureimgfilter} ${capturedir}${dispdate}.jpg
#echo "WPUT --> Upload de la photo $dispdate.jpg sur vers  $ftparchivedir"
echo "${logdate} WPUT --> Upload de la photo $dispdate.jpg sur vers  $ftparchivedir" >> ${capturedir}webcap.log
/opt/usr/bin/wput ${capturedir}${dispdate}.jpg  ftp://$ftpuser:$ftppassword@$ftpserver/
#echo "Rename --> Renommage en webcam.jpg"
echo "${logdate} Rename --> Renommage en webcam.jpg" >>  ${capturedir}webcap.log
mv ${capturedir}${dispdate}.jpg ${capturedir}webcam.jpg
#echo "WPUT --> Upload de la photo webcam.jpg sur vers $ftpdir"
echo "${logdate} WPUT --> Upload de la photo webcam.jpg sur vers  $ftpdir" >> ${capturedir}webcap.log
/opt/usr/bin/wput -nc -u ${capturedir}webcam.jpg  ftp://$ftpuser:$ftppassword@$ftpserver/
#echo "Delete --> Suppression photos locales"
echo "${logdate} Delete --> Suppression photos locales" >>  ${capturedir}webcap.log
rm ${capturedir}/*.jpg
fi
</code>


Il sera nécessaire de modifier certains éléments pour rendre le  script compatible avec votre appareil/installation.

Notamment :
  * capturecamera: qui correspond au modèle de votre appareil identifié  plus haut.
  * captureimgfilter: qui correspond au nom de fichier enregistrés par  votre appareil photo.
  * les différents paramètres FTP.

Vous pouvez ensuite vérifier que tout fonctionne correctement en  l'exécutant depuis un terminal :

<code>
root@Fonera:~# chmod +x /root/votrescript.sh
root@Fonera:~# ./root/votrescript.sh</blockquote>
</code>

Si tout fonctionne correctement nous pouvons passer à  l'automatisation du script via la tâche cron.

Créez tout d'abord un fichier vide /etc/crontabs/root (créer le  répertoire crontabs si nécessaire).

Ensuite faites un lien symbolique vers ce fichier :

<blockquote>root@Fonera:~# ln -sf /etc/crontabs/root /etc/crontab</blockquote>

Editez ensuite le fichier /etc/crontabs/root :

<code>
*/5 * * * * /root/votrescript.sh
</code>

Puis il est nécessaire de s'assurer que crond est bien lancé à chaque  démarrage, plutôt que de créer un script complexe nous nous contentons  de rajouter une ligne qui va bien au script de démarrage de la partie  USB (méthode assez sale). Modifiez le fichier en conséquence :

<code>
root@Fonera:/root# cat /etc/init.d/usb
#!/bin/sh /etc/rc.common
# Copyright (C) 2006 OpenWrt.org

START=39
start() {
[ -d /proc/bus/usb ] && {
/bin/mount -t usbfs none /proc/bus/usb
}
crond /etc/crontab -l 0 -L /pictures/crondlog.log
}
</code>

Et voilà c'est à peu près tout, votre système devrais êtres  fonctionnel automatiquement dès le démarrage de la fonera 2.0n.

<A SUIVRE>

_This article has been automatically imported from our old blog, there might be formatting or layout issues._
