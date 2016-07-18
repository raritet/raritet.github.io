---
layout:     post
title:      Analog TV Digital Picture Frame
date:       '2016-07-16 22:00'
tags:       [raspberry-pi, my-projects]
---

![TV on with Picture of Structure](http://raritet-blog.s3.amazonaws.com/img/dig-pic-frame-08.jpg)

I've always been interested in new technology that could have existed years ago. For example, the household TV could have been used since at least the 1980s to display family pictures. Imagine a service that takes your photos, scans them, and sends you back a VHS tape to play over and over again.

![Closeup of Screen](http://raritet-blog.s3.amazonaws.com/img/dig-pic-frame-10.jpg)

I don't recall ever seeing such a service, though I was too young to have been in the market for it anyway. But that idea really makes the most sense in the context of the modern day, where we can buy digital picture frames on impulse at the drug store.

![Closeup of Dials](http://raritet-blog.s3.amazonaws.com/img/dig-pic-frame-03.jpg)

And in that context the idea of using an analog TV as a picture frame is ironic. Or amusing. Humor is a big factor in many of my projects. So fast forward to now and, partly as a proof of concept and partly just to amuse myself, I built this:

<iframe src="https://player.vimeo.com/video/87426740?color=ffffff&title=0&byline=0&portrait=0" width="720" height="405" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

Ahh, gotta love how it warms up like that before you see the snow. And snow! Analog noise seems so nice (visually and aurally) when compared to today's digital glitches. I wonder if in a few years we will look back longingly at digital glitches.

Anyway, I made this particular implementation around a readily available single board computer about the size of a credit card, the [Raspberry Pi](https://www.raspberrypi.org/), and a few other odds and ends to tie it all together. The system wirelessly downloads new photos from an album on my (or any) Flickr account and displays them on the screen in a random order.

![Closeup of Screen and Knobs](http://raritet-blog.s3.amazonaws.com/img/dig-pic-frame-09.jpg)

You might have noticed that pictures of the actual device are conspicuously absent. I threw the thing together pretty quickly, but I really need to document the build and I hope to update this post (or make another) soon. In any case, the business end resides in a bundle about the size of two packs of playing cards, along with another bundle of wall-wart power supplies, strapped together along the power cable. In a future implementation, such as for a gallery setting, I‘ll place the entire assemblage directly inside the TV. I expect to have to remove the individual components from their enclosures and wire them directly together, wrapping them in insulating tape or potting them in epoxy to let them sit safely among the high voltage components in the TV.

![TV Off](http://raritet-blog.s3.amazonaws.com/img/dig-pic-frame-01.jpg)
