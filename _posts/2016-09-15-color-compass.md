---
layout:     post
title:      Color Compass
date:       '2016-09-15 23:00'
tags:       [Arduino, compass, my-projects]
---

In addition to posting my more developed ideas in the form of (highly informal) research proposals, I'm working on documenting my completed projects as though they were (heavily abbreviated) scholarly papers. I find that it helps me keep focus. And it doesn't hurt that I dream of returning to academia at some point.

So I'll start with this project, my Color Compass.

<iframe src="https://player.vimeo.com/video/87629807?title=0&byline=0&portrait=0" width="720" height="405" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

Chances are I'll update this post with more detail. But I'd also like to prepare a build log or detailed instructions so that you can make your own.

## Abstract

Many animals and even plants exhibit _magnetoception_, an ability to sense magnetic fields, though it has been reasonably well established experimentally that humans don't. It is believed that, in at least some cases, magnetoception manifests within the organism's visual field. If magnetoception is in fact visual in nature, then it should be easy enough to augment the human visual sense with the capability of perceiving magnetism as well. Without building a whole mixed reality rig to overlay a grid or provide a heads-up display on the visual field [Terminator style](http://terminator.wikia.com/wiki/Head-up_display?file=T-800a_Night_Vision.jpg), I propose to provide that sense by simply presenting the user a color that corresponds to compass heading.

## Background

The [KidRobot Munny](https://www.kidrobot.com/collections/munny) is a do-it-yourself vinyl figurine for making one of a kind art toys. Most of the time, people color them with markers or paint. Sometimes they augment the figures with polymer clay, building ears, tails, and weapons. But most of these customizations have been along the same lines—making a figurine that sits on a shelf—impressive though they may be.

![KidRobot Munny](http://raritet-blog.s3.amazonaws.com/img/color-compass-07.jpg)

But, as an engineer, I thought "how can I make these interactive?"

Meanwhile, I read that some scientists believe that pigeons may see magnetic fields, possibly overlaid in their visual field. One theory is that a light-sensitive protein, called _cryptochrome_, found in the retinas of many animals is actually responsive to magnetic fields. Interestingly, it takes extremely strong magnetic fields to affect change in a "normal" chemical reaction (fields much stronger than that of the Earth). However, there is the case of something called a _radical pair_ wherein the fates of two electrons are entangled (yes, we're talking about quantum mechanics here), resulting in magnetic field-dependent outcomes of reactions with these radial pairs.

That lead to some daydreaming on my part about how that would work for a human. In the case of birds, though no one has been able to _see_ it for themselves yet, we have an idea of how the magnetic field might look.

Lastly, at more or less the same time, it occurred to me that hue in the HSL (hue, saturation, and level) color model, represented as an angle, is analogous to compass heading which is also represented as an angle. Why not display heading as a color on the color wheel?

On a more conceptual level, I've been interested for some time in using our existing senses at the edge of conscious awareness such that they provide a new form sensory perception. In other words, though the device described in this paper uses one's sense of sight, the user really gets an extra sense. The important part is that when we use an existing sense but become unaware of it (that is, at the edge of conscious awareness or beyond), we basically earn a new sense. In a way, this is not really a new concept—we've grown used to watches providing us with a more precise sense of time than we have biologically. As technology makes seamless human-machine interface easier and less expensive, we can expect these kinds of extrasensory perception to become more like senses and less like carrying a gadget around and looking at it from time to time.

## Implementation

Those of us that use computers for drawing likely know that colors can be represented in quite a few ways from a mix of red, green, and blue to an angle around the color wheel. The latter, often referred to as HSV (hue, saturation, and value) or HSL (hue, saturation, and luminance or level) represents colors as polar coordinates in a three-dimensional space. But if you just look at it in one plane, from above, you see the same old color wheel from elementary school art class, with red on top, or zero degrees; green on the lower right, or 120 degrees; blue on the lower left, or 240 degrees; and blending back to red again on top at 360 degrees. (For the pickier, more technically minded of you out there, you might know that the artists’ color wheel and the HSV color wheel are different, but for the purposes of this project those differences are small enough as to be irrelevant.)

Now, if you’ve ever watched a movie where pilots or ship captains bark out headings, you will have noted that they issue commands in degrees around the compass rose, where zero degrees is north, ninety degrees is east, 180 degrees is south, and so on.

Why not, then, make a color compass? If you’ve been maintaining mental images of the last two paragraphs, and can lay them on top of each other, you’ll see that red is north, yellow-green is east, aqua is south, indigo is west, easing through violet as we get back to north.

Note that in mathematics and engineering, angles are usually represented as increasing in a counterclockwise direction from the 3:00 position, while compass headings increase clockwise from north. In any case, if you line them up and flip them around, this is what you get.

From that point it was almost trivial getting the compass heading and converting it to an RGB combination to send to the LED. You can check out the code at the project's [GitHub repository](https://github.com/raritet/color-compass/blob/master/ColorCompass.ino) and follow along with the explanation.

![Color Compass illuminated](http://raritet-blog.s3.amazonaws.com/img/color-compass-08.jpg)

## Discussion

I have not provided this device to anyone other than myself to use for an extended period of time. So I do not have a lot of data on how people end up using it. That said, this is only a proof-of-concept; hence the cute appearance. An experimental setup would place the "guts" of a similar device in a wearable of some type, with the indication just visible within the user's field of view.

## Future Work

I've found that simply varying red, green, and blue proportionally around the compass rose does not result in a perceptually even range of colors. It seems that we see some colors as being further apart from or closer to each other than they would appear to be if viewed as simply a recipe of red, green, and blue proportions.

There is also the critical concept of gamma, which relates the perceived brightness of a light source to the actual quantity of light emitted (or more accurately landing on your retina). This is not yet implemented in the Color Compass. Because I don't have a nice mathematics renderer installed on this blog, here is how the relationship might look in a C-like language:

`brightness = pow(luminance, (1/gamma));`

A typical value for gamma is two, which is handy for quick calculations because `pow(luminance, 1/2)` is `sqrt(luminance)`.

"Quick" is a relative term, of course, and your microcontroller might not be able to calculate powers and roots in real time, in which case you would simply use a lookup table. (Lookup tables are almost always the right answer for low power embedded applications.) I should also note that working with gamma is a little different when we're talking about full RGB instead of just the brightness of a single light source. Again, a lookup table is ultimately the way to go in most cases, and can be fine-tuned on a computer and copied and pasted into an embedded program quickly.

![A peek inside the Color Compass](http://raritet-blog.s3.amazonaws.com/img/color-compass-04.jpg)

Another option might be to slide the hue of the user's entire field-of-view in the direction of the color associated with the heading; to provide a color cast over the image. We know that people can handle this sort of thing without losing their ability to see what color something actually is. For example, we deal with color casts from incident light while maintaining a pretty good idea what color things actually are (unless, presumably, it's a [black and blue—not white and gold—striped dress](https://www.wired.com/2015/02/science-one-agrees-color-dress/)). The user could even turn her head a little (presumably instinctively) to see how much of the color seen is due to the direction, using that to instinctively average out the color cast.

## Conclusion

Using color to convey heading is not really _useful_ in terms of communicating orientation precisely. But when used in conjunction with all the other senses, at a minimum it can make our sense of direction that much better.

So, to bring it back to the little fella in the pictures, the cute vinyl toy is not exactly at the edge of conscious awareness and hence doesn't really work to augment the senses as I've described above. It's really just a proof of concept (and why not throw in a bit of whimsy to make it interesting). But, imagine if the RGB LED could sit just outside your field of vision, casting a faint glow. If tuned right, it’s not hard to see that glow falling below your threshold of conscious awareness while still providing you with valuable information. That is the future of human-machine interface.
