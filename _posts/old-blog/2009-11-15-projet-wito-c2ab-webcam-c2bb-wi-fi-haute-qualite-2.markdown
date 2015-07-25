---
layout: page
subheadline: "Tech"
title: "Projet WiTo – « webcam » Wi-Fi haute qualité – 2"
date: 2009-11-15 06:48:47+00:00
teaser: "_Comme présenté dans l'article précédent, l'objectif de ce petit  projet est de connecter un vieil appareil photo à Internet pour faire  office de Webcam haute qualité (et autonome)._"
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
La fluidité n'est pas l'objectif de ce projet, un débit (_framerate_)  d'une image toutes les 5 minutes est largement suffisant.

Nous partons donc à la recherche des options qui s'offrent à nous  (via google):

  * Connecter un appareil photo via sa sortie analogique à un [boitier d'acquisition video ethernet](http://boutique.infracom-france.com/serveur-video-audio-platine-p-743.html).
  * Utiliser une SD-Card Wi-Fi: [Eye-Fi](http://www.eye.fi/)
  * Utiliser le mode PTP et un linux embarqué.

![La carte SD Wi-Fi Eye-Fi](http://infracom-france.com/blog2/wp-content/uploads/2009/11/eye-fi-card.jpg)
    La carte SD Wi-Fi Eye-Fi

Les deux premières solutions ne répondent pas à nos besoins:

  * un boîtier d'acquisition vidéo Ethernet offrira une résolution assez  faible du fait des contraintes liées à la vidéo et détaillées  précédemment.
  * la carte Eye-Fi pourrait être une solution intéressante, mais ce  produit est relativement cher et après quelques recherches il ne semble  pas possible de la connecter à Internet directement, mais à un PC, lui  même connecté à Internet. De plus l'upload est restreint à certaines  plateformes (pas de FTP ici).

Nous allons donc opter pour la troisième solution.

_**Note:** Il existe des accessoires pour appareils SLR (reflex)  qui permettent l'envoi par FTP via Wi-Fi des photos prises. Par contre  dans ce cas là nous explosons le budget (plusieurs centaines d'euros  l'accessoire, plus le coût de l'appareil photo)._


![Le Nikon D2X dispose d'une option Wi-Fi](http://infracom-france.com/blog2/wp-content/uploads/2009/11/NikonD2x.jpg)
    Le Nikon D2X dispose d'une option Wi-Fi

[PTP (Picture Transfer Protocol)](http://fr.wikipedia.org/wiki/Picture_Transfer_Protocol) est un protocole  permettant l'échange d'informations entre un PC et un appareil photo  (notamment). C'est le protocole que vous utilisez très probablement si  vous transférez des photos en connectant directement votre appareil à  votre ordinateur.

Et c'est ici que tout deviens beaucoup plus intéressant, il est  possible de déclencher la prise de vue à distance depuis le PC et de  transférer la photo par la suite.

Mmmm nous sommes sur une piste....

<A SUIVRE>

_This article has been automatically imported from our old blog, there might be formatting or layout issues._
