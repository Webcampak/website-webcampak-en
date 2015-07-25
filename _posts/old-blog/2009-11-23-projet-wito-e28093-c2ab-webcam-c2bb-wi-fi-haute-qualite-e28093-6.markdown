---
layout: page
subheadline: "Tech"
title: "Projet WiTo – « webcam » Wi-Fi haute qualité – 6"
date: 2009-11-23 09:19:37+00:00
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
Nous avons reçut la Fonera 2.0n via UPS. La boite contient:

  * La Fonera 2.0n
  * Un câble Ethernet
  * L'alimentation
  * Des tampons en caoutchouc

La première chose à faire lors de la réception est de mettre à jour  le firmware avec une version développeur, and let's go.

![fonera-2.0n_2.3.0.0_Settings](http://infracom-france.com/blog2/wp-content/uploads/2009/11/fonera-2.0n_2.3.0.0_Settings-300x179.png)
    Panneau de Configuration de la fonera

**La première surprise** est, je doit le reconnaitre, un défaut de  préparation de ma part, tout est en effet très bien documenté ici : [http://wiki.fon.com/wiki/Network_Configuration](http://wiki.fon.com/wiki/Network_Configuration)

Petit extrait concernant le mode WiFi WAN Mode:

<code>***** For now this mode is only available for the  Fonera 2.0g.</code>

Donc pour résumer, pour le moment il est impossible d'utiliser la  connexion Wi-Fi pour connecter la Fonera 2.0n à Internet.

Ce n'est pas bloquant pour le moment, en attendant que Fon rende ce  mode disponible nous pourrons utiliser un [bridge  Wi-Fi de ce type](http://boutique.infracom-france.com/wrt54gl-ddwrt-p-574.html).

**La seconde difficulté** rencontrée est liée à l'espace mémoire.  Plusieurs partitions sont disponibles dont deux qui nous intéressent  particulièrement.

  * L'espace de stockage non volatile (qui ne sera pas perdu après un  reboot) dispose de 4 Mo d'espace libre.
  * L'espace de stockage /tmp (volatile) dispose de 30 Mo d'espace  libre.

Nous pensions utiliser /tmp pour le stockage de la photo avant envoi  et l'espace non volatile sera nécessaire pour installer les différents  paquets (gphoto2, ImageMagick et lftp).

Et c'est là que se situe le second soucis. Rien que l'archive de  ImageMagick fait plus de 5 Mo, une fois décompressée, plus de 30Mo. Le  stockage interne ne suffira pas.

Il sera donc impératif d'y adjoindre une clef USB pour le stockage.  Et tant qu'à faire nous en profiterons pour nous équiper d'une clef de  plusieurs giga (8 probablement) pour y stocker un nombre important de  photos dans le cas ou le boitier aurait des difficultés à se connecter à  Internet.

Nous réaliserons ensuite une installation en statique d'ImageMagick  sur la clef usb avec les liens (ln) qui vont bien.

La Fonera 2.0n ne disposant que d'un port USB, pour y connecter  l'appareil photo et la clef USB nous aurons donc à nous équiper d'un hub  USB (un modèle non alimenté devrait suffire).

La suites des billets avec procédure d'installation détaillée dès  réception du matériel complémentaire.

<A SUIVRE>

_This article has been automatically imported from our old blog, there might be formatting or layout issues._
