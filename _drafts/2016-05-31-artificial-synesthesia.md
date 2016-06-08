---
layout: post
title: Artificial Synesthesia
date: {}
published: true
---

This post has been a good while in the making. For maybe a year or so, I've been mulling an idea for a novel application of augmented reality systems. (I've actually been mulling several ideas, but this one is perhaps the most exciting to me at the moment.) After a good bit of research, it's pretty clear to me that the programming required is beyond my ability to perform on evenings and weekends—those of which are free of other obligations, no less. So, I'm going to present my research to-date here, summarized loosely in the form of a (very informal) research proposal. And over the next few weeks and months I'll free other ideas from the confines of my notebooks in similar form.

---

## Abstract

Synesthesia, the crossing in perception of one sense with another (think scents having color or sounds manifesting with a tangible texture), is a trait shared by perhaps four to five percent of people. In popular literature, synesthesia is often anecdotally considered beneficial to creativity, priming the mind with hard-wired metaphor. If synesthesia is in fact beneficial to creativity, an augmented- or mixed-reality system designed to mix senses could provide non-synesthetes with nearly instinctive capabilities for metaphor and all the creative benefits that arise therein. In this proposal I focus on the design of a system for simulating grapheme-color synesthesia. However, there are many other forms of synesthesia equally amenable, or perhaps more amenable, to implementation through an augmented reality system. In the most general terms, what I propose is simply a novel extension of human senses, as machines have been providing us for many years.

---

## Introduction

