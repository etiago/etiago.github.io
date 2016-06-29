---
id: 183
title: The First Flaw in Windows 7
date: 2009-05-06T21:14:31+00:00
author: tiago
layout: post
guid: http://www.tiagoespinha.net/?p=183
permalink: /2009/05/the-first-flaw-in-windows-7/
categories:
  - Uncategorized
tags:
  - flaw
  - microsoft
  - Release Candidate
  - Software
  - Technology
  - Windows 7
  - Windows 7 flaw
  - Windows 7 RC
---
Hold your horses, this isn&#8217;t a flaw per se. There isn&#8217;t a massive hole in Windows 7 that allows the execution of malicious code. Instead, there&#8217;s a legacy feature that has been around ever since Windows 98 (maybe even 95, but that I do not know for sure) that is used by virus writers to fool users into executing their viruses.

The feature I am talking about is the ability to hide the extension for known file types. This comes enabled by default on XP and Vista and it was not addressed in Windows 7. Basically, as <a href="http://blogs.zdnet.com/hardware/?p=4317&tag=nl.e550" target="_blank">Adrian over at ZDNet</a> reports, with this feature enabled, a file with &#8216;double extension&#8217; can easily be fooled for its fake extention. For example, a file named Report.txt.exe will automatically have the &#8216;.exe&#8217; extension hidden, and to the eyes of the less computer-savvy it can easily be mistaken for an innocent Report.txt file. Moreso when the creator of the virus is careful enough to add an innocent notepad icon to the malevolent application.

To be perfectly honest, I agree with Adrian. This is a feature that I disable right after I install Windows. More often than not I find myself having to change the extension of a file, and it&#8217;s impossible to do so with this feature enabled and without resorting to the command line.

This feature is dangerous and it has been the gateway for many viruses to spread. Adrian also suggests adding some sort of overlay to the icons of executable files that aren&#8217;t digitally signed &#8211; this is an incredibly good idea. Maybe something glarey as the icons of running applications on the new Windows 7 start bar. If properly done, this could be flashey and would cause a good impression on end-users, both visually and safety-wise. Personally, I would remove the feature altogether and leave it off &#8211; and please, without the possibility of working around it on the registry &#8211; but that&#8217;s just my two pennies worth of opinion.

Have a good one.