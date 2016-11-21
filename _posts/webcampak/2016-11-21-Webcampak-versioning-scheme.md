---
layout: page
subheadline: "Software"
title: "Webcampak versioning scheme"
date: 2016-11-21 10:00:00+00:00
teaser: "We recently did our second release of Webcampak 3, that's the ideal time to give a few more details about our new versioning scheme."
header:
    image_fullwidth: "webcampak-to-pictures.png"
    caption: Un de nos Webcampak de test
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

Two weeks after releasing Webcampak 3.0.0 we pushed a new version (3.0.1) and you probably wonder what is the significance of those versions numbers.

Increasing the last number means that those new features and bug fixes are non-breaking. For example migrating from 3.0.3 to 3.0.4 (1 version up) or from 3.0.3 to 3.0.7 (multiple versions up) should have a low level of risk.

Increasing the second number indicate potentially breaking changes. For example a modification of the data model for configuration files, which would impact currently configured sources. Migration to those version should then be done with caution (for example from 3.0.21 to 3.1.0). We'll try our best to document the changes so that this migration can be as smooth as possible.

Increaing the first number indicates a major Webcampak upgrade (change of the underlying GNU/Linux distribution, new feature impacting all components, ...). In this particular case it will probably be easier to re-install from scratch (for example when going from version 3.1.10 to version 4.0.0).

We hope those explanations were useful and will help you understand our versioning scheme.
