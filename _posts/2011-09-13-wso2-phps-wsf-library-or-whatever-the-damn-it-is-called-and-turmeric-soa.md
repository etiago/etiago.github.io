---
id: 519
title: 'WSO2 PHP&#8217;s WSF Library (or whatever the damn it is called&#8230;) and Turmeric SOA'
date: 2011-09-13T09:48:27+00:00
author: tiago
layout: post
guid: http://www.tiagoespinha.net/?p=519
permalink: /2011/09/wso2-phps-wsf-library-or-whatever-the-damn-it-is-called-and-turmeric-soa/
categories:
  - SOA
  - Uncategorized
tags:
  - PHP
  - PHP SOAP
  - PHP WSF
  - SOAP
  - WSF
  - WSF-PHP
  - wsfphp
  - WSO2
  - WSO2 PHP
  - WSO2 WSF
---
<p style="text-align: justify;">
  <a href="https://www.tiagoespinha.net/wp-content/uploads/2011/09/762791717WSO2pic.jpg" rel="lightbox[519]" title="762791717WSO2pic"><img class="alignleft size-full wp-image-523" title="762791717WSO2pic" src="https://www.tiagoespinha.net/wp-content/uploads/2011/09/762791717WSO2pic.jpg" alt="" width="250" height="102" /></a>The title of this post is verbose enough about the feelings I have regarding the naming of this library. It&#8217;s as if WSO2 took a page from Microsoft&#8217;s book regarding names. What&#8217;s next? A Home Edition? Maybe throw in Professional, Business and Ultimate versions too for good measure.
</p>

<p style="text-align: justify;">
  Don&#8217;t take me wrong, I have no special feelings towards names themselves, it&#8217;s just how difficult it makes to search for people working on the same things and facing the same problems. What do I Google for? WSO2? WSF? PHP? Any combination of these? It&#8217;s only made worse by these guys developing frameworks in several platforms, which means I end up finding completely unrelated results from a different implementation, in a different technology.
</p>

<p style="text-align: justify;">
  But, naming rants aside, I thought it would be a good idea to share my experience with getting this library up and running on PHP. I came across this library when converting Apache Stonehenge&#8217;s web application to use Turmeric&#8217;s instances of Stonehenge&#8217;s web services, and it gave me quite some headaches. For this reason, and so that other people in the future don&#8217;t have to go through the same painful experiences, I decided to write this blog post. Keep reading if I got your attention&#8230;<!--more-->
</p>

<p style="text-align: justify;">
  First and foremost, I should warn that I&#8217;m also gonna write the Linux walkthrough and it does expect you to have some basic Linux knowledge. Nothing too advanced, you just need to know your way around a Linux system in a command line. If you meet this criterion, this walkthrough should be a walk in the park (no pun intended there).
</p>

<h3 style="text-align: justify;">
  Setting up the library
</h3>

<p style="text-align: justify;">
  To begin with, you must download the WSF PHP library <strong>sources</strong>. You should be able to find it <a href="http://wso2.com/products/web-services-framework/php/">here</a> somewhere. At the time of writing, the latest version is 2.1.0. Make sure you download the <strong>sources</strong>. Sadly, the binaries only include DLL&#8217;s for the Windows installation, which means that us, Linux users, must compile our own binaries by hand. No biggie though, it&#8217;s easier than it sounds.
</p>

<p style="text-align: justify;">
  After you&#8217;ve downloaded the library, the next thing you should do is &#8220;cd&#8221; into the directory. Then, normally you&#8217;d just do ./configure followed by a make and make install, but there&#8217;s a caveat: it&#8217;s VERY recommended that you specify a prefix when you do ./configure. The prefix will tell WSO2 where to place the binaries after you compile and &#8220;install&#8221;, and this is extremely useful for WSF as you&#8217;ll need a clean directory featuring only the binary files of this library. You&#8217;ll understand why in a minute.
</p>

<p style="text-align: justify;">
  In sum, you should do:
</p>

> <pre>./configure --prefix=/usr/local/bin/apache2/php/wsf-php/
 make
 [sudo] make install</pre>

<p style="text-align: justify;">
  In my example you&#8217;ll see that I&#8217;m telling &#8220;make&#8221; to install the library in /usr/local/bin/apache2/php/wsf-php/ and in the last step I&#8217;ve also accounted for those of you who, like me, use Ubuntu. If you use Ubuntu, make sure you add the sudo before the make install command (without brackets).
</p>

<p style="text-align: justify;">
  <strong>Troubleshooting: </strong>If you installed PHP through Ubuntu&#8217;s packages, it is possible that everything went fine at this point. If it did (i.e. if you got no errors in neither of the stages) then excellent. Move on. Skip this section. If, on the other hand, you got an error about a missing php-config, then you need to specify the path to this binary in the ./configure step. First you should know where your PHP installation lies (and you&#8217;re entirely on your own for this one) and once you know where it is, your php-config binary is inside <path_to_php>/bin/. Once you figured out where that is, you should go back to those three steps above, except your ./configure should look like:
</p>

