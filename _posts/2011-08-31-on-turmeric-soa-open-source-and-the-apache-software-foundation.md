---
id: 490
title: On Turmeric SOA, open-source and the Apache Software Foundation
date: 2011-08-31T22:32:37+00:00
author: Tiago Espinha
guid: http://www.tiagoespinha.net/?p=490
permalink: /2011/08/on-turmeric-soa-open-source-and-the-apache-software-foundation/
categories:
  - SOA
tags:
  - Apache
  - Apache DB
  - Apache Derby
  - Apache PMC
  - Apache Software Foundation
  - ASF
  - PMC
  - Program Management Committee
  - Service Oriented Architectures
  - SOA
  - Turmeric
  - Turmeric SOA
---
<p style="text-align: justify;">
  <a href="https://www.tiagoespinha.net/wp-content/uploads/2011/08/Service-Oriented-Architecture-SOA-For-Dummies.jpg" rel="lightbox[490]" title="Service Oriented Architecture SOA For Dummies"><img class="alignleft size-full wp-image-496" title="Service Oriented Architecture SOA For Dummies" src="https://www.tiagoespinha.net/wp-content/uploads/2011/08/Service-Oriented-Architecture-SOA-For-Dummies.jpg" alt="" width="194" height="240" /></a>It&#8217;s been a while since I posted something on this blog, partly due to my laziness, but also due to a chronic lack of time and patience to come home after an intellectually intense day of work and still have the peace of mind to gather my thoughts and put them in words. Today was, luckily, one of those days. Not because it was a particularly easy day at work (reengineering someone else&#8217;s code with little to non-existing documentation is <strong>never</strong> an easy job) but perhaps the intense gym session loosed my brains just enough for organized and coherent thought to just happen. In any case, I digress.
</p>

