---
layout: page
subheadline: "Tech"
title: "Webcampak: nouvelle interface d’administration"
date: 2010-07-05 08:49:17+00:00
teaser: "L'interface d'administration du Webcampak approche de sa version  définitive."
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
Le choix d'une interface (ou IHM) est toujours un point critique : un  produit a beau être extrêmement stable et performant, si l'IHM n'offre  pas un minimum de facilité d'utilisation, n'est pas agréable et claire,  les utilisateur ne seront pas attirés par le produit ou s'en lasseront.

[![Interface d'administration](http://infracom-france.com/blog2/wp-content/uploads/2010/07/help.index_-300x120.png)](http://infracom-france.com/blog2/wp-content/uploads/2010/07/help.index_.png)

[![](http://infracom-france.com/blog2/wp-content/uploads/2010/07/help.index_.left_.numbered-158x300.png)](http://infracom-france.com/blog2/wp-content/uploads/2010/07/help.index_.left_.numbered.png)

Tel que  présentée précédemment, chaque source pourra être configurée via un menu  dédié (2) ou (3). Un menu "Système" (1) vous permettra de configurer le  Webcampak en lui-même.

Nous sommes  depuis des années favorables aux solutions libres, telles que GNU/Linux.  Ces solutions amènent avec elles des licences offrant une grande  souplesse, et évitent surtout de ré-inventer la roue.

Nous avons  par exemple un manque de compétences en "design" : plutôt que de  re-développer une interface, nous avons donc décidé de nous "inspirer"  d'une interface existante dans notre cas l'interface d'administration du  logiciel de blog [Wordpress](http://wordpress.org/). Cette interface claire  et sobre répond à l'heure actuelle complètement à nos besoins. Il ne  s'agit néanmoins pas de s'approprier le travail de l'équipe [Wordpress](http://wordpress.org/),  tout se fera dans le respect total de la license GPL, et nous restons  totalement transparent sur l'origine de ce _look_.

Le schéma  ci-dessous présente le fonctionnement des différents modules Webcampak:

[![](http://infracom-france.com/blog2/wp-content/uploads/2010/07/Webcampak-engine.png)](http://infracom-france.com/blog2/wp-content/uploads/2010/07/Webcampak-engine.png)

  * L'interface d'administration est composée d'une partie affichage,  réalisée en HTML/CSS à l'aide du moteur de template Smarty. Cette  section est très fortement inspirée de Wordpress. Remplacer le  "look-and-feel" de l'interface d'administration est donc très aisée et  ne nécessite aucune connaissance particulière en programmation. Le "back  office" est quand à lui composé d'un moteur PHP développé  spécifiquement par Infracom pour le Webcampak. Le moteur PHP a, par  exemple, pour charge d'écrire dans les fichiers de configuration.
  * Les fichiers de configuration servent à stocker les paramètres du  système et des différentes sources.
  * Le moteur "Wi-To" est le cœur du système, il consulte les fichiers  de configuration puis fonctionne de manière autonome.

L'ensemble de  l'interface d'administration sera disponible sous licence GPL, libre à  vous de la modifier de l'adapter à vos besoins voir même de l'utiliser  pour vos autres projets.

Une fois le  Webcampak finalisé, nous étudierons l'opportunité de diffuser le moteur  Wi-To sous une licence de type GPL mais il est encore trop tôt pour  prendre une quelconque décision à ce sujet. Nous préférons donc pour le  lancement et les quelques semaines/mois qui suivront conserver la  propriété de l'outil que nous avons développé.

Que  pensez-vous de cette approche ? Vos commentaires sont les bienvenus  comme toujours.

_This article has been automatically imported from our old blog, there might be formatting or layout issues._
