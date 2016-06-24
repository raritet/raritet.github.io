---
layout:     post
title:      Color Compass
date:       2016-06-24 13:00
categories: [My Projects]
tags:       [Arduino, compass]
---

In addition to posting my more developed ideas in the form of (highly informal) research proposals, like this one, I'm working on documenting my completed projects as though they were (heavily abbreviated) scholarly papers. I find that it helps focus the mind a bit. And it doesn't hurt that I dream of returning to academia at some point.

## Abstract



## Introduction



## Background

The KidRobot Munny is a do-it-yourself vinyl figurine for making one of a kind art toys. Most of the time, people color them with markers or paint. Sometimes they augment the figures with polymer clay, building ears, tails, and weapons. But most of these customizations have been along the same lines; making a figurine that sits on a shelf, impressive though they may be.

But, as an engineer, I thought "how can I make these interactive?"

Meanwhile, I read that some scientists believe that pigeons may see magnetic fields, possibly overlaid in their visual field. That lead to some daydreaming on my part about how that would work for a human.

Lastly, at more or less the same time, it occurred to me that hue in the HSL (hue, saturation, and level) color model, represented as an angle, is analogous to compass heading which is also represented as an angle. Why not display heading as a color on the color wheel?

On a more conceptual level, I've been interested for some time in using our existing senses at the edge of conscious awareness such that they provide a new form sensory perception. The important part is that when we use an existing sense but become unaware of it (that is, at the edge of conscious awareness or beyond), we basically earn a new sense. In a way, this is not really a new concept—we've grown used to watches providing us with a more precise sense of time than we might have biologically. As technology makes seamless human-machine interface easier and less expensive, we can expect these kinds of extrasensory perception to become more like senses and less like carrying a gadget around and looking at it from time to time.

## Related Work

## The Meat

Those of you who use computers for drawing likely know that colors can be represented in quite a few ways from a mix of red, green, and blue proportions to an angle around the color wheel. The latter, often referred to as HSV (hue, saturation, value) or HSL (hue, saturation, luminance) represents colors as polar coordinates in a three-dimensional space. But if you just look at it in one plane, from above, you see the same old color wheel from elementary school art class, with red on top, or zero degrees; green on the lower right, or 120 degrees; blue on the lower left, or 240 degrees; and blending back to red again on top at 360 degrees. (For the pickier, more technically minded of you out there, you might know that the artists’ color wheel and the HSV color wheel are different, but for the purposes of this project those differences are irrelevant.)

Now, if you’ve ever watched a movie where pilots or ship captains bark out headings, you will have noted that they issue commands in degrees around the compass rose, where zero degrees is north, ninety degrees is east, 180 degrees is south, and so on.

Why not, then, make a color compass? If you’ve been maintaining mental images of the last two paragraphs, and can lay them on top of each other, you’ll see that red is north, yellow-green is east, aqua is south, indigo is west, easing through violet as we get back to north.

Note that in mathematics and engineering, angles are usually represented as increasing in a counterclockwise direction from the 3:00 position, while compass headings increase clockwise from north. In any case, if you line them up and flip them around, this is what you get.

From that point it was almost trivial getting the compass heading and converting it to an RGB combination to send to the LED.

## Discussion

I have not provided this device to anyone other than myself to use for an extended period of time. So we do not have a lot of data on how people end up using it. That said, this is only a proof-of-concept; hence the cute appearance. An experimental setup would place the "guts" of a similar device in a wearable of some type, with the indication just visible within the user's field of view.

## Future Work

## Conclusion

So, the cute vinyl toy is not exactly “at the edge of conscious awareness.” It’s really just a proof of concept (and why not throw in a bit of whimsy to make it interesting). But, imagine, the RGB LED could sit just outside your field of vision, casting a faint glow. If tuned right, it’s not hard to see that glow falling below your threshold of conscious awareness while still providing you with valuable information. That is the future of human-machine interface.

## Acknowledgements

I should thank my family for putting up with me as I work on strange, apparently useless projects.
