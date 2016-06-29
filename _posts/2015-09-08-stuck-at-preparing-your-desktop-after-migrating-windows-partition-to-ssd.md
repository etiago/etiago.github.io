---
id: 763
title: 'Stuck at &#8220;Preparing your Desktop&#8221; After Migrating Windows Partition to SSD?'
date: 2015-09-08T20:52:59+00:00
author: tiago
layout: post
guid: http://www.tiagoespinha.net/?p=763
permalink: /2015/09/stuck-at-preparing-your-desktop-after-migrating-windows-partition-to-ssd/
categories:
  - Software
  - Windows
tags:
  - HDD
  - Migrate Windows Partition
  - Software
  - SSD
  - Ubuntu
  - Windows
---
<p style="text-align: justify;">
  Recently at work I helped a colleague migrating his laptop from a HDD to an SSD. He was dual-booting his machine with Windows 7 and Ubuntu, and after skillfully shrinking his original partitions (in order to fit the SSD), we copied the partitions over with dd from the HDD to the SSD. After that was done, Grub was understandably confused as its entries were pointing to the HDD partitions rather than the SSD partitions but even after an update-grub and grub-install from within Ubuntu, Windows still wouldn&#8217;t boot.
</p>

<p style="text-align: justify;">
  We consistently got stuck at &#8220;Preparing your Desktop&#8221; screen and eventually Windows would boot into a completely empty desktop.
</p>

<p style="text-align: justify;">
  Keep reading to figure out how to fix this.
</p>

<p style="text-align: justify;">
  <!--more-->
</p>

<p style="text-align: justify;">
  Even though my Windows skills have rusted from having fully migrated to Arch Linux a while back, I still remembered you could run programs from the task manager which, conveniently, is still possible to launch using the Ctrl+Alt+Del combination. Having done so allowed me to diagnose the problem: when I ran cmd.exe, Windows was mounting the SSD partition from which I was trying to boot as F:\ rather than C:\ where Windows expected everything to be.
</p>

<p style="text-align: justify;">
  The fix, after you know what to do, is simple-ish.
</p>

<p style="text-align: justify;">
  Essentially you need to change your registry (you know, regedit) and remove all the letter mappings so that Windows will remap all your drives again at boot.
</p>

<p style="text-align: justify;">
  Easy right? Just launch regedit and edit away! But NO! Because you will, with 100% certainty, not be able to launch regedit!
</p>

<p style="text-align: justify;">
  So what&#8217;s the solution then, how can you edit your registry without actually being able to boot into Windows?
</p>

<p style="text-align: justify;">
  Nice question! We do it from Ubuntu using a nifty tool called chntpw which was originally developed (I assume&#8230; based on the name&#8230;) to change the password of NT-based systems.
</p>

<p style="text-align: justify;">
  So! Jump on Ubuntu, get yourself chntpw installed (seriously, if you don&#8217;t know how to do this, get a friend to help you as the next steps are VERY sensitive!) and do the following steps:
</p>

<ol style="text-align: justify;">
  <li>
    Mount your Windows partition (from now on called <WindowsPartition>).
  </li>
  <li>
    Run chntpw -i <WindowsPartition>/Windows/System32/config/system (N.B. Windows is not case-sensitive but Linux is! Therefore, your file might be called SYSTEM).
  </li>
  <li>
    From the menu, choose option 9 (Registry Editor).
  </li>
  <li>
    Now if you type &#8220;ls&#8221;, one of the items should be &#8220;MountedDevices&#8221;.
  </li>
  <li>
    Enter it by typing &#8220;cd MountedDevices&#8221;.
  </li>
  <li>
    Again if you &#8220;ls&#8221;, a number of entries should appear, including all your drive letter mappings (we&#8217;re almost there!).
  </li>
  <li>
    Now, I had no success actually <em>changing</em> the mappings so I ended up simply removing all the mappings and letting Windows remapping on the next boot. To do so type &#8221; dv \DosDevices\C:&#8221; and repeat this command for all the mapped letters in your computer.
  </li>
  <li>
    Do &#8220;ls&#8221; one more time to confirm the mappings have been deleted.
  </li>
  <li>
    Choose option &#8220;q&#8221; to quit chntpw followed by &#8220;y&#8221; to confirm writing the registry hive file.
  </li>
  <li>
    TADA! You&#8217;re done! Boot into Windows and it should finally boot correctly.
  </li>
</ol>

<p style="text-align: justify;">
  Let me know in the comments if you&#8217;re stuck in some step and I&#8217;ll gladly give a hand!
</p>

<p style="text-align: justify;">
  Till the next time!
</p>

<p style="text-align: justify;">
  [<a href="http://members.iinet.net/~herman546/Hacking%20the%20Windows%20Registry%20with%20chntpw.html" target="_blank">Credit</a>]
</p>