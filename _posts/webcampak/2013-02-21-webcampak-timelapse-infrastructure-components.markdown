---
layout: page
subheadline: "Tech"
title: "Webcampak infrastructure – Components (1/4)"
date: 2013-02-21 15:41:27+00:00
teaser: "Typical Webcampak deployments are composed by three different layers:"
header:
    image_fullwidth: "blog/2013/02/Webcampak-Typical-Install-blank-110-1024x961.png"
    caption: Webcampak infrastructure highlight
    caption_url: "http://www.webcampak.com"
image:
    thumb:  blog/2013/02/Webcampak-Typical-Install-blank-110-150x150.png
    homepage: blog/2013/02/Webcampak-Typical-Install-blank-110-1024x961.png
categories:
    - tech
comments: false
show_meta: true
redirect_from:
    - /en/2013/02/21/webcampak-timelapse-infrastructure-components/
---
  * On-site equipments, dedicated to initial picture acquisition and processing.
  * Central Webcampak Cloud infrastructure and its redundant storage.
  * Third party infrastructure.

[![]({{ site.urlimg }}blog/2013/02/Webcampak-Typical-Install-blank-110-1024x961.png)]({{ site.urlimg }}blog/2013/02/Webcampak-Typical-Install-blank-110.png)

But before moving forward, consider the above diagram as a small sample of a large set of possible deployment scenarios.

### On-site components

Webcampak can be directly connected to the Internet using a wired line (ADSL, Cable, Fibre) or wireless (Wi-Fi, 3G, 4G/LTE). In situations where Webcampak is the only on-site component and is directly connected to the Internet, performance of this Internet link will be a key to define possible deployment scenarios:

  * All pictures (RAW + JPG) can be sent off-site as far as the Internet link is reliable and fast enough to accommodate your planned capture rate. For example, sending JPG + RAW files, at one capture every 10 minutes, will require around 50 KB/s of bandwidth. In this situation, Webcampak local storage would allow a buffer of 70 days before the systems start to delete pictures to free storage space.
  * By capturing and sending only JPG pictures, at a rate of one picture every 10 minutes, only 10 KB/s of bandwidth would be necessary (T3I, T4I 18 Mpix), or with an upload speed of 1 Mbps (120 KB/s) capturing and sending one picture per minute. Webcampak local storage would allow a buffer of 370 days (1 picture every 10mn).
  * In situations with strong Internet constraints, only a scaled-down version (for example 1920x1280 pixels) of the picture could be sent for monitoring and live-view purposes. Full size pictures being stored inside Webcampak local storage.
  * Finally, the Internet link can be used for monitoring purposes only. In this situation bandwidth usage is very low.

Please consider that keeping pictures within Webcampak only might be risky. In the unlikely event of your Webcampak being stolen or compromised, you might loose all pictures not previously archived.

To avoid bandwidth constraints, still keeping high definition pictures, a local redundant storage device can be implemented.

This device would store, on-site, a copy of all captured pictures (RAW and/or JPG). We usually also install a hardware firewall to protect the customer's environment from Webcampak's network and to protect Webcampak's network from the customer's environment.

When a local storage is installed, Webcampak infrastructure can be configured to accommodate any bandwidth restrictions, by acting on picture size and frequency upon which pictures are sent to the Internet.

### Webcampak Cloud central components

Let's start with a reminder, Webcampak Cloud is not a mandatory component of a Webcampak deployment. Webcampak can be deployed independently from our central infrastructures.

Our central infrastructures are composed by:

  * Webcampak Cloud servers, hosted in France and in Canada. Those powerful servers are connected on high speed Internet links (100 Mbps) and equipped with RAID-1 redundant storage.
  * A monitoring platform (nagios), constantly checking status of all Webcampak components (including firewall, network storage, ...).
  * Redundant storage devices located within our offices and used to store all pictures transferred over to Webcampak Cloud. Using RAID-5 redundancy, those devices are here to protect us from a major datacenter incident.

### Third-party infrastructures

Any Webcampak component can interact with third-party infrastructures.

Pictures can be sent, after automated processing (crop, resize, watermark, legend, ...), to our customer's website to act as a "live-cam".

Pictures can also be sent automatically to a remote storage device (for example within photographer's office), allowing a fast and easy access to all pictures.
