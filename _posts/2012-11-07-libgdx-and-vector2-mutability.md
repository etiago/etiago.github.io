---
id: 574
title: libgdx and Vector2 mutability
date: 2012-11-07T21:48:27+00:00
author: Tiago Espinha
guid: http://www.tiagoespinha.net/?p=574
permalink: /2012/11/libgdx-and-vector2-mutability/
categories:
  - Game development
  - Quickies
  - Software
tags:
  - game development
  - libgdx
  - quickies
  - Software
---
<p style="text-align: justify;">
  Here&#8217;s a quick post to rant about something that&#8217;s been affecting me for the last couple of days.
</p>

<p style="text-align: justify;">
  Recently I find myself toying around with libgdx to work on a game that I&#8217;ve been meaning to develop for a while. The problem with this library is that apparently, all Vector2 functions affect the actual vector on which they are invoked. This goes against the Java standard of immutability for non-primitive types and is incredibly annoying, especially because these functions will also return the vector for chaining.
</p>

<p style="text-align: justify;">
  Why is this annoying? Well, when you&#8217;re used to the Java standard, you don&#8217;t expect any functions to affect the actual object. Think for example about Java&#8217;s String.split. This will never affect the String itself, especially because the String is immutable. Affecting the String would mean creating a new instance of that string with the change applied to it.
</p>

<p style="text-align: justify;">
  Frankly, I&#8217;m not sure what happens in the backstage but this stinks.
</p>