---
layout: page
subheadline: "Tech"
title: "Projet WiTo – « webcam » Wi-Fi haute qualité – 3"
date: 2009-11-16 06:51:11+00:00
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
Une voie, que dis-je, une autoroute s'ouvre à nous : PTP nous voilà  !!

Mais avant de se jeter plus en avant il est nécessaire de s'assurer  que l'utilisation du PTP est possible sur des plateformes linux  embarquées.

Sous linux le logiciel permettant de manipuler des appareils photos  via PTP s'appelle [gphoto](http://gphoto.sourceforge.net/), il  est donc nécessaire de s'assurer de la disponibilité du logiciel pour  des plateformes embarquées.

![Le Logiciel Gphoto2 sous Linux](http://infracom-france.com/blog2/wp-content/uploads/2009/11/gphoto-logo.png)
    Le Logiciel Gphoto2 sous Linux

Un rapide connexion sur une de nos plateformes de développement  répond rapidement à nos interrogations.

<code>
wifipak> ipkg list | grep gphoto
gphoto2 - 2.4.1-1 - Command line digital camera software applications
libgphoto2 - 2.4.1-1 - digital camera software libraries
</code>

Bingo ! Le logiciel est disponible sur les dépots ipkg (apt-get pour  plateformes embarquées).

Nous pouvons donc avancer un peu plus dans le développement du WiTo.

Gphoto offre deux modes répondant à nos besoins:

  * Tethering
  * Capture and Download

Le mode tethering permet de transférer directement une photo entre  l'appareil sans passer par la carte mémoire et de transmettre ce cliché à  un logiciel présent sur le PC via un script (un "hook" script). Bien  que cette option semble intéressante, les différents tests réalisés ne  furent pas concluants (probablement un soucis de compatibilité avec  l'appareil photo de test). N'oubliez pas que nous visons l'utilisation  d'une plateforme embarquée avec de faibles ressources.

Le mode "Capture and Download", enregistre la photo sur la carte  mémoire de l'appareil photo, la transfère sur le PC puis efface la photo  de la carte mémoire.

Nous allons donc nous orienter vers cette seconde option.

La liste  des appareils testés et compatibles (ou non) avec Gphoto est disponible  ici: [http://gphoto.sourceforge.net/doc/remote/](http://gphoto.sourceforge.net/doc/remote/)

Par chance nous disposons d'un vieux Canon PowerShot A520 4 Mpix dont  le zoom ne se referme plus correctement. La prise de vue est toujours  correcte, cet appareil répond donc parfaitement à nos besoins. De plus,  il dispose d'une alimentation externe ce qui devrais permettre de le  laisser allumé 24h/24.

![Canon PowerShot A520](http://infracom-france.com/blog2/wp-content/uploads/2009/11/canon_powershot_a520.jpg)
    Canon PowerShot A520

Il ne nous reste plus qu'à développer un petit script pour prendre la  photo et la mettre à disposition en ligne.

<A SUIVRE>

_This article has been automatically imported from our old blog, there might be formatting or layout issues._
