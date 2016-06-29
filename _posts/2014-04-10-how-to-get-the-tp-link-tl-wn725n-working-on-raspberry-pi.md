---
id: 675
title: How to get the TP-Link TL-WN725N working on Raspberry Pi
date: 2014-04-10T21:22:57+00:00
author: admin
layout: post
guid: http://www.tiagoespinha.net/?p=675
permalink: /2014/04/how-to-get-the-tp-link-tl-wn725n-working-on-raspberry-pi/
categories:
  - Hardware
  - Raspberry Pi
tags:
  - Dongle
  - Hardware
  - Raspberry Pi
  - TL-WN725N
  - TP-Link
  - TP-Link WN725N
  - Wifi
  - Wifi dongle
  - Wifi USB
  - WN725N
---
<p style="text-align: justify;">
  Recently I bought two TP-Link TL-WN725N adapters off Amazon. They&#8217;re cheap and according to the RPi peripherals list [<a href="http://elinux.org/RPi_USB_Wi-Fi_Adapters">here</a>], are supposed to work well under Linux. They do, however, require a special driver which is not included in the Linux kernel itself. This leaves you with two options:
</p>

<p style="text-align: justify;">
  &#8211; Use one of MrEngman&#8217;s pre-compiled kernel modules which is available on the Raspberry Pi forums [<a href="http://www.raspberrypi.org/forums/viewtopic.php?f=28&t=62371">here</a>] (kudos to MrEngman to his ongoing effort!).
</p>

<p style="text-align: justify;">
  or
</p>

<p style="text-align: justify;">
  &#8211; You compile your own kernel module.
</p>

<p style="text-align: justify;">
  However, keep in mind the following <strong>very important caveat</strong>: whatever your choice is, this process requires some basic knowledge of Linux! If you don&#8217;t feel comfortable messing around with kernel modules and such, I would recommend that you proceed with caution and maybe even ask a more experienced friend to give you a hand. It&#8217;s unlikely you will ruin your Raspberry Pi but you may very well ruin your installation. <strong>PROCEED WITH CAUTION.</strong>
</p>

<p style="text-align: justify;">
  Now, be aware that if you just want your wifi up and running and don&#8217;t want to be bothered, you really should take the easy way out here and check whether MrEngman has a pre-compiled module that&#8217;s been compiled with the same revision of your kernel. If you cannot find one or if you&#8217;re feeling especially brave, read on for the step by step on how to compile it yourself.
</p>

<p style="text-align: justify;">
  Also keep in mind that this tutorial applies to the Raspbian distribution. It may (or may not) work in Pidora (and others) but it&#8217;s up to you to adjust accordingly.
</p>

<p style="text-align: justify;">
  <!--more-->
</p>

<h1 style="text-align: justify;">
  Compiling a kernel module
</h1>

<p style="text-align: justify;">
  Be wary, this assumes you&#8217;re going to compile a kernel module to the latest version of the Raspberry Pi firmware (and thus, at the time of writing, for the latest version of the 3.10.y branch). If you&#8217;re not running this version, consider updating [<a href="https://github.com/Hexxeh/rpi-update">updating the RPi to the latest firmware</a>]!
</p>

<h2 style="text-align: justify;">
  Pre-requisites
</h2>

<ul style="text-align: justify;">
  <li>
    Linux kernel source for the Raspberry Pi (do <strong>NOT</strong> use the original Linux kernel as it does not contain all the patches and drivers required for your RPi to work smoothly), available on GitHub [<a href="https://github.com/raspberrypi/linux/tree/rpi-3.10.y">here</a>].
  </li>
  <li>
    Driver for the RTL8188EU, available on GitHub [<a href="https://github.com/lwfinger/rtl8188eu">here</a>].
  </li>
</ul>

<p style="text-align: justify;">
  Many Linux distributions provide a package just with the precompiled kernel headers and that makes it easier than what you&#8217;ll have to do on the Raspberry Pi. Still, it&#8217;s not so difficult. All you have to do is:
</p>

<h3 style="text-align: justify;">
  Cloning and compiling the Linux kernel
</h3>

<p style="text-align: justify;">
  1. Start by cloning the Linux kernel for the RPi
</p>

<pre class="brush: bash; title: ; notranslate" title="">cd /usr/src/
sudo git clone https://github.com/raspberrypi/linux.git rpi-3.10.y
cd /usr/src/rpi-3.10.y/</pre>

<p style="text-align: justify;">
  <span style="line-height: 1.5em;">This will have created a folder called /usr/src/rpi-3.10.y/ where all the Linux kernel source now resides in your Raspberry Pi.</span>
</p>

<p style="text-align: justify;">
  2. For ease of use, create a symbolic link to the /lib/modules/ structure
</p>

<pre class="brush: bash; title: ; notranslate" title="">sudo ln -s /usr/src/rpi-3.10.y /lib/modules/`uname -r`/build</pre>

<p style="text-align: justify;">
  Be sure to write it in as is (or simply copy & paste it in!) as the backticks around uname -r will create the right name for the folder. At this point, your /lib/modules/ path will have a link to the directory where the source code resides. We do this so later when we compile the driver, our life becomes much easier (as the Makefile will automatically look in that directory).
</p>

<p style="text-align: justify;">
  3. Copy your kernel configuration file to the directory where the source is:
</p>

<pre class="brush: bash; title: ; notranslate" title="">sudo sh -c 'zcat /proc/config.gz &gt; .config'</pre>

<p style="text-align: justify;">
  This simply pulls the config from your running kernel into the new kernel you&#8217;re about to compile.
