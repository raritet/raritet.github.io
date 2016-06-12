---
layout: post
title: Radio Control Blowfish
date: 2011-09-01 22:16
author: coherentnoise
comments: true
categories: [arduino, electronics, My Projects, r/c, robot, tamiya]
---
<p>It's about time I start posting about my projects-in-progress in order that I might harness the power of embarrassment as a motivator. That is, once I talk about it publicly, I better do it lest I look like a dilettante jack of all trades, master of none slacker.</p>
<p>Sooo, one project I have in mind is radio-control-izing a <a title="Mechanical Blowfish from Tamiya" href="http://www.tamiya.com/english/products/71114blowfish/index.htm" target="_blank">Mechanical Blowfish, Tail Fin Swimming Action</a> from Tamiya. I love Tamiya kits, and have something like 5 or 6 of their cars (my favorites are from the <a title="M-Chassis Cars at Tamiya" href="http://www.tamiyausa.com/product/category.php?sub-id=36350" target="_blank">M-Chassis</a> line) in various states of disrepair.</p>
<p style="text-align:center;"><a href="http://www.tamiya.com/english/products/71114blowfish/index.htm"><img class="size-full wp-image-283 aligncenter" title="Mechanical Blowfish" src="http://squishyrobot.files.wordpress.com/2011/09/top.jpg" alt="" width="408" height="306" /></a></p>
<p>Anyway, this mechanical blowfish is mega-cute and deserves to be more than just a bathtub toy. My plan is to replace the motor and gearbox with a servo of appropriate torque and install a home-made radio control system.</p>
<p>Why not just cannibalize one of the R/C units from my cars? Good question! I hope to control and drive the blowfish from the flapping tail. So forward speed is modulated, more or less, by the amplitude (and maybe speed) of the wagging tail. And steering, then, is the left or right offset of this wagging. A single servo can do this, but you have to translate two channels of control, speed and direction to the motion of one servo. The easiest way to do this, for me at least, is in software. So the plan is to link two Arduinos (actually an Arduino and an ATTiny25 programmed as though it were an Arduino) wirelessly with <a title="Cheap Wireless Module at Sparkfun" href="http://www.sparkfun.com/products/8945" target="_blank">these</a> cheap modules. And that's pretty much it, sort of. I'll keep you updated.</p>

