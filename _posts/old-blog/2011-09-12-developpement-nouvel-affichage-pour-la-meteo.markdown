---
layout: page
subheadline: "Tech"
title: "Programming: New weather sensors graphs"
date: 2011-09-12 15:33:34+00:00
teaser: "We implemented RRDTool within Webcampak core software. RRDTool is well-known network (not only) graphing tool used by large network monitoring software (Nagios/Centreon being one of them)."
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
    - /en/2011/09/12/developpement-nouvel-affichage-pour-la-meteo/
---
We were previously using matplotlib, a library created to display scientifical values (maths, stats, ...) with a wide range of capabilities, not only focusing on graphing temporal values. The downside of this was its complexity, matplotlib is way more complex to implement than RRDTool.

No major impacts for our users except slightly more user-friendly graphs but on our side it opens a new range of future capabilities we might offer to our customers (we could for example develop a module to measure precisely Webcampak network bandwidth performance).

Anyway, from now we've got new nice graphs and a more stable software.

[![]({{ site.urlimg }}blog/2011/09/Sensor-RelativeHumidity.png)![]({{ site.urlimg }}blog/2011/09/Sensor-Temperature.png)]({{ site.urlimg }}blog/2011/09/Sensor-Temperature.png)Just take a look at temperature variation compared to humidity. Higher is the humidity lower is the temperature, and vice-versa.

_This article has been automatically imported from our old blog, there might be formatting or layout issues._