<p style="text-align: justify;">
  This post has three main themes. I will be talking about a platform for SOA applications called Turmeric (funny name, I know. I&#8217;m using for SOA the same I use in my lentil soup), open-source in general and finally, the Apache Software Foundation and some recent events I&#8217;ve been involved in.
</p>

<p style="text-align: justify;">
  <!--more-->
</p>

<p style="text-align: justify;">
  I shall begin with <a href="https://www.ebayopensource.org/index.php/Turmeric/HomePage">Turmeric SOA</a>. Turmeric SOA, despite the strange choice of name, is actually an industry grade platform for web services. Why is it industry grade, you ask? Is it because the developers so claim? Not really. The industry grade designation is actually made by me &#8211; the project (and its developers) do not claim anything about it being industry ready or anything of that kind. I should mention, however, that Turmeric SOA is the <strong>open-source</strong> version of the platform that powers eBay. Yes, you read that right, THE eBay. In my book, if a platform handles the millions of customers all over the world that eBay does, that platform is pretty much as industry-grade as it gets these days.
</p>

<p style="text-align: justify;">
  Why am I talking about Turmeric SOA? Why am I even involved in Turmeric SOA?
</p>

<p style="text-align: justify;">
  It&#8217;s very simple really and it all points back to my work as a Ph.D. student at the <a href="http://www.st.ewi.tudelft.nl/~tiago/">Delft University of Technology</a>. My research, in broad terms consists of analyzing and coming up with new ways of helping the maintenance, reengineering and testing of Service Oriented Architectures. In this description, I&#8217;ve cleverly omitted the keyword that defines my research, mostly because it&#8217;s a vague buzzword that means different things to different people (in case you&#8217;re wondering, the word is <em>multi-tenancy</em>). In any case, my research involving SOA only makes sense if I have a software system on which I can investigate and demonstrate my claims and this is where it all gets hairy.
</p>

<p style="text-align: justify;">
  The fact is that for most companies, SOA simply means exposing some of their data through an API built on top of SOAP or REST, et voilà. All of a sudden they can claim that they are a company of the future because they have a SOA system. This, however, couldn&#8217;t be farther from what an actual SOA system should be. We can even take the etymological angle and look at what SOA means: Service Oriented <strong>Architecture</strong>. I&#8217;ve emphasized the word &#8220;architecture&#8221; as I believe that is the keyword in the SOA acronym. Your SOA system should be built using an architectural style consistent with that of services that communicate with each other. It should be oriented towards/based on services, and not a monolithic blob with one tiny service gateway that allows me to query some data, even if that data is provided in a platform-agnostic manner. To people who have such monolithic SOA-wannabe systems, I ask: can I slice part of your software and place it elsewhere in the world with an Internet connection on both ends? If I can&#8217;t, what if your user-base or your business grow to a point where one server no longer cuts it? What do you do then? Keep buying bigger motherboards with more CPU and RAM sockets?
</p>

<p style="text-align: justify;">
  Let&#8217;s get real here. Your software system is service-oriented if I can grab all the pieces that compose it and spread it all over the world. The only thing I should have to tell the software system is: &#8220;you have service A deployed at this endpoint, service B at this other endpoint, etc etc&#8221; and then it would automagically just work, regardless of whether the services are running in the same application server or in each other&#8217;s antipodes in completely opposite timezones.
</p>

<p style="text-align: justify;">
  So why am I bringing this up? Well, as it stands it&#8217;s difficult enough to find open-source systems that are truly built around a service-oriented architecture. For most of these services, SOA is an afterthought. It&#8217;s something those open-source ERP developers woke up one day and thought &#8220;hey, wouldn&#8217;t it be cool if our ERP had some SOA features?&#8221; &#8211; and alas, the result is invariably slamming some poorly engineered JAXWS or Axis2 solution on top of already existing business logic and inevitably making a mess of a perfectly fine (albeit, poorly scaling) software system.
</p>

<p style="text-align: justify;">
  From my own experience, this is the summary of most open-source ERP systems out there that claim to have some kind of SOA functionality.
</p>

<p style="text-align: justify;">
  This doesn&#8217;t cut it for us. This is not what the SOA paradigm truly stands for and these systems are ultimately useless for my research. There&#8217;s only one web service! How the hell is it supposed to communicate with anything? Its business logic is ultimately still relying on local method calls.
</p>

<p style="text-align: justify;">
  Then out of this hell comes another frightening fact. Even the web service platforms out there are useless on their own. I was chatting with a friend of mine &#8211; who&#8217;s not a computer scientist &#8211; the other day, and I was struggling to explain to her what exactly my problem was without using terms such as JAXWS, Turmeric, web services or SOA. I think I came up with a clear laymen explanation involving the process of building a car. So, my problem right now is that I need a very specific type of car, say, one that is rocket propelled. There are, of course, brands out there that have rocket propelled cars but there&#8217;s no way on Earth that these guys are gonna let me even LOOK at their car, set aside open the hood and disassemble its engine. Yet, my research consists of analyzing the problems and challenges of maintaining a rocket propelled car. But I have no car, and no means to get one. This is a pretty big inconvenience. Not even me promising this car brand that I won&#8217;t build a competitor car, or destroy their car will convince them to let me pop the hood &#8211; and so, Houston, we have a problem.
</p>

<p style="text-align: justify;">
  The solution to this problem is seemingly simple. I can just build my own rocket propelled car and hope for the best. But then we run into a more essential problem: I&#8217;m not a car maker, nor does my department pay me to make cars. Also, if by the end of my Ph.D. I&#8217;ve only built a rocket propelled car, they&#8217;re not gonna be happy.
</p>

<p style="text-align: justify;">
  I could also cut some corners and build a mockup of a rocket propelled car. Sure, maybe it doesn&#8217;t have a gearbox and the steering wheel is made of cardboard, but hey! It&#8217;s a rocket propelled car! This would be swell, if it wasn&#8217;t for the fact that even the free tools I can get out there to make cars are pretty&#8230; well&#8230; horrible. Stepping back out of the metaphor world, the problem is that the technologies available allow me to build simple web services. I can just grab Java&#8217;s Metro project (aka JAXWS) and very easily deploy a web service, but that&#8217;s just what it is. A web service, accessible via SOAP, amidst nothingness. There&#8217;s nothing I can query to know that this service is there, there&#8217;s no platform managing this service and telling me that it has <em>this many</em> services and that <em>this particular one</em> is one of them, there&#8217;s no statistics or runtime information being kept on this service, there&#8217;s basically&#8230; nothing. Just a Java class with a &#8220;WebService&#8221; sticker on it.
</p>

<p style="text-align: justify;">
  These tools make it difficult to build something that even resembles a real world SOA system (i.e. a rocket propelled car). They&#8217;re the tiniest building blocks that you can think of. The sand in the car&#8217;s windshield or the iron ore in the chassis&#8217; stainless steel. Sure, I can melt the sand, add some caustic soda and fashion my own windshield out of it. I can melt the iron ore and through some process I don&#8217;t even know, make steel. But how long is this going to take me? And will the final result be a faithful representation of what actual companies in this line of work have made? Or just a silly toy example that doesn&#8217;t fully represent the pains and benefits of such a system?
</p>

<p style="text-align: justify;">
  <a href="https://www.tiagoespinha.net/wp-content/uploads/2011/08/TurmericLogo.jpg" rel="lightbox[490]" title="TurmericLogo"><img class="alignright size-full wp-image-498" title="TurmericLogo" src="https://www.tiagoespinha.net/wp-content/uploads/2011/08/TurmericLogo.jpg" alt="" width="214" height="117" /></a>That&#8217;s where Turmeric comes in. My first impression when I started using Turmeric was that of confusion. I thought to myself &#8220;well, that&#8217;s another platform with an awful lot of features that no one&#8217;s ever going to use&#8221;, but I was wrong. Over time, with more thoroughly exploring this platform, it became clear that perhaps every single feature in Turmeric really stemmed from a real world use case, most likely from eBay. All those features, if you really think about it, you&#8217;ll end up realizing &#8220;oh yeah, they probably use this to achieve X and Y&#8221;. In other words, even if we don&#8217;t have the rocket propelled car, we have the exact tools that we need to build one. Knowing that if the toolset includes a door-shaped mould, it probably means that our car should have at least one door &#8211; for which other reason would those guys have built such a tool if they hadn&#8217;t built a door for their car before?
</p>

<p style="text-align: justify;">
  This makes Turmeric a very good candidate to be used as the tooling for my research. But Turmeric isn&#8217;t, in my point of view, a very good candidate anymore. It&#8217;s evolved from that into an <strong>excellent</strong> candidate at that! Now it&#8217;s the time when I really have to shine a light on <strong>all</strong> the guys behind the task of open-sourcing eBay&#8217;s platform. Those guys form a small community of people who usually hang around #turmeric-dev at irc.freenode.net and who just happen to be extremely friendly and helpful. Every time I hit a road bump with Turmeric, these guys go out of their ways to help me achieve the things I&#8217;m trying to achieve and I think that&#8217;s a lot more than I could have ever asked for.
</p>

<p style="text-align: justify;">
  Quickly moving to the topic of open-source, since Turmeric SOA is actually an open-source project, this made me ever so fond of open-source stuff. It&#8217;s really nice to see all these people dedicated in making such a tremendous contribution that is open-sourcing a platform from eBay to the good of the community. I love that. I love being able to &#8211; should I need &#8211; download a relational database management system from Apache without having to pay for it. I love seeing projects like Ubuntu flourish, showing companies that even software is all about the people it&#8217;s built to and with a little help, even an open-source can kick big corporations in their royal butts.
</p>

<p style="text-align: justify;">
  All this to say that I&#8217;ve learned a whole lot over the last few days. Amongst the things I&#8217;ve learned is for example, git. The cool kids&#8217; versioning system. As Turmeric nowadays relies on Git for its version management, I thought now would be a good time to learn it and see what advantages it brings over SVN &#8211; and boy, does it leave SVN in its rear view mirror! I&#8217;ve grown so much accustomed to it that I&#8217;ve started moving my projects to Git as well and I&#8217;ve been trying to influence other people around me to use it (Andy, if you&#8217;re reading this, wink wink, nudge nudge ;)). The saddest part of it all is that, in my opinion, you don&#8217;t really fully understand the advantages it brings until you really give it a try with real source code that you must maintain in collaboration with other people.
</p>

<p style="text-align: justify;">
  Going on a bit of a tangent, Git (and open-source) has also enabled me to propose some enhancements to David Carver&#8217;s (Turmeric SOA&#8217;s top man) IRC bot that idles around #turmeric-dev &#8211; all via the clever features of Github, forking and pull requesting.
</p>

<p style="text-align: justify;">
  <a href="https://www.tiagoespinha.net/wp-content/uploads/2011/08/46833_425136126860_586946860_5624931_1569623_n.jpg" rel="lightbox[490]" title="46833_425136126860_586946860_5624931_1569623_n"><img class="alignleft size-full wp-image-499" title="46833_425136126860_586946860_5624931_1569623_n" src="https://www.tiagoespinha.net/wp-content/uploads/2011/08/46833_425136126860_586946860_5624931_1569623_n.jpg" alt="" width="254" height="259" /></a>To finalize, the Apache Software Foundation. I&#8217;m gonna make it short and sweet. As of a couple of days ago, my fellow open-sourcers at Apache Derby decided to vote me to become a PMC (Program Management Committee) member for the Apache DB project. I have, of course, accepted and it is a post I will do my best to honor and live up to. I started off as a Google Summer of Code student at Apache Derby, then got promoted to committership, this year I had the privilege to mentor Siddharth Srivastava and now I&#8217;m becoming a PMC member. Life&#8217;s good.
</p>

<p style="text-align: justify;">
  It&#8217;s late now, time for sleep. If you&#8217;ve read it all the way down here, thank you! You&#8217;re brave!
</p>

<p style="text-align: justify;">
  Good night!
</p>