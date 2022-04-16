---
id: 535
title: '[Quickies] Galaxy S2 MIUI 1.12.30 Camera Force Closes'
date: 2012-01-03T22:29:39+00:00
author: Tiago Espinha
guid: http://www.tiagoespinha.net/?p=535
permalink: /2012/01/quickies-galaxy-s2-miui-1-12-30-camera-force-closes/
categories:
  - Android
  - Quickies
tags:
  - Camera FC
  - Camera Force Close
  - FC
  - Force Close
  - Galaxy S2
  - Galaxy SII
  - MIUI Camera
  - MIUI Camera FC
  - MIUI FC
  - MIUI Force Close
---
<p style="text-align: justify;">
  I&#8217;ve tagged this post as a &#8220;quickie&#8221; as I just want to share the solution to a problem I&#8217;ve been having with my recently bought Galaxy S2. This solution was found indirectly and from my extensive search through the Internet, I haven&#8217;t found anyone describing either this problem or the solution to it.
</p>

<p style="text-align: justify;">
  <strong>Problem</strong>: When using the MIUI 1.12.30 ROM on the Samsung Galaxy S2, the camera will freeze and eventually force close while attempting to record video.
</p>

<p style="text-align: justify;">
  <strong>Solution</strong>: The solution to this problem is so simple that &#8220;it hurts&#8221;. If you&#8217;re running MIUI, your kernel will most certainly have the ClockworkMod (CWM) flashed onto it. You will have to go into CWM (i.e. Shutdown phone then power it up with the combo Volume Up + Power + Home), then into the &#8220;advanced&#8221; menu and choose the &#8220;fix permissions&#8221; option.
</p>

<p style="text-align: justify;">
  After you&#8217;ve done this, reboot the phone et voilà! It&#8217;s really that easy!
</p>

<p style="text-align: justify;">
  I&#8217;ve found this <a href="http://forum.cyanogenmod.com/topic/32601-camera-keeps-force-closing/page__p__278856__hl__camera__fromsearch__1">solution</a> through having a similar problem in CyanogenMod. In their forums they explain how to fix it for CM7.1 so I decided to give it a try on MIUI. Turns out the problem is the same.
</p>

<p style="text-align: justify;">
  Hope this saved you some time!
</p>