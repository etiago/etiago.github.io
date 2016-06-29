---
id: 754
title: Disable power management for the 8188eu driver in Raspbian
date: 2015-04-06T20:46:20+00:00
author: admin
layout: post
guid: http://www.tiagoespinha.net/?p=754
permalink: /2015/04/disable-power-management-for-the-8188eu-driver-in-raspbian/
categories:
  - Software
  - Technology
tags:
  - 8188eu
  - Raspberry Pi
  - Raspbian
  - raspbian wifi turns off
  - Software
  - wifi power management
---
Many WIFI USB dongles out there rely on the 8188eu driver for support under Linux. In fact, in a [previous post](http://www.tiagoespinha.net/2014/04/how-to-get-the-tp-link-tl-wn725n-working-on-raspberry-pi/)  I covered how to compile a 8188eu driver for your own Raspbian kernel which will keep being upgraded if you are vigilant enough to run rpi-update every now and then.

One thing I didn&#8217;t mention in that blog post is that certain devices which use this chipset will enter power management mode after some time.

If this is the case with your device, you can fix it by creating a file called /etc/modprobe.d/8188eu.conf which loads the configuration for the 8188eu kernel module and write the following inside:

options 8188eu rtw\_power\_mgnt=0 rtw_enusbss=0

Then restart your Raspbian and you should be good to go!

&nbsp;