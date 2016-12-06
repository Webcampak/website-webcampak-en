---
layout: page
subheadline: "Software"
title: "Automated Alert mechanisms"
date: 2016-12-01 10:00:00+00:00
teaser: "Success of a timelapse project strongly depends on the ability of the technical platform to prevent picture loss. Alert mechanisms play a strong role by sending alerts about possible capture issue (camera malfunction, loss of power, loss of network connectivity). In this blog post we are going to detail how  Webcampak deals with this along with recent improvements implemented for Webcampak 3."
header:
    image_fullwidth: "webcampak-to-alerts.png"
    caption: Webcampak Alerts Configuration
    caption_url: "http://www.webcampak.com"
image:
    thumb:  webcampak-to-pictures_thumb.png
    homepage: webcampak-to-alerts.png
categories:
    - alertes
    - software
comments: false
show_meta: true
---

Very early on in the project, we realized than implementing an alert management mechanism was as critical but also complex to setup. Too many alert lessen the sense of urgency (it create some sort of habits), too little might result in picture loss.

# Webcampak 2

In earlier Webcampak version, alerts were serialized with image capture, this made it very efficient. Configuration as done in three steps:
* Define a threshold after which an alert should be sent (after X capture failures)
* Define how frequently to send reminders
* Define if an email should be sent anytime capture transitions from failed to operational (even if capture is less than threshold).

This resulted in a very simple implementation for sources directly connected to a camera, capture was working or not working, as simple as that.

But this setup also highlighted a lack of flexibility for centralization sources, in particular remote ones. For example, a Webcampak on construction site would capture at two different frequencies and sent its pictures to our Cloud. How to deal with this schedule variation and still accommodate possible delays caused by the network ?

To prevent false positive from being sent, the configuration had to be very precisely setup.

# Webcampak 3

For Webcampak 3, we've been thinking at a better way to make this system more flexible. Starting in Webcampak 3, two configuration modes are available for email alerts:

* Based on capture delays
* Based on a calendar

## Based on capture delay

This mode is the simplest to configure and remains very similar to Webcampak 2. At regular interval the system will calculate the time since last capture. If this time is above the pre-configured threshold an alert it sent.

The system then keep checking the status, and sends a reminder at a pre-configured interval.

## Based on a calendar

The second most required the user to pre-define a weekly capture calendar, the system then constantly verify that pictures are captured at their expected slot.

By configuring a threshold based on the number of failed pre-configured capture slots, this system allow for much finer grain and subsequently supports an unlimited number of capture frequencies.

Similar to the other mode, the system is able to send reminders at regular interval. A "Grace" period can be configured to delay the time at which an email should be sent, to accomodate for possible network delays.

## Two compatible modes

Those two modes can be used simultaneously. It is for example possible to configured the system to trigger alarms based on the calender but send reminders based on a delay since last email.

# Conclusion

This new feature will make the alert mechanism more flexible and better accomodate remote sources. Couple with daily capture statistics, it will become virtually impossible to miss pictures.
