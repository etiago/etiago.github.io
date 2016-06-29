---
id: 128
title: A personal view at Firefox vs. Chrome
date: 2008-10-10T22:32:10+00:00
author: tiago
layout: post
guid: http://www.tiagoespinha.net/?p=128
permalink: /2008/10/a-personal-view-at-firefox-vs-chrome/
categories:
  - Software
tags:
  - Browsers
  - Chrome
  - Firefox
  - Google
  - Mozilla
  - Technology
---
<p style="text-align: justify;">
  So, really, now that the hype is over, what is the browser of choice? Well, the out of the box answer for me is Firefox but let&#8217;s have a deeper look at the contest shall we?
</p>

<p style="text-align: justify;">
  What plays in favour of Google Chrome?<br /> I for one really enjoyed the looks. It has a clean and sleek interface without your regular toolbar menus and without a caption bar. I find this amazing. It&#8217;s the first browser that was designed with true usability in mind regarding the menu paraphernalia. The guys at Google really are being serious about seeing websites as actual applications, and proof of that is the fact that you can create &#8220;application links&#8221;. This also plays in Chrome&#8217;s favour in my opinion. There are pages that I simply have open at all times and ones that I have to be able to access quickly; Google Chrome with this feature allows me to run GMail (or any other website) as a separate window, simply by leaving an icon on my desktop. This separate window is also special, it has kind of usability on steroids since it has no menu whatsoever. It does have a caption, which in this case is good because I might want to move the window around while not maximized.
</p>

<p style="text-align: justify;">
  Ok, now that we&#8217;re done talking about the user interface, we go on to the actual features. For starters, let&#8217;s face it: <a href="http://blogs.zdnet.com/hardware/?p=2507" target="_blank">Google Chrome is <strong>fast</strong></a>. Actually, it feels faster than Firefox as far as browsing is concerned. How do they achieve it? I&#8217;m not exactly sure and if my suspicions are right, you can probably achieve the same effect with <a href="http://fasterfox.mozdev.org/" target="_blank">FasterFox</a> or with a <a href="http://www.ghacks.net/2007/03/29/10-tips-to-speed-up-opera-9/trackback/" target="_blank">properly configured</a> Opera, but I&#8217;m dealing with the facts here and that is that Chrome feels fast.
</p>

<p style="text-align: justify;">
  <!--more-->
</p>

<p style="text-align: justify;">
  There is also a technical choice in Chrome that pleased me greatly, in part I&#8217;m amazed that such a big open-source project like Mozilla Firefox, packed with paranoid security people let something like this go through on Firefox. The choice I&#8217;m talking about is the fact that Chrome spawns different processes for each tab whereas Firefox uses a threading system instead. It is common programming knowledge that when it comes to security, processes are by far much safer than threads, not to mention the advantages regarding memory management. Why, you ask? Memory leaks. This isn&#8217;t just some buzz word that came with Firefox, this is an actual problem that Firefox and many more applications suffer from. What is a memory leak? Again, to put it simply, it&#8217;s memory of your system that was reserved but that wasn&#8217;t marked as free when it was no longer needed. So if a browser eats 100Mb of your RAM, and when you, say, close a tab it does not free the resources that belonged to that tab, then the more tabs you open, the more memory the browser will be using, and it can only use ever so much. How does multiprocessing help prevent this? It&#8217;s simple: since each tab runs in its own process, when the process dies (i.e. the tab is closed), the memory that was assigned to it gets released <em>automagically. </em>So even as far as plugins are concerned (to name a few: Flash, Silverligh, Acrobat Reader&#8230;the list goes on), even if those are leaking memory, which has happened in the past, it will all be contained as soon as the tab is closed.
</p>

<p style="text-align: justify;">
  In practical terms, you open up Firefox and note down how much memory its using. Then browse for 6 hours in a row without closing and reopening the browser. Still, you open tabs, browse in those tabs, close some tabs, open up new ones and do some browsing following this procedure. Also, do visit some Flash-powered websites, and do view some PDF documents in-browser. In the end, close all the tabs but one, it can even be a blank, newly opened, tab. Now open your Task Manager and check how much memory Firefox is using. Note it down and do the same with Google Chrome. See what I&#8217;m talking about? I&#8217;m no future teller but Firefox will be using much memory after the 6 hours than it was in the beginning, and that is memory leaks plus memory fragmentation kicking in (which is also tameable by using processes instead of threads).
