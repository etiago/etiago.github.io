---
id: 367
title: 'Samsung Galaxy S Gets Android 2.2 (Froyo) [Beta]'
date: 2010-08-29T11:42:15+00:00
author: Tiago Espinha
guid: http://www.tiagoespinha.net/?p=367
permalink: /2010/08/samsung-galaxy-s-gets-android-2-2-froyo-beta/
categories:
  - Mobiles
tags:
  - Android
  - Android 2.2
  - Android Froyo
  - Android OS
  - Android rooting
  - Cellphones
  - Froyo
  - Galaxy S
  - Galaxy S Froyo
  - Lag fix
  - Lag issue
  - Mobile
  - Mobile phones
  - Samsung
  - Samsung Galaxy S
  - Samsung Galaxy S Lag Issue
  - Technology
---
<p style="text-align: justify;">
  <a href="https://www.tiagoespinha.net/wp-content/uploads/2010/08/froyogalaxy.jpg" rel="lightbox[367]" title="froyogalaxy"><img class="alignright size-full wp-image-370" title="froyogalaxy" src="https://www.tiagoespinha.net/wp-content/uploads/2010/08/froyogalaxy.jpg" alt="" width="216" height="217" /></a>In case you were not aware yet, there are Froyo builds available out there <strong>RIGHT NOW</strong> for the Samsung Galaxy S. You just have to be aware that these builds are in fact beta builds released by Samsung and thus might still be a bit buggy and crash-ey. Still, it shouldn&#8217;t break your phone. If anything you&#8217;ll just have to reflash it back with Éclair which is perfectly possible and very safe.
</p>

<p style="text-align: justify;">
  So you want to give these Froyo builds a try? After all there are already <strong>three</strong> betas out there so it can&#8217;t be that bad, right? Well, just read on for a walk through on how to get these builds and how to get them on your phone!<!--more-->For this walk through I&#8217;m going to assume you&#8217;ve never flashed a firmware &#8220;through the back door&#8221; before. Essentially there are two ways of flashing a firmware onto the Samsung Galaxy S. You can either use Samsung Kies which is an application very much like Nokia&#8217;s PC Suite, or you can use Odin. Odin is a hacker&#8217;s tool. It&#8217;s not an official tool by Samsung but instead it&#8217;s a tool that allows you to flash any firmware you want, as long as you have the files for it. To flash these Froyo betas we are, obviously, using Odin.
</p>

<p style="text-align: justify;">
  First and foremost you should obtain all the files that you need, so here&#8217;s a list of what you&#8217;re going to need during the process:
</p>

<ol style="text-align: justify;">
  <li>
    Odin &#8211; the flasher tool
  </li>
  <li>
    Either the 512 or the 513 PIT file (read after step 4 to know which one you need)
  </li>
  <li>
    You get both the above tools by <a href="https://www.wuala.com/Samsung%20Galaxy%20S/Firewares%20,%20Updates%20and%20Odin/Odin%20&%20Bootloader(.PIT)/?key=AfzUZSU4SpKU" target="_blank">clicking here</a>.
  </li>
  <li>
    The firmware that you want to flash.
  </li>
</ol>

<p style="text-align: justify;">
  You can get the latest Froyo build at the time of writing (i9000XXJP3) by going here: <a href="http://rapidshare.com/files/415790394/I9000XXJP3.7z" target="_blank">Rapidshare</a>. Now, as far as the PIT files go, normally you need the 512 file but some firmwares will require the 513. For this XXJP3, you will need the <strong>512 PIT file</strong> which you can get from the link on step 3.
</p>

<p style="text-align: justify;">
  After you have downloaded all the files, make sure you <strong>UNPLUG YOUR PHONE</strong> from your computer.
</p>

Now, here&#8217;s all the steps you need to get to the actual flashing:

  1. Turn off your phone and remove your SIM and SD cards.
  2. Hold the following buttons at the same time: Volume Down, Home and Power button.
  3. After doing the step above, your screen should say &#8220;Download mode&#8221;.
  4. Fire up Odin **BEFORE** you plug your phone to the USB port.
  5. Plug the phone with the USB cord.

<p style="text-align: justify;">
  After step 5, Odin should detect your Galaxy S and it should acknowledge the connection where it says &#8220;ID:COM&#8221;.
</p>

<p style="text-align: justify;">
  When Odin has recognized your phone, you need to load all the files you&#8217;ve downloaded. Keep in mind that the firmware has to be extracted and in it you will find three files: the CSC, the [Modem/Phone] and the [PDA/Code]. Load all the files in their respective slots on Odin and load the 512 PIT file as well. After you&#8217;ve done this, just press &#8220;Start&#8221; and let it rip 🙂 it will take a while and <strong>DO NOT</strong> remove the cable before the process is completed. You will know once the process is completed as Odin will tell you it has finished and your phone will boot back up normally. Keep in mind that the phone will reboot at least once and you should still let it do its thing before it&#8217;s come to a full stop.
</p>

<p style="text-align: justify;">
  After this is done, just enjoy your new Froyo phone 😀
</p>

<p style="text-align: justify;">
  <strong>WORD OF ADVICE:</strong> After you&#8217;ve switched to Android 2.2 Froyo, the method I described in my other post on how to root and apply the lag fix on the phone <strong>no longer will work</strong>. To root and apply the lag fix you will need to use a different method so please, don&#8217;t try to use that on a Froyo Galaxy S.
</p>

<p style="text-align: justify;">
  <strong>ALSO&#8230;!:</strong> I&#8217;m not to be held responsible if you brick your phone in the process of flashing firmwares. I&#8217;m just providing some guidance which if for some reason does not work for you, I am not to be held accountable.
</p>

<p style="text-align: justify;">
  Happy flashing!
</p>