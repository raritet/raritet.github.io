---
layout: post
title: Digital CV
date: 2011-05-07 21:28
author: coherentnoise
comments: true
categories: [analog, electronics, music, My Music]
---
CV, or control voltage, is used in analog synthesizers, sort of like, but different from, the MIDI protocol that electronic musicians of my generation know and love. CV, however, seems to be the new cool thing at least partly because it's exotic in this age of iPads and the such.

While thinking about this I realized that CV might be more useful (read easier) for tiny digital microcontroller-based synthesizers. Let me amplify: Rather than try to parse a MIDI stream, an Arduino could poll a few A/D converters and convert those values straight to pitch, volume, whatever. This may upset some analog purists, but I think it could open a new world of CV-based organic randomness, even though the core equipment is digital. Rather than being a weak attempt at analog emulation, it's just a completely new concept more along the lines of circuit bending.

Then, that gave me another idea. It seems that it should be easy enough to create a control voltage "filter" gadget that could be loaded up with an arbitrary transfer function allowing for all manner of madness. And I mean not just something easy like "the output is the square of the input" or whatever, but an actual s-domain (or I guess, really, z-domain) transfer function. So it could dampen an LFO depending on its frequency or "ring" after a particularly sharp attack envelope or whatever. Or maybe it could phase shift a pulse train or LFO by an arbitrary amount if that's what you need.

Now, after a bit of research I might find that this exists already. But until then, let's see what we come up with.

By the way, <a title="From a Little Droid to a Big Moog Taurus Pedal, Analog to Digital, More Experimental Sound Tips" href="http://createdigitalmusic.com/2011/04/from-a-little-droid-to-a-big-moog-taurus-pedal-more-experimental-tips/" target="_blank">this post</a> on <a title="Create Digital Music" href="http://createdigitalmusic.com/" target="_blank">Create Digital Music</a> is what really got me on this analog kick.
