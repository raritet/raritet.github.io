---
layout: post
title: Papilio, the FPGA Arduino
date: 2011-07-29 17:00
author: coherentnoise
comments: true
categories: [arduino, biology, electronics, fpga, Reposts]
---
<a href="http://squishyrobot.files.wordpress.com/2011/07/papilio_one_small.jpg"><img class="aligncenter size-medium wp-image-225" title="Papilio One" src="http://squishyrobot.files.wordpress.com/2011/07/papilio_one_small.jpg?w=300" alt="An image of the Papilio One board." width="300" height="277" /></a>

This new development board, the <a title="Papilio" href="http://papilio.cc/" target="_blank">Papilio</a>, looks pretty rad. The best way to think of it seems to be as an FPGA Arduino. That is, it's a really easy way to get into FPGA development. What is an <a title="FPGA on Wikipedia" href="http://en.wikipedia.org/wiki/Field-programmable_gate_array" target="_blank">FPGA</a>? It stands for field programmable gate array... so... essentially it's a chip that you can program to be any chip (or combination of chips) that you want. Another way to think of it is as hardware that you can program. So instead of writing a program that is run as software on a microprocessor, you write a "program," often in a language called <a title="VHDL on Wikipedia" href="http://en.wikipedia.org/wiki/Vhdl" target="_blank">VHDL</a>, that is then burned into hardware.

Why? There are FPGAs in many consumer electronics devices, for one. Instead of developing a new chip for some application like a TV and getting all the tooling up and running to fabricate it, Toshiba, Sony, or whoever can simply program an FPGA to do the task. They can then fix mistakes or upgrade the "program" on the FPGA up to the last moment before production (and, I think, even after with firmware upgrades).

But what interests me the most is the capability of an FPGA to perform certain tasks much more quickly than software. I read something about a guy who programmed an FPGA to run some chemistry calculations for him and it got me thinking about some very computationally intensive applications in biology, namely bioinformatics and protein folding. I wonder if FPGAs could help out in these fields. Perhaps, some day, there could even be a device that plugs into a computer to run the calculation to determine the shape of a protein and then send the result back for display on the computer screen... if such a thing doesn't exist already.

Anyway, I want a Papilio and may get around to buying one someday.
