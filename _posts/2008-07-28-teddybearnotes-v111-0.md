---
id: 11
title: TeddyBearNotes v1.1.1-0
date: 2008-07-28T13:59:00+00:00
author: tiago
layout: post
guid: http://tiagoespinha.info/?p=11
permalink: /2008/07/teddybearnotes-v111-0/
blogger_blog:
  - www.tiagoespinha.net
blogger_author:
  - Tiago Espinhahttp://www.blogger.com/profile/03044662244226940894noreply@blogger.com
blogger_permalink:
  - /2008/07/teddybearnotes-v111-0.html
categories:
  - tbn releases
  - teddybearnotes
---
<div style="text-align: justify;">
  <a href="http://downloads.sourceforge.net/teddybearnotes/TeddyBearNotes-1.1.1-0_setup.zip?use_mirror=osdn">Installer</a><br /><a href="http://downloads.sourceforge.net/teddybearnotes/TeddyBearNotes_src_1.1.1.0.7z?use_mirror=osdn">Source Code</a></p> 
  
  <p>
    That&#8217;s right! Such a young application and there&#8217;s already an update for it. This is actually a somewhat critical update if you have been experiencing issues with vanishing notes. If you had such issues, worry not, your notes are totally safe &#8211; if you had not had any issue at all, you are still advised to upgrade as soon as possible.
  </p>
  
  <p>
    This version has two changes:<br />&#8211; The XML and the XSD files now have a version of its own, this meaning that I can keep releasing versions that do not directly interfere with the structure of the said files, without having to worry about providing means of backup and restore across installs of such versions.
  </p>
  
  <p>
    As a more technical background on this change, the XML and XSD file names now have a version based on the executable version, whereas the actual application version is given by the assembly version. So basically, if you right click your executable and click «Properties», the version you will see there is actually the version of the files it is using as storage.
  </p>
  
  <p>
    &#8211; The second change is a <span style="font-weight: bold;">bug fix</span>. The option of getting the program to startup with Windows had a flaw under Windows XP (this does NOT affect Windows Vista &#8211; read below why). TeddyBear Notes would create a shortcut under Windows&#8217; startup folder but it was setting a wrong «Startup Path», resulting in the following effect:
  </p>
  
  <p>
    -> If you started storing notes when the program was launched on Startup, and then for some reason you closed the program and opened it again manually, you would have an empty note window.
  </p>
  
  <p>
    -> The same would happen if you were to start using the program by launching it manually and then tried to access your notes when it had been started up automatically.
  </p>
  
  <p>
    Q: Why does this not affect Windows Vista?<br />A: Due to slackness of myself (and partly due to convenience), I am storing the data files on the installation directory. Microsoft does <span style="font-weight: bold;">NOT</span> condone this practice on Windows Vista and it has measures in place where it will simply automatically redirect the files elsewhere, as it will also redirect the shortcut startup path.
  </p>
  
  <p>
    [This note does not apply if you are making a clean install of TeddyBear Notes]<br /><span style="color: rgb(255, 0, 0);"><span style="font-weight: bold;">NOTE: </span>If after installing this version you can no longer see your notes, do not panic! Just follow these simple steps:</span><br /><span style="color: rgb(255, 0, 0);">1. Click Start then go over to &#8220;Startup&#8221;</span><br /><span style="color: rgb(255, 0, 0);">2. You should have a file named &#8220;TBN_1_1_0_4.xml&#8221; in there</span><br /><span style="color: rgb(255, 0, 0);">3. Right-click the file and choose &#8220;Cut&#8221;</span><br /><span style="color: rgb(255, 0, 0);">4. Go to the path where you have installed TeddyBear Notes (by default C:\Program Files\TeddyBearNotes)</span><br /><span style="color: rgb(255, 0, 0);">5. Right-click inside that folder and &#8220;Paste&#8221; the file in it.</span>
  </p>
  
  <p>
    <span style="color: rgb(255, 0, 0);">On step 2, if there is no file under &#8220;Startup&#8221;, please contact me through my e-mail: tiago[at]espinhas[dot]net .</span>
  </p>
  
  <p>
    <span style="color: rgb(255, 0, 0);"><span style="color: rgb(0, 0, 0);">A thank you is due to my friend and TeddyBear Notes user (and beta tester), Esther van Ginneken.</span></span></div>