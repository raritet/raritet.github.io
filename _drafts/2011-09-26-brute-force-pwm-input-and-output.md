---
layout: post
title: Brute Force PWM Input and Output
date: 2011-09-26 18:00
author: coherentnoise
comments: true
categories: [arduino, attiny, blinkm, electronics, My Projects, programming, rgb_led, thingm]
---
OK, so I finished the code for my Munny project. It <em>seems</em> to work, but it's too slow. That is, it doesn't quite respond appropriately and I think it's because things are happening too slowly. And forget about an IIR filter on the accelerometer values.

Take a look at my <a title=" Accelerometer and BlinkM as Arduino at Pastebin" href="http://pastebin.com/HKqKGpBC" target="_blank">Pastebin</a> if you want to see the code.

Well, I shouldn't totally forget about the IIR filter, but I would need to study all the speed tricks in implementing such a thing before it will work (I tried).

So what now? I guess I'll just use a proper Arduino with enough PWMs to do the task to begin with. Unless I'm really stuck on the ATtiny, in which case I can probably keep the BlinkM and talk to it from an ATtiny over I2C or whatever. Sounds like unnecessary work.
