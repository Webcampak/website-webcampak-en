---
layout: page
subheadline: "Tech"
title: "Webcampak : record weather and interract with sensors"
date: 2011-02-23 06:37:30+00:00
teaser: "There has not been much post on our blog recently, we are currently working on improving the core of our system to easy addition of new functionalities."
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
redirect_from:
    - /en/2011/02/23/webcampak-ajout-de-la-meteo/
---
While working on this we took some time to add new functionalities. You can now remotely power shut/unshut the camera via an electronic relay automatically or manually controlled by Webcampak.

We've also added a nice functionality that some of you might find interesting, the ability to manage weather sensors and insert results within pictures and videos.

We are currently only working on two sensors but our system makes it really easy to add new ones (such as wind direction, wind speed, pressure, humidity ...). Measurements are recorded on a structured text file and can be easily inserted within any other projects.

[caption id="attachment_6774" align="aligncenter" width="400" caption="Webcampak sensors over half a day"][![Webcampak Capteurs Température et Luminosité](http://infracom-france.com/blog2/wp-content/uploads/2011/02/sensors.txt.png)](http://infracom-france.com/blog2/wp-content/uploads/2011/02/sensors.txt.png)[/caption]

[caption id="attachment_6775" align="aligncenter" width="349" caption="Inserting measurements within a picture"][![Intégration des capteurs dans une image](http://infracom-france.com/blog2/wp-content/uploads/2011/02/webcampak.capteurs.jpg)](http://infracom-france.com/blog2/wp-content/uploads/2011/02/webcampak.capteurs.jpg)[/caption]

As you can see there are a few variation when the temperature goes under 8°C, probably related to the test-enclosure of the sensor, we are currently working on improving those results. Accurancy is announced to be around 0.5°C by the manufacturer. Webcampak could interract with highly reliable sensors but they are much more expensive (around 400-600€ per sensor).

Last nice addition, the luminosity sensor can interract with the camera, for example by enabling automatic captures only during day time.

_This article has been automatically imported from our old blog, there might be formatting or layout issues._
