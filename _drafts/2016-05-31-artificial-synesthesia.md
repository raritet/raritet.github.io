---
layout: post
title: Artificial Synesthesia
date: {}
published: true
---

Augmented reality (AR) and now mixed reality (MR) are the new cool thing, as I'm sure you've noticed. No one can disagree that this stuff will be useful for all the obvious things like heads-up displays of contextually useful information. But to me that has always seemed boring, for lack of a better term. Perhaps it's because it's obvious; _Of course_ you would display relevant facts next to what you are looking at through your MR headset. That's what they've been doing in every cyborg movie for who knows how long. I should also note that this was a thing in the MIT Media Lab now twenty years ago or so.

To me the real neat stuff is when you come up with an entirely new use case. I think I have thought of one.
 
While reading about Vladimir Nabokov's particular case of grapheme-color synesthesia---the condition in which one sees letters with color---it seemed to me like it should be pretty straightforward to build an augmented reality app to simulate it for those of us not lucky enough to have been endowed with such a gift. Run the live stream of your cell phone camera through an OCR (optical character recognition) program to find text in the field of view, figure out what letter each one is, outline it, and fill that outline with the color from the lookup table.

It turns out that it's not as straightforward as I thought. I had hoped to more or less replace the fiducial marker used in AR applications with the output of an OCR library, and I suspect that might still be possible. But as far as I can tell, the gold standard open source OCR library, Tesseract, doesn't work like that. Rather, it just outputs the characters corresponding to the text it finds in the image.

Imagine being able to load up some famous synesthete's particular in your MR headset and see the world through their eyes.

Here's a table I compiled of Nabokov's description of his grapheme-color synesthesia from his autobiography:

| Letter | Color | RGB Value | Notes |
| :---: | :--- | :---: | :--- |
| _a_ | weathered wood | | In English, at least. I take this to mean the _ae_ sound like "at" or "that." Nabokov says this is in the black group. |
| _a_ | polished ebony | | The French _a_, which I assume is the phonetic _a_. |
| _b_ | burnt sienna | | |
| _c_ | light blue | | |
| _d_ | creamy | | In the yellow group. |
| _e_ | yellow | | |
| _f_ | alder-leaf | | |
| _g_ | vulcanized rubber | | Specifically a hard _g_. |
| _g_ | rich rubbery tone | | This is the soft _g_, and is in the brown group. |
| _h_ | drab shoelace | | Also in the brown group. I guess it's a dirty shoelace. |
| _i_ | yellow | | |
| _j_ | rich rubbery tone | | Similar to the soft _g_, but paler. |
| _k_ | huckleberry | | |
| _l_ | noodle-limp | | |
| _m_ | a fold of pink flannel | | |
| _n_ | oatmeal | | |
| _o_ | ivory-backed hand mirror | | |
| _on_ | the brimming tension-surface of alcohol in a small glass | | The French _on_, which I assume is nasalized. |
| _p_ | unripe apple | | |
| _q_ | browner than _k_ | | This must be blue, still, but "browner." |
| _r_ | sooty rag being ripped | | This will be interesting to convey simply as a color. |
| _s_ | a curious mixture of azure and mother-of-pearl | | This is partly to show that shape matters in color in addition to sound. |
| _sh_ | fluffy-gray | | |
| _t_ | pistachio | | |
| _u_ | brassy with an olive sheen | | Also in the yellow group. |
| _v_ | rose quanrtz | | |
| _w_ | dull green, combined somehow with violet | | |
| _x_ | steely blue | | |
| _y_ | bright-golden | | |
| _z_ | thundercloud bluish | | |

It looks like I might need to take a little artistic license in implementing some of these colors. Also note that many of these letters rely on the sound, or the phoneme, and not just the shape of the letter (the grapheme). So to really get this right, the OCR algorithm would also need to look at the word, extract the sounds, and map them back to the letters to really get the colors right. But in a proof-of-concept I don't think we really need to do that.
