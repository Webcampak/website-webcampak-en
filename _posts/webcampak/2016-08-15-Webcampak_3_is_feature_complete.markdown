---
layout: page
subheadline: "Corporate"
title: "Webcampak 3.0 is feature complete"
date: 2016-08-15 10:00:00+00:00
teaser: "It took us almost 18 months to get there, but Webcampak is now feature complete and we are getting ready for integration testing."
header:
    image_fullwidth: "header_typewriter.jpg"
    caption: Image by Florian Klauer
    caption_url: "http://florianklauer.de/"
image:
    thumb:  typewriter_thumb.jpg
    homepage: homepage_typewriter.jpg
categories:
    - corporate
comments: false
show_meta: true
---

As you might have noticed, the upgrade to v3.0 took us much longer than planned. During this migration we have been re-writing almost all of Webcampak core components.

## Internal changes

### User Interface
The UI has been entirely rewritten to be more modular, structured and to facilitate the addition of new features. We are still using Sencha framework but migrated from Extjs 4.x to Extjs 6.x.
The Sencha Touch component (mobile interface) has been replaced by Extjs 6.x modern UI.

### API
The previous API was based on a custom PHP framework, it has been entirely rewritten and is now based upon Symfony and uses Doctrine for the ORM part.

## CLI / Core
Webcampak CLI takes care of captures and internal processing, it has been rewritten as well to clean the code and wrapped by the CLI framework Cement.

### Database

We are doing our best to limit database usage, but it remains necessary for authentication and authorization. The database has been migrated from MySQL to SQLite to make everything a bit lighter (we were not using most of MySQL features anyway). 

## Features

You're probably much more interested by new features and changes impacting your day to day usage. We'll write further blog posts on this topic, but to make things short, we've been focusing on simplifying incident management and ease management of a fleet of Webcampaks.

### Sync Reports
This feature allows a webcampak to compare pictures stored locally with pictures located on a remote server. If differences are found, the user can decide to transfer missing pictures.
Those reports can be generated at anytime, for example to synchronize a large number of pictures after a network incident.

### Xfer
The Xfer feature is a queue mechanism for file transfer. Previously, transfered was serialized with its associated action (picture acquisition, video creation). The Xfer feature allows you to run transfer in parrallel of other Webcampak activity with no risk of saturation (if configured properly).

This will allow you to configure burst capture session, capturing at a higher rate than what your Internet bandwidth would allow. Files being transferred at their own rate by the Xfer queue. 

### Emails
Email behavior has also been revamped (although we still have a couple of improvements in the pipe), for users operating multiple Webcampak, the system can send one single email (instead of one email per source).

### New mobile/tablet interface
A new mobile/tablet interface has been developed, it provides more details about captures and allows a few more simple manipulations. 

## What next ?

Now that all features have been added, we'll be starting to debug and ensure Webcampak 3.0 is ready for production. A big step forward !
