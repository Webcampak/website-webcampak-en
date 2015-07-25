---
layout: page
subheadline: "Tech"
title: "Webcampak network monitoring"
date: 2011-09-15 15:58:16+00:00
teaser: "To ensure we provide stabled and reliable services to our customers some of our Webcampak devices are being monitored 24/7 using a central monitoring server built with Nagios/Centreon software."
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
    - /en/2011/09/15/supervision-reseau-webcampak/
---
This system can be considered as an addition to the existing email alert built-in Webcampak software.

Centreon let us see in one single page the operational status of our devices. It allows us to react quickly and sends us an email automatically if something goes wrong.

[![]({{ site.urlimg }}blog/2011/09/Nagios-Header.png)]({{ site.urlimg }}blog/2011/09/Nagios-Header.png)For example, on the above capture we have 25 devices being monitored. 24 are up and 1 is down (one of our rental Webcampak system is currently being reconfigured). Then, 52 services are currently under supervision, 2 of them need a bit of attention and 5 are considered critical (sensor values over limits we defined in the system).

[![]({{ site.urlimg }}blog/2011/09/Webcampak-Supervision.png)]({{ site.urlimg }}blog/2011/09/Webcampak-Supervision.png)As you can see on this capture, last can for this set of equipment happened at 22:15 (capture was taken at that time). We can see the rental Webcampak being "Down". Devices are monitored over Internet (for two of them, using SSH) or, preferrably, over a secured VPN.

We can then for each of our devices check the status of each service under supervision.

Graps are useful to see how thing changes over a long period of time.

[![]({{ site.urlimg }}blog/2011/09/Webcampak-disk.png)]({{ site.urlimg }}blog/2011/09/Webcampak-disk.png)For example, on the above pictures you can see disk usage of one of our Webcampak. As you may notice the system automatically and regularly free disk space by removing oldest pictures from the internal hard disk (the system was configured this way).

_This article has been automatically imported from our old blog, there might be formatting or layout issues._
