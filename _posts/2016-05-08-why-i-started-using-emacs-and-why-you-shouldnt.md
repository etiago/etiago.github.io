---
id: 773
title: 'Why I started using emacs (and why you shouldn&#8217;t)'
date: 2016-05-08T16:03:33+00:00
author: Tiago Espinha
guid: https://www.tiagoespinha.net/?p=773
permalink: /2016/05/why-i-started-using-emacs-and-why-you-shouldnt/
categories:
  - Software
tags:
  - editor
  - emacs
  - functional programming
  - Software
---
<p style="text-align: justify;">
  In what feels like a long time ago, I &#8211; as the curious software engineer that I am &#8211; began a journey. I had decided to try vim (<em>&#8220;wha&#8230;? It said emacs in the title&#8230; is this the right art&#8230;&#8221;</em> &#8212; yes it is, just keep on reading). It&#8217;d always baffled me why would people use such a barebones editor over a proper IDE but I figured, if so many people were using it and following it almost as a cult, there <em>must</em> be something to it. So I sat down and forced myself to learn some basics to get me started. And, of course, I started by learning how to <em>quit</em> the editor (relevant side joke: <em>Q: How do you generate a random string? A: Put a Windows user in front of vi, and tell them to exit.</em>), learned about the different modes and I learned basic things like moving forwards and backwards by units of words, and how to delete multiple lines and how to go to a certain line, etc. Basically the kind of thing I would be faced with whilst using vim to actually achieve something programming-wise.
</p>

<p style="text-align: justify;">
  [Continue Reading]
</p>

<p style="text-align: justify;">
  <!--more-->
</p>

<p style="text-align: justify;">
  And it was glorious.
</p>

<p style="text-align: justify;">
  The muscle memory started forming and it became second nature. Vim became part of my tool belt and, when it came to editing files, I started to use it for <em>everything. </em>Delete lines in bulk? Got it. Search and replace the whole document with regular expressions? Piece of cake. Moving around the document by using search rather than painstakingly scrolling my way to it? Hell yeah.
</p>

<p style="text-align: justify;">
  As part of my vim usage, I also created a very small .vimrc which loaded some basic plugins and set the tabbing policies to something sensible (spaces master race!), but that was it, and all was well.
</p>

<p style="text-align: justify;">
  Then one day, I woke up and thought: <em>&#8220;heh, it&#8217;s funny, I&#8217;ve heard about the <a href="https://en.wikipedia.org/wiki/Editor_war">editor war</a> but I never really took the time to see what&#8217;s on the other side of the fence&#8221;</em> and so I decided to climb the fence and have a quick peek. I equipped myself with emacs and, again, forced myself to go through the same bootcamp I had forced myself to years earlier with vim. Not only did I do the same thing, but because my muscle memory was already developed around vim, I started noting down the key combinations for the most common things I was doing in vim, except this time in emacs.
</p>

<p style="text-align: justify;">
  Editor-wise, I didn&#8217;t feel much difference in productivity. It was when I started exploring the different plugins and available customizations that I got really hooked. You see, emacs has its equivalent of the .vimrc file, the init.el. Here is where you can load plugins and set configuration variables to be loaded on emacs&#8217; startup. While in the process of trying to customize emacs to behave the same way <em>my</em> vim was behaving with regards to tabbing and directory explorer (I was using NERDTree) I found out how that in emacs you can simply set up MELPA, emacs&#8217; package repository, and install everything through it. Emacs has its own package repository. Mind blown. Every single mainstream plugin is available at the distance of Alt + X (M-x in emacs notation), writing package-install, and then typing the name of the package. It&#8217;s like your editor has its own version of <em>apt-get</em>.
</p>

<p style="text-align: justify;">
  Since this exotic new editor (which contrary to vim is always in edit mode) was allowing me to discover, install and configure a whole range of plugins through a package repository, I started installing and configuring. That&#8217;s when mind blown #2 came. To load and configure this plugins via the <em>init.el</em> file I was writing elisp code. That&#8217;s right, emacs is built around elisp, its own dialect of a functional programming lisp language. I&#8217;d never done any functional programming before, but damn, I was enjoying it thoroughly. I&#8217;d never done any Vimscript before but I&#8217;d heard horror stories about it, and elisp, by opposition, was being a walk in a very pleasant park with a warm breeze flowing through.
</p>

<p style="text-align: justify;">
  After all was said and done, and after gradually (over the course of days) customizing my init.el to my liking, my emacs was looking no different than a fancy Atom or Sublime Text. Below you&#8217;ll find a comparison of what emacs looks like out of the box (courtesy of GNU) and what <em>my</em> emacs looks like sporting the monokai theme:<img class="wp-image-775 aligncenter" src="https://www.tiagoespinha.net/wp-content/uploads/2016/05/splash.png" alt="splash" width="500" height="453" srcset="https://www.tiagoespinha.net/wp-content/uploads/2016/05/splash.png 722w, https://www.tiagoespinha.net/wp-content/uploads/2016/05/splash-300x272.png 300w, https://www.tiagoespinha.net/wp-content/uploads/2016/05/splash-500x453.png 500w" sizes="(max-width: 500px) 100vw, 500px" />
</p>

<p style="text-align: justify;">
  <img class="wp-image-774 aligncenter" src="https://www.tiagoespinha.net/wp-content/uploads/2016/05/Capture-1024x718.png" alt="Capture" width="500" height="350" srcset="https://www.tiagoespinha.net/wp-content/uploads/2016/05/Capture-1024x718.png 1024w, https://www.tiagoespinha.net/wp-content/uploads/2016/05/Capture-300x210.png 300w, https://www.tiagoespinha.net/wp-content/uploads/2016/05/Capture-768x538.png 768w, https://www.tiagoespinha.net/wp-content/uploads/2016/05/Capture-500x350.png 500w, https://www.tiagoespinha.net/wp-content/uploads/2016/05/Capture-900x631.png 900w" sizes="(max-width: 500px) 100vw, 500px" />
</p>

<p style="text-align: justify;">
  Now, a few weeks later, I look back and I think I would have done it all the same. However, beware, <em>don&#8217;t</em> get into emacs unless you really have the time to spare to have a whole new world opened to you. Are you already a functional programming guru? Then step right ahead, you&#8217;ll feel right at home with emacs. Otherwise, you&#8217;ll find yourself discovering <em>more</em> than an editor. Emacs was once jokingly defined as a &#8220;great operating system, lacking only a decent editor&#8221;. I disagree. It <em>is</em> an operating system, but the editor itself is awesome and kicks vim out of the park any time. By the way, did I mention that vim was <em>implemented </em>within emacs? You will be able to use your tested and tried vim experience with all the goodness of emacs. What&#8217;s more to want?
</p>

<p style="text-align: justify;">
  Have fun with emacs and tell me about your experiences in the comments section below. Until the next time.
</p>

<p style="text-align: justify;">