---
layout: page
subheadline: "Tech"
title: "Simplified admin interface and scheduled captures"
date: 2012-05-08 15:32:11+00:00
teaser: "We started working on Webcampak in 2009 and we've been constantly adding new features since then."
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
    - /en/2012/05/08/simplification-de-linterface-dadministration-et-des-captures-planifiees/
---
The administration panel progressively became complexe and one of our focus for this new version (v1.5) was to make things easier, especially be reducing the number of menu and working on their content.

**Capture calendar**

This feature is especially useful in construction projects to avoid capturing too many pictures. It lets you configure capture timeframe depending of the day of the week.

This feature was available previously but was more complex to implement. We removed the "schedule" global menu and moved its content to "capture" on a per source basis.

[![]({{ site.urlimg }}blog/2012/05/Screen-Shot-2012-05-08-at-11.19.24-AM-300x171.png)]({{ site.urlimg }}blog/2012/05/Screen-Shot-2012-05-08-at-11.19.24-AM.png)

Above, you can see that capture is activated Monday-Thursday from 07:00 am to 06:00 pm and Friday from 07:00am until noon.

**FTP Servers configuration**

We noticed that it was sometime necessary to send content from multiple sources to the same FTP server, to ease configuration in this situation we decided to move configuration of all FTP servers used by Webcampak to a dedicated global configuration page.

When a source is being configured, you can choose in a list the FTP server you want to send data to.

[![]({{ site.urlimg }}blog/2012/05/Screen-Shot-2012-05-08-at-11.20.15-AM-300x64.png)]({{ site.urlimg }}blog/2012/05/Screen-Shot-2012-05-08-at-11.20.15-AM.png)

_This article has been automatically imported from our old blog, there might be formatting or layout issues._


