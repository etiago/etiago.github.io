---
id: 549
title: 'The cross-discipline conundrum (or how we can&#8217;t always learn from other disciplines)'
date: 2012-07-10T15:22:03+00:00
author: tiago
layout: post
guid: http://www.tiagoespinha.net/?p=549
permalink: /2012/07/the-cross-discipline-conundrum-or-how-we-cant-always-learn-from-other-disciplines/
categories:
  - Research
  - SOA
  - Software
---
<p style="text-align: justify;">
  I was cycling home one day and this thought popped into my mind: I&#8217;m trying to address the issues of multi-tenancy in software systems. In other words, that is to say that I&#8217;m trying to make it easier for several software systems to co-exist, as tenants, in the same piece of hardware. When we think about it from a software perspective, it is definitely novel &#8211; big names out there like Microsoft, VMWare, Salesforce, etc are working hard on this (each in their own way of course) and it&#8217;s a rather hot topic. Companies provide their employees with Microsoft Azure training and there&#8217;s this growing need to fit more (tenants) in less (hardware). Come to think of it, it&#8217;s a bit like what&#8217;s happening in big cities all over the world.
</p>

<p style="text-align: justify;">
  Wait a minute.
</p>

<p style="text-align: justify;">
  <strong>That&#8217;s exactly what&#8217;s happening in big cities all over the world!</strong>
</p>

<p style="text-align: justify;">
  And why does this matter, you ask. Well, we&#8217;ve been doing this with people and cities for the best part of a century, so maybe some of the problems we face in software have already been dealt with in the &#8220;physical world&#8221;. &#8220;Sure, Tiago, that&#8217;s obvious! Why are you still writing this blog post and not out there reading books on urbanization?&#8221;. Yeah, yeah, yeah&#8230; have you read the title of the post? How we <strong>can&#8217;t</strong> always learn from other disciplines.
</p>

<p style="text-align: justify;">
  Multi-tenancy in software engineering presents its own challenges. How can you compare the concept of software versioning to any concept of the physical world? Same goes for concepts like deploying several instances of the same piece of software in different servers. Surely we can&#8217;t deploy the same person across several buildings (well, quantum physics says we can, but let&#8217;s stick to classical mechanics for the purpose of this post) and we definitely don&#8217;t want to have a tenant with a bathroom on one street, the bedroom two blocks away and finally the living room in a different town. That doesn&#8217;t work for people, it&#8217;s not convenient, but it works for software. Software doesn&#8217;t care if it has to invoke method foo() in its own memory stack or if it has to wrap its request in SOAP and have it traverse all over the world to have it executed.
</p>

<p style="text-align: justify;">
  So what&#8217;s the point of this post, really? While it&#8217;s always good to have a broad cross-disciplinary view and keep an open mind and an eye out for other fields which might be (metaphorically) solving the same problems as yourself, it&#8217;s also very important to identify genuine problems in your field. Sure, resorting to metaphors is perfect to learn from other fields but these don&#8217;t always apply perfectly and when they don&#8217;t apply perfectly, my theory is that they are no good.
</p>

<p style="text-align: justify;">
  In other news, I just submitted my paper to WCRE 2012 🙂 let&#8217;s see how convincing am I with my maintenance techniques for distributed systems&#8230;
</p>