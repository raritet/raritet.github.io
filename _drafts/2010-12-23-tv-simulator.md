---
layout: post
title: TV Simulator
date: 2010-12-23 14:09
author: coherentnoise
comments: true
categories: [arduino, My Projects]
---
I made a TV Simulator for my <a title="The Arduino project home page." href="http://www.arduino.cc/" target="_blank">Arduino</a> using a 7-Segment shield (for the RGB LED). It's pretty simple. It just changes the brightness of the 3 colors red, green, and blue to a random setting after a random amount of time. The brightness of each component color (hence the overall brightness and mixed color) is controlled by pulsewidth modulation of digital output pins 3, 5, and 6.

I gotta hook this up to my <a title="My single pixel display." href="http://squishyrobot.wordpress.com/2010/12/23/single-pixel-display/" target="_blank">single pixel display</a> Processing sketch some time.

A TV simulator, by the way, makes it look like there is a TV on in a room. It's definitely not my idea, but I don't remember where I saw it.

<a title="My TV simulator Arduino sketch." href="http://squishyrobot.com/arduino/tv_simulator/TV_Simulator.pde" target="_blank">Here</a> is the sketch.
