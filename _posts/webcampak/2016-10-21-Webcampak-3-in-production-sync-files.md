---
layout: page
subheadline: "Software"
title: "Webcampak 3.0 in production - Sync files"
date: 2016-10-21 10:00:00+00:00
teaser: "Second blog post detailing Webcampak 3 features, we'll take a close look at the pictures sync features."
header:
    image_fullwidth: "webcampak-to-pictures.png"
    caption: One of our test Webcampak
    caption_url: "http://www.webcampak.com"
image:
    thumb:  webcampak-to-pictures_thumb.png
    homepage: webcampak-to-pictures.png
categories:
    - corporate
    - software
comments: false
show_meta: true
---

## Sync'ing files

A new module called "Sync-Reports" has been created specifically to answer the following use cases:

* Verify that all pictures have properly been sent to a remote server 
* Add a new remote server and send all pictures there
* Re-send any missing pictures to a remote server

### How it works

It's actually a pretty simple feature, users can request a report and the Webcampak will compare files between two locations using, for each file, it's name, location and size. 

The Webcampak will provide the user with a short report showing number of missing files and corresponding size. This report can then be used to transfer missing pictures.

### Create a report

When creating a sync report, the user select the source and destination to be compared.

[![]({{ site.urlimg }}webcampak.sync.create_600x196.png)]({{ site.urlimg }}webcampak.sync.create.png)

The report is then placed in a queued and processed by the system.

[![]({{ site.urlimg }}webcampak.sync.queue_600x271.png)]({{ site.urlimg }}webcampak.sync.queue.png)

### Analysis of a report

The report display details about pictures available in source and destination, with count and size of files either in one, or the two locations.

[![]({{ site.urlimg }}webcampak.sync.large_600x232)]({{ site.urlimg }}webcampak.sync.large_600x232)

To transfer missing pictures, the user just has to click on ""Re-run & Sync" to initiate the transfer.