</p>

<p style="text-align: justify;">
  4. Pull the latest Module.symvers into your kernel&#8217;s directory. Note: this is one of the reasons why I would recommend updating first to the latest kernel, otherwise you&#8217;ll have to figure out which Module.symvers you need.
</p>

<pre class="brush: bash; title: ; notranslate" title="">curl -O https://raw.githubusercontent.com/raspberrypi/firmware/master/extra/Module.symvers</pre>

<p style="text-align: justify;">
  5. Compile the kernel to a stage that is ready to be linked against kernel modules. You don&#8217;t want to compile the whole kernel since that&#8217;s 1) not necessary for compiling kernel modules and 2) would take ages on a Raspberry Pi with its limited computing power.
</p>

<pre class="brush: bash; title: ; notranslate" title="">sudo make oldconfig
sudo make modules_prepare</pre>

<p style="text-align: justify;">
  6. Clone the driver off GitHub, compile it and off you go!
</p>

<pre class="brush: bash; title: ; notranslate" title="">cd /usr/src/
git clone https://github.com/lwfinger/rtl8188eu.git
cd /usr/src/rtl8188eu/
sudo make
sudo make install</pre>

<p style="text-align: justify;">
  At this stage, the driver&#8217;s firmware as well as the compiled kernel module have been copied into place but there are a few more considerations to be had.
</p>

<p style="text-align: justify;">
  1 &#8211; Do <strong>NOT</strong> plug the wifi dongle with the Raspberry Pi turned on! Many people (including me) have reported that doing so causes the Raspberry Pi to suddenly restart and this can lead to serious corruption of your SD card. Be on the safe side! Shut down your Raspberry Pi (sudo shutdown -h now), plug in the dongle, and turn it back on.
</p>

<p style="text-align: justify;">
  2 &#8211; At this point, when you run &#8220;ifconfig&#8221; you should already have a wlan0 network which is not connected to anything. In my experience, getting it to connect was the biggest challenge so if you have a WPA/WPA2 network and would like to learn how to connect to it via command line, read on.
</p>

<h1 style="text-align: justify;">
  Connecting to a WPA/WPA2 network via command line
</h1>

<p style="text-align: justify;">
  When you know what you&#8217;re doing, this is an extremely simple process. First off, run the following command:
</p>

<pre class="brush: bash; title: ; notranslate" title="">wpa_passphrase &lt;ssid&gt;</pre>

<p style="text-align: justify;">
  Where you should replace <ssid> with the actual SSID of your network (hint: use &#8220;&#8221; if your network&#8217;s name has spaces in it). It will then prompt you to type in the password for your network. This script generates then a few lines in the format of:
</p>

<pre class="brush: plain; title: ; notranslate" title="">network={
    ssid="Foo"
    #psk="FoobarFoobar"
    psk=f21df897e40a0e7253b8d53e35930e814f312df43ca2b085daa5109f2c2c5e54
}</pre>

<p style="text-align: justify;">
  I recommend that you delete the line started by #psk (as it reveals your password in clear text) and the rest you should copy and paste into a file at /etc/wpa_supplicant.conf. If it exists, overwrite it, if it does not exist, then create it (with e.g. sudo nano /etc/wpa_supplicant.conf).
</p>

<p style="text-align: justify;">
  After you&#8217;ve done that, you need to tell Linux how this network is going to get an IP address and how it&#8217;s managed. You can do so by editing the /etc/network/interfaces file as such:
</p>

<pre class="brush: bash; title: ; notranslate" title="">sudo nano /etc/network/interfaces</pre>

<p style="text-align: justify;">
  Here you should lookout for a line that starts as &#8220;iface wlan0&#8221;. In my case, this line was setting wlan0 as manual which is <strong>NOT</strong> what we want. Ultimately you want something that looks like this:
</p>

<pre class="brush: bash; title: ; notranslate" title="">iface wlan0 inet dhcp
wpa-conf /etc/wpa_supplicant.conf</pre>

<p style="text-align: justify;">
  And <strong>watch out!</strong> If there is a line starting with &#8220;wpa-roam&#8221;, you can safely delete it as it will conflict with your new WPA settings!
</p>

<p style="text-align: justify;">
  After you&#8217;ve modified the file you can then save it and we&#8217;re ready for action. Next thing you need to do is take the WLAN interface down and back up as such:
</p>

<pre class="brush: bash; title: ; notranslate" title="">sudo ifdown wlan0
sudo ifup wlan0</pre>

<p style="text-align: justify;">
  And that&#8217;s it! If everything went well, your Raspberry Pi should now be connected to your network via wifi!
</p>

<p style="text-align: justify;">
  If there&#8217;s something that&#8217;s not clear enough or some steps that I missed, feel free to drop me an e-mail. My e-mail address is my first name [@] my last name [dot] nl. And you can find my first and last name in the url of this blog (hint, my first name is Tiago!).
</p>

<p style="text-align: justify;">
  Finally I would like to thank MrEngman for his dedication and continuous engagement in the Raspberry Pi forums as well as lwfinger for maintaining this driver and making it possible for us to use it on Linux! I would also like to thank Martijn from Grendelman.net for this <a href="http://www.grendelman.net/wp/compiling-kernel-modules-for-raspbian-raspberry-pi/">blog post</a> which helped me in getting all this to work. Thanks! In a future post I will come back and explain how to cross-compile a kernel module for the Raspberry Pi so you can get it done faster by using your (more powerful) desktop computer to do the compilation.
</p>