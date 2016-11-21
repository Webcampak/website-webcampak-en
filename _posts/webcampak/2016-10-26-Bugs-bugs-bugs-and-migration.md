---
layout: page
subheadline: "Software"
title: "Bugs, Bugs, Bugs... and migration."
date: 2016-10-26 10:00:00+00:00
teaser: "Before any deployment to production we test all components as much as possible. But sometimes things do not go as planned..."
header:
    image_fullwidth: "webcampak-to-pictures.png"
    caption: One of our Test Webcampak
    caption_url: "http://www.webcampak.com"
image:
    thumb:  webcampak-to-pictures_thumb.png
    homepage: webcampak-to-pictures.png
categories:
    - bug
    - software
comments: false
show_meta: true
---

As you might know, we are currently migrating our cloud servers to Webcampak 3. Tests are complete and the system is now ready for  deployment.

## Migration Strategy 

We have a couple of terabytes of files to be transferred between our servers, to limit incidents and interruption for our clients we are doing an active/active migration.

The workflow is as follow; we install Webcampak on a new server, duplicate all files, reconfigure on-the-fields Webcampak to send pictures to the new server instead of the old one, then synchronize all missing pictures between the two servers.

This workflow limit the risk of interruption and also allows us to easily roll-back in case of issues.

But sometimes things do not go as planned...

## Sync'ing pictures

Now that we have our new feature to sync files, we decided to use it instead of using [Rsync](https://fr.wikipedia.org/wiki/Rsync) as we were before. 

There is no question that using Rsync would have been easier and faster, one single command to copy all resources from one server to another. But this is also a great opprotunity to run some load tests on our systems (we were limiting ourselves to a couple of GB during our integration tests).

## A large number of pictures

And this is when things do not go as per the plan ...

The impact though it fairly limited and completely transparent to our clients. But this highlighted an aspect we did not validate, we did test with a couple thousands files, more precisely the 8640 pictures captured during 2011 "Vielles Charrues" festival.

No issues during those tests, in both directory (local to remote and remote to local).

So to get back on topic, the next step was to transfer a source from a running project, and we started with one with 58,300 pictures and over 200GB (see below).

[![]({{ site.urlimg }}webcampak.sync.large_600x232.png)]({{ site.urlimg }}webcampak.sync.large.png)

Being confident everything would work fine, why not sync multiple clients in parrallel.

And the... the reports UI became unrachables, impossible to visualize any report, all replaced by API error messages.

## An easy diagnosis

Finding the root cause of the issue was not really difficult.

To improve reactivity and save on system resources (in particular for on-the-field systems), we tend to give a higher priority in collecting and storing metrics, versus calculating those "on-the-fly". Disk space for those is usually very limited, but in thise particular case, we were storing way too much data.

The report was holding the list of files on the source, on the destination, shared in both location, missing on the source and missing on the destination.

Way too mych, especially since for now, only files missing on the destination (files to be transferred) are relevant to us.

The solution was then simply to remove unnecessary data, and compress (GZip) the list of missing files in a dedicate file (this list only being used once). Keeping in the main report only statistics.

A few lines of code later, and less data in our reports, their filesize went from 70MB to 1.7MB.

We could have pushed a bit further, without keeping the list, lowering our report size to about 3.9K but we would have lost an historical data that might become useful in the future.

Here was our bug properly eradicated, we can resume our activities.
