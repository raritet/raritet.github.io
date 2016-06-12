---
layout: post
title: All is not Lost
date: 2011-09-28 12:57
author: coherentnoise
comments: true
categories: [electronics, embedded, My Projects, programming]
---
You must be getting tired of me always talking about this stupid project, especially when it worked just fine on an Arduino. Me too, to the extent that I had sort of given up on using a reprogrammed BlinkM at all. But while driving in my car I thought about this IIR filter application note I read by Dave van Ess at Cypress. Just to fill you in, an infinite impulse response (IIR) or exponential moving average filter looks about like this in C:

<code>newAverage = k*oldAverage + (1-k)*newValue;</code>

where <code>k</code> is a value between 0 and 1 and represents how much the previous values affect the new ones.

Instead of performing floating point calculations, Dave van Ess's article talked about using bit shifts. He used assembly, but his general description was the important part. So I rewrote the above formula along these lines and added bit shifts until things worked about right:

<code>newAverage = (oldAverage &gt;&gt; 1) + (oldAverage &gt;&gt; 2) + newValue - (newValue &gt;&gt; 1) - (newValue &gt;&gt; 2);</code>

It cut my compiled code size by about 30%! (Certainly way more if you're just talking about the filter code itself.) Since each unit shift is essentially a division by two, it looks like I need to extend the series out a little further to maybe four or even five shifts to get smooth transitions. That is, if I want <code>k</code> to be something fairly large (0.9 used to work nicely) I need to add up a bunch of shifts. Overly simplified, a series with four shifts is:

<code>1/2 + 1/4 + 1/8 + 1/16 = 0.5 + 0.25 + 0.125 + 0.0625 = 0.9375 = k</code>

It's still fiddly, so I'm going to convert <code>digitalWrite()</code> and <code>digitalRead()</code> functions to direct port access and see if that gives me the edge I need.
