---
layout: post
title: Hot-Headed Me
date: 2011-09-22 19:36
author: coherentnoise
comments: true
categories: [arduino, electronics, My Projects, programming]
---
So, I've just gotten myself deeper into various messes on this <a title="Hot-Headed Munny Blog Post at Squishyrobot" href="http://squishyrobot.wordpress.com/2011/09/20/hot-headed-munny/" target="_blank">munny</a> project. I knew, but I didn't know, but sorta knew, but didn't seem to care, that the ATTiny series in the BlinkM only has two PWMs. And worse, only one is connected to the RGB LED. So I'm working on a brute force PWM right now. Here's a bit of pseudo-pseudocode to explain:
<pre>void loop() {
    // Set the output high if the index is before the transition point...
    if (index &lt;= pulseOnTime) digitalWrite(REDPIN, HIGH);
    // ...and set it low if the index is after the transition point.
    else digitalWrite(REDPIN, LOW);
    // Increment the index if it's less than 255, otherwise reset it.
    if (index &lt; 255) index++;
    else index = 0;
}</pre>
Don't fault me if there is a ridiculous logic error there. I just scribbled it down after thinking about it on the drive to work. (Although, if you <em>do</em> see an error, it might be nice to point it out so I don't have to struggle with it later.) Anyway, I'm going to interleave the rest of the code bits I need in there and see if it's still fast enough.

Another problem I expect to have is that I don't really know how fast this all is running. I want to set up a color fade as a test, but I don't really have a good way of knowing if, for example, I can't see the fade because it's too fast or because it's not working. There is no UART on the ATTiny so serial is out of the question.

That is, unless I set up a software serial on one of the spare pins! The problem there (really just an inconvenience) is that I would have to unplug the ATTiny and plug it into a TTL-USB interface. Maybe I could rig up a little bit of code to blink out the number of milliseconds passed after one run through the main loop. That would certainly get me in the ballpark.

I won't have time to test it out tonight. I can't wait, though.