Augmented reality (AR) and now mixed reality (MR) are the new cool thing, as those of us in [the tech world have no doubt noticed](http://www.wired.com/2016/04/magic-leap-vr/). No one can disagree that this technology will be useful for all the obvious things like heads-up displays of contextually useful information. But to me that has always seemed _boring_, for lack of a better term. Perhaps it's because it's obvious; _Of course_ you would display relevant facts next to what you are looking at through your MR headset. That's what they've been doing in every cyborg movie for who knows how long. For that matter, Thad Starner pioneered this in real life with the [predecessor to Google Glass](http://archive.boston.com/business/technology/innoeco/2012/07/the_mit_roots_of_google_glass.html) during his time at the MIT Media Lab back in 1993.

To me the real neat stuff is when you come up with an entirely new use case. I think I have thought of one.

Synesthesia is a neurological phenomenon wherein the stimulation of one sense (or more generally one _cognitive pathway_) stimulates another. Imagine a situation where you see the letter 'S' and it has a iridescent, swirly blue tint perceived simultaneously with whatever color the letter was printed in. In other cases, synesthetes (that is the name for people who exhibit synesthesia) may hear a pitch or timbre in music and _feel_ a very real sense of its texture; perhaps prickly, or soft like blades of grass under one's hand.

The locations of the brain corresponding to the perception of the senses involved in a particular case of synesthesia are typically physically adjacent. Researchers therefore theorize that synesthesia may be as simple as brain activity spilling out of one sensory region and into adjacent regions.

There is a seemingly high concentration of synesthetes among the world's most creative people. I've heard synesthesia described as an instinctive form of metaphor. Perhaps what a "normal" person thinks is an incredibly imaginative metaphor is simply the way the writer sees the world on a neurological level. Many believe that synesthesia is also common in children, though they do not often have the facilities to communicate it or the mentorship to nurture it. If synesthesia is in fact common in children, it may, at least in part, explain the nature of their highly active imaginations. In any case, examples of synesthesia exist in our daily language, even among non-synesthetes, such as the timbre of a musical instrument being dark or bright, or even things like _sharp_ cheddar cheese.

---

## Background

While reading about Vladimir Nabokov's particular case of grapheme-color synesthesia—the condition in which one sees letters with color—it seemed to me like it should be pretty straightforward to build an augmented reality app to simulate it for those of us not fortunate enough to have been endowed with such a gift: Run the video stream of a cell phone camera through an OCR (optical character recognition) program to find text within the field of view, outline each letter, and fill those outlines with the color called for on a lookup table.

It turns out that implementing this is not as straightforward as I thought. In basic AR applications the developer trains a computer vision (CV) library such as [OpenCV](http://opencv.org/) with an image called a "fiducial marker." OpenCV then looks for this image in the video stream and can overlay something on top. This fiducial marker often has a geometric pattern such that its orientation in space is easily determined, allowing the overlay to make sense in three-dimensions. There are several toys and [video games](http://www.nintendo.com/3ds/ar-cards) that make use of this, with three-dimensional characters rendered on a playing field.

I had hoped to more or less replace the fiducial marker used in AR applications with the output of an OCR library; and I suspect that might still be possible. But, as far as I can tell at this point, the gold standard open source OCR library, [Tesseract](https://github.com/tesseract-ocr), doesn't work like that. Rather, it just outputs the characters corresponding to the text it finds in the image.

Other ideas included training the CV library with hundreds or thousands of fiducial markers; one for every letter in every common typeface. However, that will likely be very computationally intensive. And it seems outright inelegant when we know that OCR software exists.

In terms of hardware, as noted above, in my original concept the device would simply be a cell phone running an AR app developed in [Unity](https://unity3d.com/) or something similar, but with an OCR library providing the fiducial marker in real time instead of OpenCV finding it in the video stream. For a more immersive experience, MR hardware like Microsoft's [HoloLens](https://www.microsoft.com/microsoft-hololens/en-us) or the [Magic Leap](https://www.magicleap.com/) device are particularly exciting. The fact that grapheme-color synesthetes see both the visual color of the text and the synesthetic color of the text is perfect for the MR devices. On those systems the user sees the projected images as slightly translucent, with the real world still there in the background. (I should note that "projected image" is probably not the correct term to use for these light-field based systems.)

---

## Approach

### How the System Works

On the input end, a computer receives a video stream of the scene. This is processed as a series of images and, in the case of a virtual reality (VR) or cell phone based system, passed through to the output screen.

That video stream is also passed to the OCR subsystem, which analyzes each frame of video (or every nth frame of video as needed to accomodate the algorithm and the hardware) for text characters anywhere in the field of view. When the OCR subsystem locates letters, it sends closed vector outlines of those letters, along with information as to which letter is represented, to something which will overlay the video. For the most authentic experience, the OCR subsystem should process frames at a rate comparable to that at which a person can recognize a letter in her visual field.

The video overlay subsystem takes the vector outlines of the letters and fills them with the appropriate color based on the attached letter information compared against the lookup table. Speaking of lookup tables, here is one I compiled from Nabokov's description of his grapheme-color synesthesia in his autobiography:

| Letter | Color | RGB Value | Notes |
| :---: | :--- | :---: | :--- |
| _a_ | weathered wood | * | I take this to mean the _æ_ sound like "at" or "that." Nabokov says this is in the black group. |
| _a_ | polished ebony | * | The French _a_, which I assume is the phonetic _a_. |
| _b_ | burnt sienna | * | |
| _c_ | light blue | * | |
| _d_ | creamy | * | In the yellow group. |
| _e_ | yellow | * | |
| _f_ | alder-leaf | * | |
| _g_ | vulcanized rubber | * | Specifically a hard _g_. |
| _g_ | rich rubbery tone | * | This is the soft _g_, and is in the brown group. |
| _h_ | drab shoelace | * | Also in the brown group. I guess it's a dirty shoelace. |
| _i_ | yellow | * | |
| _j_ | rich rubbery tone | * | Similar to the soft _g_, but paler. |
| _k_ | huckleberry | * | |
| _l_ | noodle-limp | * | |
| _m_ | a fold of pink flannel | * | |
| _n_ | oatmeal | * | |
| _o_ | ivory-backed hand mirror | * | |
| _on_ | the brimming tension-surface of alcohol in a small glass | * | The French _on_, which I assume is nasalized. |
| _p_ | unripe apple | * | |
| _q_ | browner than _k_ | * | This must be blue, still, but somehow "browner." |
| _r_ | sooty rag being ripped | * | This will be interesting to convey simply as a color. |
| _s_ | a curious mixture of azure and mother-of-pearl | * | This is partly to show that shape matters in color in addition to sound. |
| _sh_ | fluffy-gray | * | |
| _t_ | pistachio | * | |
| _u_ | brassy with an olive sheen | * | Also in the yellow group. |
| _v_ | rose quartz | * | |
| _w_ | dull green, combined somehow with violet | * | |
| _x_ | steely blue | * | |
| _y_ | bright-golden | * | |
| _z_ | thundercloud bluish | * | | 

\* _I am working on selecting RGB values and may ultimately select a different method to store the color. This is particularly important for the colors that Nabokov describes with motion or texture, such as those for 's' and 'a.'_

Finally, the overlay is mixed back in to the video stream and displayed on the screen. Even though we are talking about video of the "real world," you can see from the signal flow described above that this is all still a two-dimensional system (at least when implemented as a simple cell phone based AR app).

In the case of the MR systems, the signal flow must account for the third dimension so that the letter's color overlay shows up on top of the letter in space and not just as paint on a screen. This is obviously very important for MR systems and is implemented in the Microsoft HoloLens with something they call "environment understanding cameras" providing [spatial mapping](https://developer.microsoft.com/en-us/windows/holographic/spatial_mapping). In this case I can use the spatial mapping to tell my program where in three dimensions a piece of text is, and more importantly the orientation of the plane that text is written on. The the color fills can be drawn in the same plane.

### Software Implementation and Problems

Given the problems discussed in the Background section, based on my current research it appears that I will have to explore the innards of the Tesseract OCR library to extract the needed outline information. It is my understanding that Tesseract finds outlines—or uses outlines—to make a judgment as to what text is represented. But it is not clear that that process is made transparent enough to reach in and play with intermediate steps.

I suppose another problem will be determining if something is in fact text. Otherwise, my program might just end up demanding that Tesseract make a guess as to what text an outline represents, whether it actually is text or not. That will lead to all sorts of funny results with random color areas all over the view. That is not necessarily a bad thing, and could provide the user with something like _artifical imagination_ as a row of light poles starts to look like a string of capital 'I's or lowercase 'L's. In fact, this idea warrants further study as a separate concept.

But if we want to stick with the clean artificial synesthesia implementation, we need to remove the noise. If Tesseract provides a certainty of its output (another pending research question), we can use that to determine whether we should in fact apply a color overlay at a particular location. If not, we will again have to reach in to the library and see if we can find some variable somewhere that we can use to make some sort of judgment on the quality of the character recognition.

Aside from the character recognition problems, the 3D programming aspect of the system, though difficult, seems at this point to be "straightforward" in that what we want to do, essentially just drawing planes in three dimensions, is not new or unusual.

### Other Considerations

Taking a look at the grapheme-color table a few paragraphs above, it looks like I might need to take a little artistic license in the implementation. Nabokov certainly took some artistic license, piling synesthetic descriptions on top of synesthesia (see _on_ in particular).

Also note that many of these letters rely on the sound, or the phoneme, and not just the shape of the letter (the grapheme). (I believe they should call this phoneme-color synesthesia instead of grapheme-color, but that's neither here nor there.) So to really get this right, the OCR algorithm would also need to look at the word, extract the sounds, and map them back to the letters. But for a proof-of-concept we don't need to do that right now.

---

## Future Work

In future implementations, the color overlay step of image processing could include some more "life," perhaps animating a swirly, colored cloud within the outlines to really get the user to see things vividly like the original synesthete.

Speaking of "original synesthete," imagine being able to load up some particular famous synesthete's "program" in your MR headset and see the world through their eyes. When you're done with Nabokov, just load up the program for Nikola Tesla, or Wassily Kandinsky, or whoever (to the extent that we have enough infomration to recreate their synesthesia). One could even license her synesthesia description, providing artists a form of income.

Of course grapheme-color synesthesia is not the only type. Chromesthesia, when sounds trigger a color sensation, could be relatively easily implemented in an MR headset. In fact, I probably should have started with that one since many chromesthetes (I just made that word up, I think) report that the visual phenomena show up as though projected on a screen. Notably, many, or perhaps all, MR systems have a sense of the user's gaze, so they can tone down or relocate the visual manifestations away from where the user is looking. This ensures that the chromesthesia does not interfere with normal visual function.

Some other interesting synesthesiae (I think I made that word up, too) to explore include auditory-tactile and visual-tactile synesthesia, where the user can have a tactile generator, such as a fabric with embedded vibrating motors or something like a [braille display](https://en.wikipedia.org/wiki/Refreshable_braille_display) with pins of various materials, activated by sound or visual cues extracted by a CV algorithm. Smell-color synesthesia could have some very practical applications if amplified to give users a heightened sense of olfaction, or chemical (explosives, poison) detection, while still allowing the user to be present for other experiences. There are of course many more types, and given that this is all done in software, we can easily invent yet more.

Lastly, as mentioned above in the Problems section, glitches in the practical implementation of these artificial synesthesia systems can actually be used as something like articifially augmented imagination. Recall the case of the OCR system mistaking light poles for letters 'I' and 'l,' wheels for 'o's, etc. and coloring them all in accordingly. That sounds to me like a very interesting psychedelic world and I'd love to experience it. From there it is not a stretch to imagine purposefully coding an agorithm for a sort of generative reality bending system, drug-free. Leave it to [Adult Swim](http://www.adultswim.com/promos/vr/) to be on the cutting edge.