> <pre>./configure --prefix=/usr/local/bin/apache2/php/wsf-php/ --with-php-config=&lt;path_to_php&gt;/bin/php-config</pre>

<p style="text-align: justify;">
  After this, don&#8217;t forget of course, to do the make and make install steps.
</p>

<p style="text-align: justify;">
  With that done, you should now have the compiled library in /usr/local/bin/apache2/php/wsf/ (or in whichever folder you specified as prefix). You also want to have a look at the final lines of the &#8220;make install&#8221; step and look for a reference to a wsf.so file. That&#8217;s THE library that PHP will load and you&#8217;ll need to know exactly where it is. In my case, the library sits in /usr/local/bin/apache2/php/lib/php/extensions/no-debug-non-zts-20090626/wsf.so . My guess is that the make install step is smart enough to put it in the equivalent folder inside your PHP&#8217;s installation. Anyhow, copy this directory.
</p>

<p style="text-align: justify;">
  The next step involves editing your php.ini file. Again, you should know where this is. After you found it, add the following lines to it:
</p>

> <pre>extension=/usr/local/bin/apache2/php/lib/php/extensions/no-debug-non-zts-20090626/wsf.so
wsf.home="/usr/local/bin/apache2/php/wsf-php/"</pre>

<p style="text-align: justify;">
  From that you can see that I put the path to the .so file as an extension that PHP must load, and I specified an entry called &#8220;wsf.home&#8221; that will tell WSF where its &#8220;auxiliary&#8221; files are. This is the path you used as the prefix during the compiling process. These are the two most essential parameters that need to be configured to get WSF up and running, there&#8217;s more but I&#8217;m aiming at the quickest way possible to get it running, with as little configuration as possible.
</p>

<p style="text-align: justify;">
  After you&#8217;ve added those lines, you should restart your Apache et voilà! Your PHP installation should now have loaded the WSF library. If you want to be sure that everything is up and running, you can check the contents of /tmp/wsf_php_server.log . If everything went well, this log should have no errors.
</p>

<h3 style="text-align: justify;">
  Creating a client and using it
</h3>

<p style="text-align: justify;">
  Now comes another <strong>tricky part</strong>. Great, now your library is up and running, but how do you <strong>use it</strong>?
</p>

<p style="text-align: justify;">
  I&#8217;m gonna provide another quick and simple explanation of how to get a client up and running for an existing service. This assumes, of course, that you already have a service running somewhere which provides you with a WSDL file and SOAP ports that you can invoke.
</p>

<p style="text-align: justify;">
  Provided you have that, you need to copy a folder in the WSF sources to somewhere safe and accessible by PHP (by accessible, I mean, PHP/Apache should have at least read and execute permissions). The folder you need is <WSF_sources>/scripts/. Copy it somewhere you know it won&#8217;t get deleted by an overzealous system administrator and keep it accessible. I would keep it out of public access via Apache but that&#8217;s entirely up to you. It&#8217;s the next step that is <strong>important</strong>.
</p>

<p style="text-align: justify;">
  Now that you copied this folder (and all its contents) to somewhere safe, you need to go back to your php.ini and add the folder to its include_path definition. In my case, I just uncommented the already existing line and added my scripts folder to it. In the end it looked like:
</p>

> <pre>include_path = ".:/php/includes:/usr/local/bin/apache2/php/scripts/"</pre>

<p style="text-align: justify;">
  After you&#8217;ve added/uncommented this line, be sure to restart Apache once more. This line will just tell PHP where it can find scripts that WSF will need whenever you&#8217;re using its libraries.
</p>

<p style="text-align: justify;">
  With that out of the way, the next step consists of creating a PHP classmap of all the operations and types you have in your WSDL file. My advice is that you obtain the WSDL file in advance and store it somewhere in your hard-drive. After you&#8217;ve done this, just go to the scripts folder and do:
</p>

> <pre>php wsdl2php.php &lt;path_to_your_wsdl_file&gt;</pre>

<p style="text-align: justify;">
  It can happen at this step that Linux will tell you it can&#8217;t find PHP. If that&#8217;s the case, instead of starting off with just &#8220;php&#8221;, use the full path instead.
</p>

<p style="text-align: justify;">
  By doing this step, you&#8217;ll see a bunch of PHP code scrolling through your console. If that was the case, repeat the command and redirect the output to a file, e.g. > somefile.php.
</p>

<p style="text-align: justify;">
  This somefile.php is now your client. It includes a PHP class for every type in your WSDL and an action for every SOAP port. It also includes, at the very end, a sample of how you&#8217;d invoke every action. By looking at that you can probably get a good idea of how WSF works, and that&#8217;s pretty much it. I assume that if you&#8217;re messing around with PHP, you do have enough knowledge to get rid of these sample invokations and just use this file as something you import and use in your PHP application. That&#8217;s not going to be covered in this tutorial.
</p>

<p style="text-align: justify;">
  If you do have questions or ran into trouble while following these steps, please do leave me a comment and I&#8217;ll try to answer as soon as possible. I hope this has somehow helped you, reader. I know I wish I had found something like this post when I first started messing around with WSF!
</p>

<p style="text-align: justify;">
  Till the next post!
</p>