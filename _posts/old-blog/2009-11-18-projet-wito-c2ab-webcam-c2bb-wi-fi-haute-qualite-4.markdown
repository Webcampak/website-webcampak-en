---
layout: page
subheadline: "Tech"
title: "Projet WiTo – « webcam » Wi-Fi haute qualité – 4"
date: 2009-11-18 11:54:36+00:00
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
Comme vous pouvez le constater nous ne nous sommes pas encore penché  sur l'aspect "matériel" de la solution. Nous y consacrerons un prochain  billet.

De manière à automatiser la prise de photo et l'envoi vers un serveur  FTP, nous allons créer un script shell.

L'objectif de ce script sera:

  * de prendre une photo et de la transférer via USB,
  * de "tagger" cette photo avec la date et l'heure,
  * de mettre en ligne cette photo sur un serveur FTP,
  * de redimensionner (1024x768) et renommer la photo en "webcam.jpg" et  la mettre en ligne sur un serveur FTP.

En plus des paquets gphoto, deux paquets complémentaires seront  installés : imagemagick (manipulation d'images) et lftp (logiciel ftp  avancé).

<code>
wifipak> ipkg list | grep imagemagick
imagemagick - 6.5.5.10-1 - A set of image processing utilities.
wifipak> ipkg list | grep lftp
lftp - 4.0.3-1 - Sophisticated ftp/http client, file transfer program  supporting a number of network protocols.
wifipak>
</code>

Comme vous pouvez le constater, ces paquets sont bien disponibles sur  plateforme embarquée.

![Exemple de date crée par ImageMagick](http://infracom-france.com/blog2/wp-content/uploads/2009/11/WiTo-Script-Date.png)
    Exemple de date crée par ImageMagick

Le script sera ensuite lancé via une tache cron toutes les X minutes.  Entre 5 et 10 minutes me semble correct. Notez qu'il faut être sûr que  la photo soit bien en ligne avant de relancer le script.

De plus, il faut veiller à bien supprimer les photos, en effet le  stockage sur la plateforme sera matériellement très limité. Il sera peut  être nécessaire d'y adjoindre une clef usb.

Voici donc le script:

<code>
#!/bin/sh
######################################
######## CONFIGURATION START #########
######################################
capturedir="/home/fanfoue/Videos/capture/";

# PARAMETRES FTP
ftpserver="ftp.sample.com";
ftpuser="sample";
ftppassword="sample";
ftpdir="/webtest/";
ftparchivedir="/webtest/archive/";

Init="no"
CaptureStd="yes";
CaptureAdv="no";
######################################
######## CONFIGURATION STOP ##########
######################################

if [ "$Init" = "yes" ] ; then
echo "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
echo "xxxx    INITIALISATION    xxxx"
echo "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
rm ${capturedir}* -r
fi

if [ "$CaptureStd" = "yes" ] ; then
echo "xxxxxxxxxxxxxxxxxxxxxxxxxxx"
echo "xxxx   CAPTURE PHOTO   xxxx"
echo "xxxxxxxxxxxxxxxxxxxxxxxxxxx"
cd ${capturedir}
echo "Delete --> Suppression photos precedentes (si existantes)"
rm ${capturedir}IMG_*.JPG
gphoto2 --capture-image-and-download
dispdate=$(date +%Y%m%d%k%M)
printdate=`echo $(date +%A) $(date +%d) $(date +%B) $(date +%Y) - $(date  +%k) h $(date +%M)`
mv IMG_*.JPG ${capturedir}${dispdate}.jpg
mogrify -font Helvetica -pointsize 30 \
-draw "gravity southwest \
fill black  text 0,12 \"${printdate}\" \
fill white  text 1,11 \"${printdate}\"" ${capturedir}${dispdate}.jpg
echo "Lftp --> Upload de la photo $dispdate.jpg sur vers  $ftparchivedir"
lftp -c "open $ftpserver; user $ftpuser $ftppassword; cd $ftparchivedir;  put ${capturedir}${dispdate}.jpg; bye"
echo "Resize --> Redimensionnement ${capturedir}${dispdate}.jpg en  1024x768"
convert ${capturedir}${dispdate}.jpg -resize 1024x768  ${capturedir}${dispdate}.jpg
echo "Rename --> Renommage en webcam.jpg"
mv ${capturedir}${dispdate}.jpg ${capturedir}webcam.jpg
echo "LFTP --> Upload de la photo webcam.jpg sur vers $ftpdir"
lftp -c "open $ftpserver; user $ftpuser $ftppassword; cd $ftpdir; put  ${capturedir}webcam.jpg; bye"
echo "Delete --> Suppression photos locales"
rm ${capturedir}/*.jpg
fi
</code>

Vous pouvez tester le script en utilisant la commande suivante: sh  nomduscript.sh

<code>
xxxxxxx@laptop:~/WiTo$ sh videoscript.sh
xxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxx   CAPTURE PHOTO   xxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxx
Delete --> Suppression photos precedentes (si existantes)
rm: cannot remove `/home/xxxxxxxx/Videos/capture/IMG_*.JPG': No such  file or directory
New file is in location /store_00010001/DCIM/148CANON/IMG_4830.JPG on  the camera
Downloading 'IMG_4830.JPG' from folder  '/store_00010001/DCIM/148CANON'...
Saving file as IMG_4830.JPG
Deleting file /store_00010001/DCIM/148CANON/IMG_4830.JPG on the camera
Deleting 'IMG_4830.JPG' from folder '/store_00010001/DCIM/148CANON'...
Lftp --> Upload de la photo 200911131816.jpg sur vers  /webtest/archive/
Resize --> Redimensionnement  /home/xxxxxxxxxxx/Videos/capture/200911131816.jpg en 1024x768
Rename --> Renommage en webcam.jpg
LFTP --> Upload de la photo webcam.jpg sur vers /webtest/
Delete --> Suppression photos locales
</code>

Le script s'exécute en moins d'1 minute sur une liaison Adsl 8M.

Tout fonctionne, l'étape suivante consiste donc à trouver la  plateforme embarquée.

_This article has been automatically imported from our old blog, there might be formatting or layout issues._
