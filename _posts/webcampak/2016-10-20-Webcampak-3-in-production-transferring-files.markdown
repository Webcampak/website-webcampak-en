---
layout: page
subheadline: "Software"
title: "Webcampak 3.0 in production - Transferring files"
date: 2016-10-20 10:00:00+00:00
teaser: "Since mid-August we were testing Webcampak 3 to ensure its proper operation before starting to use it in production."
header:
    image_fullwidth: "webcampak-to-pictures.png"
    caption: One of our test webcampak
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

After many installations, reboots, hard shutdown (controlled and not) we now have a system as reliable and stable as the previous version but bringing along quite a few improvements.

This blog post will be the first of a serie detailing new Webcampak features

## Transferring files

Webcampak 3 has two modes of transferring files:

* __serial__ mode, sending pictures as soon as they are captured. 
* __xfer__ mode, queuing files to be sent by another process running in the background. 

Those two modes are using FTP, but we could easily implement new communication means.

[![]({{ site.urlimg }}webcampak.xfer.to_600x194.png)]({{ site.urlimg }}webcampak.xfer.to.png)

The new __xfer__ mode is a solution to two types of difficulties we've been having on our project, a temporary burst in our capture rate, preventing all pictures to be transmitted or a temporary drop in network performances.

### Bursting capture rate

In some project phases, our client want to strongly increase capture frequency (for example one picture every 20 seconds as a crane is being installed). When using a Webcampak with serial transmission mode, to avoid performance issues, we had to ensure that the full capture process was completed before starting a new one. And in some cases network connectivity was the limiting factor. 

On pre-webcampak 3 version, it did not represent a major issue since it was possible to temporarily suspend picture upload (our Webcampak usually have between 220GB and 500GB of local storage), but it required some manual intervention to re-sync pictures.

This new __xfer__ mode remove the need of those adjustments, the system will simply queue pictures and send them as the bandwidth permit it. 

### Drop in network performances

This issue is actually the trickiest to work with and hard to plan because not related to our infrastructures. A drop of network connectivity is easy to work with, it simply doesn't send pictures, and does not create stress on the system. But a strong drop of performance is more difficult to work with. Transmission is actually not failing, just taking much, much, much longer than usual. In some situations it was creating stress on the system, which ended up transmitting a large number of files at once.

Since pictures were actually being sent (although slowly), the Webcampak had no clue something wrong was happening and was continuing to capture and try to send pictures until it ran out of resources (which would usually take a couple of days).

### Xfer mode

When thids mode is being used, multiple queues are created, each of those queues will receive a transfer request. Transfer queues are shared on the entire system but still isolated from individual sources (a source submit a request to the queueing system, which then dispatch the job to a queue).

[![]({{ site.urlimg }}webcampak.sysconf_600x218.png)]({{ site.urlimg }}webcampak.sysconf.png)

Setup happens at multiple levels, during general configuration, we indicate how many transfer queues should be supported by the system. The more queues there are, the greater the number of files to be transferred in parrallel. We also indicate how many files each queue can hold.

Those settings will differ based on the type of hardware used for Webcampak. A 12-core Intel Xeon based Webcampak cloud supporting 50 on-the-field systems will have settings very different from an on-the-field system installed on a construction site.

Then each time a new remote server is added, users can enable the Xfer mode and select how many queues can be used for this particular remote server.

The queueing mechanism will then spread the load amongst all queues according to selected configuration settings.

[![]({{ site.urlimg }}webcampak.xfer.to_600x194.png)]({{ site.urlimg }}webcampak.xfer.to.png)

For example, on the above screenshot, you can see that the system has 3 queues, but only 2 are being used.

### Pros & Cons 

The Xfer system is particularly interesting in situations where bandwidth might be low or unstable, if capture frequency is lower over night time, the system can then use night-time to finish sending pictures captured during the day.

It is also useful at time where a large number of files needs to be synced between two systems. The system will evenly spread the load, giving 50/50 priority between a capture source and the sync job.

On the other hand, it can involve a slight delay in sending pictures (for example if the queue for a particular source is already filled) as well as a slight increase of local resources use.

We would recommend using the xfer mode in most of the use cases and keep the serial transfered mode for some specific type of usage, such as sending live pictures to a remote website.
