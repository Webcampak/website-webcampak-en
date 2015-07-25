---
layout: page
subheadline: "Roadmap"
title: "Webcampak 3.0 - Development on track"
date: 2015-04-24 19:07:50+00:00
teaser: "A lack of updates on the blog does not necessarily means a lack of activities on Webcampak. The third major Webcampak revision is currently being implemented and will bring a large set of new features and improvements."
header:
    image_fullwidth: "blog/2015/07/webcampak-login-large.png"
    caption: Webcampak lost password screen
    caption_url: "http://www.webcampak.com"
image:
    thumb:  blog/2015/07/webcampak-login_150x150.jpg
    homepage: blog/2015/07/webcampak-login-large.png
categories:
    - software
comments: false
show_meta: true
---
Among those changes, we are re-building the interface from scratch in order to bring even more control and autonomy to our clients. By using our advanced REST API, each Webcampak will be able to act as its own webcampak control centre.

[![]({{ site.urlimg }}blog/2015/07/webcampak-sources_600x420.png)]({{ site.urlimg }}blog/2015/07/webcampak-sources.jpg)

A few years ago Webcampak became a cloud product, it is now progressively entering the "BigData" field.

We are also going to improve file transfer, and in particular in critical situations (such as capture rate higher than what the bandwidth can accommodate). Our existing processes warn us in case of issues and our cache allows for a couple of day of additional capture with no interruption. But some manual actions were still necessary to re-sync data once everything was back online. We are going to teach Webcampak how to identify the end of a critical period and when to re-initiate file synchronization.

In terms of hardware, we are going to lower power consumption, natively support 4G/LTE, and probably develop an even smaller enclosure.

Many other features will come, stay tuned.

{% include list-posts.html tag='header' %}
