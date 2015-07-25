---
layout: page
subheadline: "Tech"
title: "Webcampak infrastructure – Pictures processing (2/4)"
date: 2013-02-22 15:41:38+00:00
teaser: "With Webcampak we took extra care in ensuring pictures would be safe, even if this implies having pictures saved in multiple places at a single time."
header:
    image_fullwidth: "blog/2013/02/Webcampak-Typical-Pictures-110-1024x961.png"
    caption: Webcampak infrastructure highlight
    caption_url: "http://www.webcampak.com"
image:
    thumb:  blog/2013/02/Webcampak-Typical-Pictures-110-150x150.png
    homepage: blog/2013/02/Webcampak-Typical-Pictures-110-1024x961.png
categories:
    - tech
comments: false
show_meta: true
redirect_from:
    - /en/2013/02/22/webcampak-timelapse-picture-processing/
---

[![]({{ site.urlimg }}blog/2013/02/Webcampak-Typical-Pictures-110-1024x961.png)]({{ site.urlimg }}blog/2013/02/Webcampak-Typical-Pictures-110.png)

Picture acquisition, from the D-SLR camera, can be in JPG or RAW format. Choice between the two is usually taken by our customer, taking in consideration that RAW pictures require much storage than JPG.

Once a picture has been captured, Webcampak will process it. It can modify it and/or send it straight to its storage location (within Webcampak, on a local redundant storage or off-site).

The first layer of the above diagram (Customer Site) provides sample scenarios of picture processing and storage:

  * A Webcampak can capture in RAW + JPG and send all pictures off-site,
  * A Webcampak can capture in RAW + JPG, save all pictures on a local redundant storage and send JPG pictures off-site,
  * A Webcampak can capture in JPG, and send all pictures off-site,
  * A Webcampak can capture in RAW + JPG, save all pictures on a local redundant storage and send a scaled down version of the picture off-site (for example 1920x1280 pixels).

If pictures are sent to Webcampak Cloud or to another Webcampak, they can go through another layer of processing.

A copy of all pictures processed by Webcampak Cloud is sent, for backup purposes, to RAID-5 redundant arrays located within our offices.

Webcampak can also send pictures to a third-party storage device. When this storage device is located within the photographer's office it ease access to pictures by progressively transferring them (instead of transferring all pictures at once at the end of the project).

Finally, Webcampak can send pictures (usually as "hotlink") to a remote website for public access.
