---
layout: page
subheadline: "Tech"
title: "Projet WiTo – « webcam » Wi-Fi haute qualité – 7"
date: 2009-12-03 14:22:02+00:00
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
Nous disposons donc maintenant d'un appareil photo de test, d'une  fonera flashée avec le firmware de développement (fonosphera), d'un hub  USB et d'une clef USB de 2Go.

La clef USB servira à installer les paquets complémentaires, mais  également de tampon pour stocker, si nécessaire, certaines photos avant  envoi par FTP.

Nous avons réalisé durant ces derniers jours toute une série de test  pour valider le fonctionnement de la plateforme et identifier les  restrictions associées. Nous passons en effet d'un PC portable utilisé  pour tester les script à une plateforme embarquée beaucoup plus limitée  en terme de ressources notamment.

Avant de vous présenter la suite et la procédure d'installation,  faisons le points sur les limitations et difficultés rencontrées.

  1. **La taille disque:** Une fois le firmware installé il ne reste  que 2Mo d'espace libre pour installer des applications (ce qui est  suffisant pour gphoto) mais nous a oblige à installer d'autres  applications sur la clef USB (opkg isntall -dest usb paquet).

  2. **La version de gphoto2** disponible dans les dépôts "opkg" date  de 2008, et certaines options (comme la très pratique  capture-and-download) n'existent pas. Il a donc été nécessaire de  modifier le script pour contourner cette limitation. De plus nous  trouvons cette version de gphoto2 moins performante que la dernière  disponible. A moins que cette constatation soit due à la puissance de la  Fonera elle-même.

  3. **Les dépendances logicielles** ont aussi représenté une forte  limitation qui nous a empêché d'utiliser imagemagick (redimensionnement  et ajout d'un sous-titre avec la date). Nous avons également du trouver  un autre logiciel FTP, lftp ne voulant pas s'installer, faute de trouver  les bons paquets. Les difficultés que nous avons rencontrées sont liées  à libsdc++ et libbz2.

  4. Quelques soucis pour démarrer le cron automatiquement mais ce  problème est résolu.

D'un point de vue fonctionnel le système est donc capable:

  * de prendre une photo et de l'envoyer sur internet avec deux noms  (date.jpg et webcam.jpg),
  * de prendre cette photo toutes les xx minutes (configurable).

Le système n'est pas capable:

  * d'apposer un bandeau au bas de l'image avec la date de prise de vue.
  * de redimensionner cette photo (utile pour le fichier webcam.jpg).

Prochainement, nous étudierons probablement la capacité de la Fonera à  mettre en tampon les fichiers image en cas d'indisponibilité de la  connexion Internet. Une fois la connexion rétablie la Fonera pourra  alors de nouveau continuer à mettre en ligne les images.

Nous allons donc vous présenter dans les prochains billets les  commandes à passer pour transformer votre fonera en outil de prise de  vues automatiques.

<A SUIVRE>

_This article has been automatically imported from our old blog, there might be formatting or layout issues._
