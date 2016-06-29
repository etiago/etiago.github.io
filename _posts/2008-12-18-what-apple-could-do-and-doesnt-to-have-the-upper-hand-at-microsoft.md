---
id: 148
title: 'What Apple could do (and doesn&#8217;t) to have the upper hand at Microsoft'
date: 2008-12-18T17:04:16+00:00
author: tiago
layout: post
guid: http://www.tiagoespinha.net/?p=148
permalink: /2008/12/what-apple-could-do-and-doesnt-to-have-the-upper-hand-at-microsoft/
categories:
  - Technology
tags:
  - Apple
  - Hardware
  - Technology
  - Windows Vista
---
<p style="text-align: justify;">
  Howdy everyone,
</p>

<p style="text-align: justify;">
  I was thinking the other day (yes, this does happen every now and then) and something hit me: what is the big issue with developing any kind of software these days? Optimization, right? This is truer on a special case and I am refering to the operating systems. Windows, Mac OS, Linux-based&#8230; you know the drill.
</p>

<p style="text-align: justify;">
  Optimization is by nature, a very herculean task, especially when you are developing a piece of software to run on a wide variety of platforms and environments. Sure, some of the most recent computers come with dual-core CPUs, but pretty much all operating systems <strong>must</strong> still be able to operate on single-core processors, just as they have to be able to handle 4 or 8 cores effectively. This is not only true in the case of processors but also on RAM. If an operating system is running on 256Mb of RAM, it must certainly behave differently resource-wise than it will behave on a system with 4Gb of available RAM. More to the point, what is the use of having 4Gb of RAM, if 3Gb stay unused at all times? One could argue that having available memory is good because it allows the applications to use more as they need it, without resorting to swap files, but for the most part it is wasted memory, a precious resource in our computers.
</p>

<p style="text-align: justify;">
  With this said, for companies like Microsoft, it certainly is hard to develop an operating system that will efficiently handle old and new, resource-limited and resource-boasted platforms, simply because they create Windows for a variety of hardware. Windows will run on AMD, Intel and VIA and although they all are x86-based, there are certain instructions, that could be used to optimize but are not, because if my Core 2 Duo has SSE4, my friend&#8217;s Athlon XP 3000+ hasn&#8217;t got this set of instructions and therefore an application optimized for my CPU won&#8217;t actually run on his.
</p>

<p style="text-align: justify;">
  This is, to some extent, the story of Windows Vista. Windows Vista brought quite a few innovations when compared to XP but it had a problem: if your resources are on the lower end, your computer will feel like a sloth on a lazy day and XP feels like cool breeze when compared to Vista. However, if you have ever had the chance to try out Vista on a powerful system, you&#8217;ll be in awe simply because it will feel as fast as XP and you have all the goodies. Windows 7 by the way, is set to change this, but let us keep that to a different post as that is off-subject.
</p>

<p style="text-align: justify;">
  So, what is the main characteristic of a Macintosh computer? Until very recently, they used hardware unlike that of PCs but not anymore, their hardware is now similar and compatible with PC hardware. Actually, its parts are normal PC parts, with Intel CPUs and Intel/Nvidia/ATI graphics cards so what is really different? It&#8217;s simple: they come assembled and are not meant to be disassembled at the risk of getting your warranty voided.
</p>

<p style="text-align: justify;">
  My point is that if Apple keeps such a high-standard on their computers and keeps them so expensive, why not turn the competition knob a notch? Pack their computers with like 8Gb of RAM at least and with 1Tb hard drives. In a way, Apple has started optimizing since Mac OS 10.5 will only run on at least the Core 2 Duo platform and this is a good thing, but I still think that RAM is a major factor in computers that is being systematically (and wrongly) left behind. However, if you have 8Gb of RAM, you could almost reserve 4Gb just for pre-fetching most used applications <strong>before</strong> the user needs them, and still have plenty of RAM for the average user to mess with. Maybe we need to go big and supersize and make a break with the past of computing.
</p>

<p style="text-align: justify;">
  What is the real problem? Not knowing in advance when and how much RAM the user will need. So if an operating system starts using all the available (free) memory to pre-fetch applications, if at some point the user needs an application that requires, say, 512Mb of RAM and that program wasn&#8217;t pre-fetched, the OS will have to quickly ditch 512Mb of that pre-fetch RAM and quickly load that program into memory. The problem? This can&#8217;t happen quickly because the program will be loaded from the hard drive and the hard drive is inherently slow.
</p>

<p style="text-align: justify;">
  Effectively, the memory allocation algorithm has to have something like a behaviour analysis module. Something that records the user behaviour and finds patterns, and even then it has to give room for the unexpected. A good memory allocation algorithm isn&#8217;t the key to all of the problems though, if for instance there isn&#8217;t enough RAM available, then an algorithm can&#8217;t make miracles no matter how good it is.
</p>

<p style="text-align: justify;">
  To finish my post: Apple can control both their software and hardware, as the Portuguese saying goes &#8220;they have the knife and the cheese&#8221; so I sincerely feel that they can do way much more for their users in terms of performance. I do reckon that Mac OS users do not typically complain about performance, but what is also true on a computer is that it can always be faster.
</p>