</p>

<p style="text-align: justify;">
  Something else that I find great about Chrome is its OmniBar. I had loved Firefox&#8217;s Awesome Bar but OmniBar throws us to a completely different level of browsing. For instance it cuts off the need for two input boxes like Firefox has, since this address bar can do both automatic searching and regular browsing. Way to go Google. As of yet, I&#8217;m still trying to find a Firefox plugin that perfectly mimics OmniBar&#8217;s behaviour.
</p>

<p style="text-align: justify;">
  The incognito mode is also a neat little feature, specially when you are on public computers (or visiting sites that you should not be visiting&#8230;..). This is something that has also been included on <a href="http://www.microsoft.com/windows/internet-explorer/beta/default.aspx" target="_blank">Internet Explorer 8</a> (InPrivate) but apparently is <a href="http://www.zdnetasia.com/news/security/0,39044215,62042653,00.htm" target="_blank">yet to be announced</a> on Firefox, even if I&#8217;m pretty sure that there&#8217;s already some addon out there that serves the same purpose.
</p>

<p style="text-align: justify;">
  Lastly there&#8217;s the download management. Chrome&#8217;s way of handling downloads is far from perfect, but I still like it better than that of Firefox. I really dislike having a separate window in my task pane just for downloads. It&#8217;s a real pain in the rear when you&#8217;re using the feature on Windows that allows you to group windows of the same application. I think there is still some work needed on this.
</p>

<p style="text-align: justify;">
  Now, for the not-so-good things about Chrome.<br /> The spell checker. For God&#8217;s sake, I still cannot believe that you cannot change the spell checker language without having to restart the whole browser! And even more, you have to crawl through the menus to achieve that. Thank you Firefox for allowing me to do that on the context menu.
</p>

<p style="text-align: justify;">
  The lack of extendibility. Unfortunately, Google Chrome still does not support plugins or addons, nor does it support themes. A shame really, specially because it doesn&#8217;t seem like it&#8217;s something that it&#8217;s being worked upon, since their policy seems to be simplicity. This is kind of both good and bad.
</p>

<p style="text-align: justify;">
  It&#8217;s still <strong>very</strong> beta. There&#8217;s features missing (print selected text anyone?), it&#8217;s still kinda buggy and well, it still needs a lot of work. As an advantage is the fact that it&#8217;s an open-source project, meaning that if there are bugs, there&#8217;s a high likeliness that the community will find and report them, and when those bugs are security-critical, this is a massive advantage over closed-source projects.
</p>

<p style="text-align: justify;">
  I also feel that Chrome&#8217;s password management is less intuitive and neat than Firefox&#8217;s. Maybe I&#8217;ve just grown used to the way Firefox handles things. I don&#8217;t really know.
</p>

<p style="text-align: justify;">
  I believe I have in one way or another, covered out everything on both browsers, at least the things that affect me directly. There is a specific addon for Firefox that I cannot go without, that is <a href="http://www.foxmarks.com/" target="_blank">Foxmarks</a>. This addon allows me to share bookmarks across several computers, and I simply cannot get anything like it on Google Chrome, which is sad really. I keep a toolbar with my neatly organized bookmarks and if they aren&#8217;t coherent across all my computers, then it defeats the purpose of having it there.
</p>

<p style="text-align: justify;">
  There&#8217;s another topic on the «browser-war» that I would like to address here: memory usage. No, I&#8217;m not going to show screenshots or make videos of how Firefox uses less or more memory than Chrome, or anything like it. For ages, we&#8217;ve been living on the edge of a good program translating into a program that uses little memory. Nowadays this is a <strong>VERY</strong> wrong concept. In the early days, the RAM memory available was scarce and sometimes we had to make the craziest juggles to even play certain games. Today, we typically have more RAM memory than we can handle; memory which just sits there on our computer, idling. Now, think for a minute: what good is it to have free memory? Yeah, sure it prevents the computer for using the swap file since there&#8217;s always free memory for that one application you&#8217;ve just started but hold on for a second. The RAM is extremely fast when compared to your hard drive, so populating the RAM with data that might be handy in the near future is a measure that will for sure make your computer feel faster. If resources for a certain application are being loaded from the RAM rather than from the hard-drive, you will notice that the application runs faster.
</p>

<p style="text-align: justify;">
  So I think you see where I am getting here? I don&#8217;t really mind if browser X uses more RAM when compared to browser Y, as long as that RAM is being put to good use. That is, as long as that memory is being used to make the application run faster.
</p>

<p style="text-align: justify;">
  Firefox actually has a go at this but the Mozilla guys kind of failed. Firefox does use a ton of memory but it&#8217;s far from being used to enhance speed, it&#8217;s basically memory that gets left over and forgotten about. Since Firefox runs in one single process, this also builds up memory fragmentation within the process, which just adds up to the RAM being wasted mindlessly. The idea of fragmentation is as follows: say that you have 3 tabs. The first is using 20Mb of your RAM, the second is using 5Mb and the third is using 15Mb and also assume that they were opened by this order, thus they are ordered like that in the process&#8217; memory space (it&#8217;s much more complex than this, but for this purpose we can simplify it like that). Then you decide that the second tab (the one with 5Mb) is no longer needed and you close it. Tada, you just have created a hole in your memory. Firefox <strong>won&#8217;t</strong> reorganize the memory assignments just to fill the gap with the existing tabs, set aside the operating system doing that.
</p>

<p style="text-align: justify;">
  Now there are two scenarios:<br /> &#8211; You open a tab that by default uses up 10Mb and therefore it won&#8217;t fit the gap. (You are wasting the 5Mb that despite being free, they can&#8217;t be used by whatever else that requires more space)<br /> &#8211; You open a tab that starts up at 2Mb, and as you browse on it, it grows to 15Mb. Then you&#8217;ll have fragmentation. Part of your tab&#8217;s data will be on that gap, and the rest will be somewhere else.
</p>

<p style="text-align: justify;">
  Either scenario is undesirable and also avoidable with processes instead of tabs.
</p>

<p style="text-align: justify;">
  But hey, I&#8217;m going to stop hitting the same key, it&#8217;s just that apparently Mozilla has pushed this notion way down on their priority stack and this is just foolish. I&#8217;m sure it will take a lot of work to switch from threads to processes, but it will be really worth it in the end.
</p>

<p style="text-align: justify;">
  The last remark on the two browsers<br /> There&#8217;s a new fight going on right now which is the Javascript fight. Google and Mozilla seem to be going head-to-head trying to make their Javascript engine be the fastest one. Truth is that when you compare Google Chrome (any version) to Mozilla Firefox (up until 3.1.0 which is still due to be released), Chrome simply is <a href="http://news.cnet.com/8301-1001_3-10030888-92.html" target="_blank">much faster</a> as it is shown by many reviews out there. However, Mozilla is working on a completely new Javascript engine, TraceMonkey, which <a href="http://andreasgal.com/2008/09/03/tracemonkey-vs-v8/" target="_blank">at first sight</a> will put a hell of a fight with Chrome&#8217;s V8. Who benefits from this? Us, users, of course. The more they fight, the better served we are 😉 .
</p>

<p style="text-align: justify;">
  To finish off my post, I just would like to clarify the reason I stick with Firefox. The point is that Firefox has been out there for quite a while now, and despite its security flaws here and there that have happened throghout time, it is pretty rock solid and secure. Google Chrome still has a lot to prove, it&#8217;s still embrionary and it has a lot of growing up to do. Firefox also allows me to use addons that allow me to extend its features and I value this deeply, specially the possibility of using Foxmarks and of changing dictionaries quickly. These are practical things that I cannot go without, hence choosing Firefox for my day-to-day tasks. However, if what you do isn&#8217;t exactly mission critical and if there aren&#8217;t any extensions for Firefox that you use, then by all means, stick with Google Chrome. Only with a good userbase a piece of software can be improved.
</p>