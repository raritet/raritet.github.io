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

Augmented reality (AR) and now mixed reality (MR) are the new cool thing, as those of us in [the tech world have no doubt noticed](http://www.wired.com/2016/04/magic-leap-vr/). No one can disagree that this technology will be useful for all the obvious things like heads-up displays of contextually useful information. But to me that has always seemed _boring_, for lack of a better term. Perhaps it's because it's obvious; _Of course_ you would display relevant facts next to what you are looking at through your MR headset. That's what they've been doing in every cyborg movie for who knows how long. For that matter, Thad Starner started with the predecessor to Google Glass during his time at the MIT Media Lab back in 1993.

To me the real neat stuff is when you come up with an entirely new use case. I think I have thought of one.

Synesthesia is a neurological phenomenon wherein the stimulation of one sense (or more generally one _cognitive pathway_) stimulates another. Imagine a situation where you see the letter 'S' and it has a iridescent, swirly blue tint perceived simultaneously with whatever color the letter was printed in. In other cases, synesthetes (that is the name for people who exhibit synesthesia) may hear a pitch or timbre in music and _feel_ a very real sense of its texture; perhaps prickly, or soft like blades of grass under one's hand.

The locations of the brain corresponding to the perception of the senses involved in a particular case of synesthesia are typically physically adjacent. Researchers therefore theorize that synesthesia may be as simple as brain activity spilling out of one sensory region and into adjacent regions.

There is a seemingly high concentration of synesthetes among the world's most creative people. I've heard synesthesia described as an instinctive form of metaphor. Perhaps what a "normal" person thinks is an incredibly imaginative metaphor, is simply just how the writer sees. Many believe that synesthesia is also common in children, though they do not often have the facilities to communicate it or the mentorship to nurture it. If synesthesia is common in children, it may, at least in part, explain the nature of their highly active imaginations. In any case, examples of synesthesia can also be found in our typical language, such as the timbre of a musical instrument being dark or bright, or even things like _sharp_ cheddar cheese.

While reading about Vladimir Nabokov's particular case of grapheme-color synesthesia—the condition in which one sees letters with color—it seemed to me like it should be pretty straightforward to build an augmented reality app to simulate it for those of us not lucky enough to have been endowed with such a gift: Run the live stream of your cell phone camera through an OCR (optical character recognition) program to find text in the field of view, figure out what letter each one is, outline it, and fill that outline with the color from the lookup table.

It turns out that it's not as straightforward as I thought. I had hoped to more or less replace the fiducial marker used in AR applications with the output of an OCR library, and I suspect that might still be possible. But as far as I can tell, the gold standard open source OCR library, Tesseract, doesn't work like that. Rather, it just outputs the characters corresponding to the text it finds in the image.

Imagine being able to load up some famous synesthete's particular in your MR headset and see the world through their eyes.

Here's a table I compiled of Nabokov's description of his grapheme-color synesthesia from his autobiography:

| Letter | Color | RGB Value | Notes |
| :---: | :--- | :---: | :--- |
| _a_ | weathered wood | * | In English, at least. I take this to mean the _ae_ sound like "at" or "that." Nabokov says this is in the black group. |
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
| _q_ | browner than _k_ | * | This must be blue, still, but "browner." |
| _r_ | sooty rag being ripped | * | This will be interesting to convey simply as a color. |
| _s_ | a curious mixture of azure and mother-of-pearl | * | This is partly to show that shape matters in color in addition to sound. |
| _sh_ | fluffy-gray | * | |
| _t_ | pistachio | * | |
| _u_ | brassy with an olive sheen | * | Also in the yellow group. |
| _v_ | rose quanrtz | * | |
| _w_ | dull green, combined somehow with violet | * | |
| _x_ | steely blue | * | |
| _y_ | bright-golden | * | |
| _z_ | thundercloud bluish | * | |

\* _I am working on selecting RGB values and may ultimately select a different method to store the color. This is particularly important for the colors that Nabokov describes with motion or texture, such as those for 's' and 'a.'_

It looks like I might need to take a little artistic license in implementing some of these colors. Also note that many of these letters rely on the sound, or the phoneme, and not just the shape of the letter (the grapheme). (I believe they should call this phoneme-color synesthesia instead of grapheme-color, but that's neither here nor there.) So to really get this right, the OCR algorithm would also need to look at the word, extract the sounds, and map them back to the letters. But in a proof-of-concept I don't think we really need to do that.
