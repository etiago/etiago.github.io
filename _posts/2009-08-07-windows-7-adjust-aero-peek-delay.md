---
id: 257
title: 'Windows 7 &#8211; Adjust Aero Peek Delay'
date: 2009-08-07T17:07:05+00:00
author: Tiago Espinha
guid: http://www.tiagoespinha.net/?p=257
permalink: /2009/08/windows-7-adjust-aero-peek-delay/
categories:
  - Windows
tags:
  - Aero Peek
  - Aero Peek Delay
  - DesktopLivePreviewHoverTime
  - microsoft
  - Software
  - Windows 7
  - Windows 7 Aero Peek
  - Windows 7 RTM
---
<p style="text-align: justify;">
  Having recently tried Mac OS X and all of it Exposé and Spaces goodness, I couldn&#8217;t help but to notice that Aero Peek feels like a complete rip off of the Exposé feature. Don&#8217;t take me wrong though, it is not a critic. I am of the opinion that progress can only be made if we pick the best bits and pieces out of everything that is out there and put it all into one package. So while Windows still has a long way to go on user experience matters, I see this as a move forward.
</p>

<p style="text-align: justify;">
  Still, Aero Peek came with an annoyance for me: it takes too damn long! Basically, when you activate Exposé on a Mac (either by having a shortcut or by hovering over a hot corner) you instantly get to your desktop and can see what&#8217;s underneath &#8211; with Aero Peek this takes at least one or two seconds which isn&#8217;t ideal for me by any stretch.
</p>

<p style="text-align: justify;">
  With that in mind, and since there does not seem to be that much documentation about this yet, Microsoft allows you to adjust that delay time with some registry hacking. To adjust the delay, do the following:
</p>

<ol style="text-align: justify;">
  <li>
    Open regedit (Start -> regedit -> press enter)
  </li>
  <li>
    Go to the key <strong>HKEY_CURRENT_USER \ Software \ Microsoft \ Windows \ CurrentVersion \ Explorer \ Advanced</strong>
  </li>
  <li>
    Once here, create a new DWORD (32 bit) entry with the name <strong>DesktopLivePreviewHoverTime</strong> and set it to whatever time you&#8217;d like in milliseconds. I found that 100 works best for me but I will leave that at your own discretion.
  </li>
</ol>

<p style="text-align: justify;">
  Now I&#8217;m back to testing Windows 7 RTM &#8211; have a good one!
</p>