---
id: 640
title: Automatic Recovery of REST Interfaces
date: 2013-10-07T14:46:53+00:00
author: tiago
layout: post
guid: http://www.tiagoespinha.net/?p=640
permalink: /2013/10/automatic-recovery-of-rest-interfaces/
categories:
  - SOA
  - Software
---
<p style="text-align: justify;">
  Recovery of REST interfaces is an interesting research topic which came into conversation with one of our industrial partners and which I would like to explore. This is also something mentioned by Maleshkova et al in their work on &#8220;<em>Investigating Web APIs on the World Wide Web</em>&#8221; (<a href="http://sweet-dev.open.ac.uk/war/Papers/mmaWebAPISurvey.pdf">pre-print</a>, I<a href="http://ieeexplore.ieee.org/xpls/abs_all.jsp?arnumber=5693251&tag=1">EEE citable</a>). The authors claim that <em>&#8220;two thirds of the APIs do not state the data-type of the input and 40% of the APIs do not state the HTTP method. If a standard interface description language, such as WSDL, [was] used [&#8230;] this would be unthinkable&#8221;</em>.
</p>

<p style="text-align: justify;">
  This is very true. Read on to know more.
</p>

<p style="text-align: justify;">
  <!--more-->
</p>

<p style="text-align: justify;">
  While SOAP services are always backed up by their WSDL files which describe the interfaces, including all the methods and data types, the much more popular REST services have no such feature. Instead, developers are left with manually created web pages which describe in natural language how to invoke the web API and what the endpoints are; case in point: <a href="https://developers.facebook.com/docs/reference/api/publishing/">Facebook</a>, <a href="https://dev.twitter.com/docs/api/1.1">Twitter</a> and <a href="http://developer.netflix.com/docs/HTTP_Status_Codes">Netflix</a>. But what about when web API developers forget to change the documentation, or even worse, make a mistake when specifying the interface? This is when having automatic recovery of the REST interface would prove useful.
</p>

<p style="text-align: justify;">
  The possibilities are endless. This recovery can be done on either client or server side (or both) and each of the sides can add a different view and understanding of the communication. Where with a SOAP-generated WSDL file we know that<em></em> whatever is in the WSDL file is what&#8217;s available in the system, <em>no more, no less,</em> by doing recovery of a REST interface we can learn many things:
</p>

<ol style="text-align: justify;">
  <li>
    Client-side recovered interface: whatever is in the recovered interface <em>may or may not</em> be all that&#8217;s available on the server-side. At any rate, we know that whatever is in the recovered interface represents whatever <strong>features we are using</strong> of that particular web API (because if we recovered it from runtime data, then our client has at some point used these features).
  </li>
  <li>
    Server-side recovered interface: once again, because we&#8217;re recovering the interface from usage data (and even though on the server-side you could probably do a full recovery based on static analysis), whatever we see in the recovered interface is in fact whatever is being used by <strong>ALL</strong> our clients. This means that if you use long periods of runtime data to recover the interface, you can detect <em>potential dead code.</em> This is very much the same principle behind code coverage, except we&#8217;re testing interface coverage by client code.
  </li>
</ol>

<p style="text-align: justify;">
  This is, of course, in a very premature stage and in my mind only but it is a thought I wanted to put out there and maybe stir the discussion around this topic a little. If you have any thoughts on this feel free to drop me a comment!
</p>