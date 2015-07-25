---
layout: page
subheadline: "Tech"
title: "Webcampak: vous avez un message"
date: 2010-07-16 09:34:11+00:00
teaser: "Webcampak est, depuis hier, en mesure de vous contacter directement par email, par le biais de votre serveur SMTP préféré (gmail par exemple)."
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
[![](http://infracom-france.com/blog2/wp-content/uploads/2010/07/Webcampak-email-300x146.png)](http://infracom-france.com/blog2/wp-content/uploads/2010/07/Webcampak-email.png)

Pour le moment c'est un simple message de test, ne tenez pas compte de sa présentation ;-)

Nous avons rendu possible l'envoi d'email dans deux cas de figure:
  * En cas d'erreurs répétées dans la capture d'une source (par exemple un appareil photo débranché).
  * A la fin de la création d'une vidéo personnalisée (processus qui peut être long).

Penchons-nous un peu plus en détails sur l'erreur de capture.

A chaque erreur, un compteur est incrémenté. Une fois que ce compteur atteint une certaine valeur (de votre choix), le Webcampak procède à l'envoi d'un email (en y incluant les messages de logs pour vous assister dans l'identification du problème). Il place ensuite un marqueur interne pour lui indiquer qu'un email a déjà été envoyé.

Aucun email ne sera envoyé tant que la capture ne fonctionne pas de nouveau. Une fois la capture fonctionnelle, le compteur est réinitialisée et le marqueur supprimé. Le processus redémarre donc à zéro.

_This article has been automatically imported from our old blog, there might be formatting or layout issues._
