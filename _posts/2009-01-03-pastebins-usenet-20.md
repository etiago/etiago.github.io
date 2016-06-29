---
id: 150
title: 'PasteBins &#8211; Usenet 2.0'
date: 2009-01-03T12:33:24+00:00
author: tiago
layout: post
guid: http://www.tiagoespinha.net/?p=150
permalink: /2009/01/pastebins-usenet-20/
categories:
  - Software
  - Uncategorized
tags:
  - HaxTools
  - PasteBin
  - Usenet 2.0
---
<p style="text-align: justify;">
  Here I am again with a crazy project of mine: HaxTools.
</p>

<p style="text-align: justify;">
  Ok, the name wasn&#8217;t particularly well thought but I think you will find the idea quite well engineered.
</p>

<p style="text-align: justify;">
  On a little background note, let me introduce you to Usenet. Usenet started off in 1979 as a forum-like service. It was a discussion board were allowed to discuss and share opinions, very much like forums as we know them nowadays. Instead of using your webclient, you would have to use an e-mail client with support for NNTP (the newsgroups protocol) or an actual application dedicated to newsgroups, this means that this service, unlike forums, doesn&#8217;t work over HTTP but over a different protocol, NNTP.
</p>

<p style="text-align: justify;">
  What happened after was that people realized the potential of the newsgroup servers for other purposes, namely file distributing based on a centralized server (as opposed to peer-to-peer). Such newsgroup servers are most commonly provided over very powerful Internet backbones which makes them great platforms for distributing all kinds of binary files to several people just at the cost of one single upload.
</p>

<p style="text-align: justify;">
  And so it started happening. Programs were developed that were able to post binary files on newsgroups, and newsgroup clients that were able to download binary files also started showing up. From posting innocent files to using Usenet as a gateway for piracy was quite a small leap and nowadays one could say that the Usenet is perhaps most used for illegal content than for actual discussion of ideas.
</p>

<p style="text-align: justify;">
  Now, back to my application. HaxTools is a proof of concept set of tools; therefore, I won&#8217;t be liable for any damage it causes to your computer or to <strong>whatever</strong> uses people give it. In principle, the program does not violate any terms of service, although it is likely that the service it uses currently (http://rafb.net/paste/) will get up measures to fight it.
</p>

<p style="text-align: justify;">
  My application makes use of PasteBin sites (like the RAFB.net) to store files online. The HaxUploader allows you to choose the granularity of the upload up to 500Kb (meaning that your file will be sliced in 500Kb pieces) and allows files of up to 10Mb &#8211; this limit is in place so that your computer doesn&#8217;t crash. This is just because I had no concern with optimization, so all operations are done in memory, which can be cumbersome on the computer for big files. However, optimizations can indeed be made so that all operations are done out of the hard drive, making the process slower but workable for bigger files. Depending on the success of this proof of concept, I may get into optimizing the idea.
</p>

<p style="text-align: justify;">
  How does it work from a user&#8217;s perspective?<br /> Nothing simpler. The user chooses a file on HaxUploader, presses upload and waits until the green bar gets filled completely and links show up on the box below. When the links are there, you just have to copy the said links (<strong>don&#8217;t ever change the order!</strong>) and distribute them to other people.
</p>

<p style="text-align: justify;">
  From the receiver&#8217;s perspective, they will open HaxDownloader, paste in the links on the <strong>SAME</strong> order as they have received them and press Download. After a while, a message will appear saying that the process was completed; at this point, on the same folder as HaxDownloader was ran, there will be a NewFile.bin &#8211; this is the standard name for all downloaded files. Afterwards you&#8217;ll have to rename it to whatever you like and also keep in mind that you do have to change the extension of the file to what it was originally &#8211; this is also something that could be done better in an actual program.
</p>

<p style="text-align: justify;">
  After that is done, your file is ready to use. Whether it is a RAR file, or an MP3&#8230; whatever, it will work with all file types and we&#8217;ll now get to how it works from the code&#8217;s perspective.
</p>

<p style="text-align: justify;">
  What&#8217;s the whole idea? In a nutshell, the HaxUploader grabs the file it is meant to upload, streams it into memory (treating it as a binary file, thus working for any kind of files) and then moves on to convert the file contents to Base64. This is the standard format on which files are stored on Usenet; so the core idea is kept. With the contents on Base64, it goes on to split them into smaller chunks (given by the granularity setting) and uploads each of the chunks into a separate &#8216;pasting&#8217;.
</p>

<p style="text-align: justify;">
  When it has finally submitted all the parts and acquired all the links from the &#8216;pastings&#8217; we&#8217;re all done and it simply outputs the links to the user.
</p>

<p style="text-align: justify;">
  The order in which the links are arranged does matter and it is imperative that they are kept in the order they are provided to you, otherwise it simply won&#8217;t work as I haven&#8217;t put in place any order measure. (It can be done though and on an actual application this would be needed).
</p>

<p style="text-align: justify;">
  The Downloader program simply fetches the content of the paste links, puts it all back together and decodes the Base64 string into binary, recreating the file.
</p>

<p style="text-align: justify;">
  As a final note, there isn&#8217;t a big deal of protections and validations in place, that is why this is a proof of concept &#8211; I just wanted to prove that it can be done.
</p>

<p style="text-align: justify;">
  For now I am not releasing the source code but just the binaries. If you are interested in the source code, you can contact me at tiago[at]espinhas[dot]net and we can discuss the situation.
</p>

<p style="text-align: justify;">
  Until the next time!
</p>