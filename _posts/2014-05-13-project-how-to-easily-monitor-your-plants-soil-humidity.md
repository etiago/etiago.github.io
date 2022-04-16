---
id: 689
title: '[Project] How to easily monitor your plants&#8217; soil humidity'
date: 2014-05-13T20:02:06+00:00
author: Tiago Espinha
guid: http://www.tiagoespinha.net/?p=689
permalink: /2014/05/project-how-to-easily-monitor-your-plants-soil-humidity/
categories:
  - DIY
  - Hardware
  - Raspberry Pi
  - Software
tags:
  - Arduino
  - DIY
  - Do it yourself
  - dupont cables
  - How To
  - Pebble
  - Python
  - Raspberry Pi
  - soil moisture
  - Soil moisture monitoring
  - Soil moisture sensor
  - YL-38
  - YL-69
---
<h3 style="text-align: justify;">
  You came here to learn about soil humidity monitoring, right?
</h3>

<p style="text-align: justify;">
  Then you should probably scroll down to the part where I have a photo of my setup. However, if you have the time and feel like reading some of my ramblings, why don&#8217;t you just continue with the next paragraph? I promise you won&#8217;t be disappointed!
</p>

<h3 style="text-align: justify;">
  My beginning as an urban farmer
</h3>

<p style="text-align: justify;">
  Spring is here and with it comes the sunshine, even in <a href="http://en.wikipedia.org/wiki/Netherlands#Climate">rainy Netherlands</a>. For this reason I recently started growing all kinds of things at home. First I started with some of those tiny thumb-sized vases which come bundled with sunflower and lavender seeds but&#8230; soon after, I realized those vases were not gonna be big enough to hold that many seeds. Determined to see those plants through to flowering, I started buying bigger vases and soil. Soon after that, I was growing not only the sunflowers and lavender but I sowed some seeds I had bought a long time ago. I was now growing several shoots of <em><a href="http://en.wikipedia.org/wiki/Mimosa_pudica">mimosa pudica</a> (aka the shy plant, famous for the fact that it closes its leaves when you poke it &#8211; which you can see <a href="https://www.youtube.com/watch?v=BLTcVNyOhUc">on Youtube</a>)</em>, a few more seedlings of <em><a href="http://en.wikipedia.org/wiki/Allium_tuberosum">chinese chives</a> (or scientifically speaking, allium tuberosum</em><em>, delicious in many dishes)</em> and my proudest plantation, seedlings of the hottest pepper in the world: the <em><a href="http://en.wikipedia.org/wiki/Trinidad_moruga_scorpion">trinidad moruga scorpion</a>, which i</em>n the the <a href="http://en.wikipedia.org/wiki/Scoville_scale">Scoville scale</a> is said to be approximately 500 times hotter than your average Jalapeño or Chipotle chilli. Now THAT&#8217;S spicy!
</p>

<p style="text-align: justify;">
  You like the post so far? Well keep on reading then!
</p>

<p style="text-align: justify;">
  <!--more-->
</p>

<h3 style="text-align: justify;">
  Okay, I became a farmer.
</h3>

<p style="text-align: justify;">
  Yeah okay, I didn&#8217;t start farming because the weather was nice. Most people who face the same circumstances will just go to the beach or do a barbecue or just have a beer with friends in the sunshine but&#8230; I realized I like farming. In a more and more brick and mortar world where everywhere there&#8217;s buildings and cars and in a world where more and more the artificial replaces the natural, it is nice to have a small piece of nature close by.
</p>

<p style="text-align: justify;">
  At this point I had a substantial collection of vases and it didn&#8217;t take me long to realize that I sometimes would forget my plants and the soil would be bone dry. Whilst plants make for great landscape, they are very unobtrusive and don&#8217;t exactly ask for water the same way my cat used to. So I decided to put my skills to good use and do something about it. After some browsing on eBay I found the perfect tool for the task: soil moisture sensors. It is important that you realize that these sensors are nothing but metal plates with a silicon coating so don&#8217;t expect anything too fancy and always remember the adage: you get what you pay for.
</p>

<p style="text-align: justify;">
  The sensors themselves are pretty useless but I had a few Raspberry Pi boards laying around so I started investigating whether it would be possible to take analog readouts with it, which, to my dismay, was not possible. At least not without using a USB soundcard (it&#8217;s pretty ingenious actually&#8230; when you think of it, what&#8217;s sound if not analog current waves at different frequencies?). So I decided to be more professional and bought an old friend of mine: an Arduino Nano board which can take all kinds of readouts. It does have however the inconvenient of not being able to push the readouts anywhere. You can&#8217;t connect it to a network which means you can&#8217;t exactly take the data out into a database and plot it without additional devices and so the Raspberry Pi came to rescue!
</p>

<h3 style="text-align: justify;">
  Time to join the forces of my inner farmer and inner nerd together!
</h3>

<p style="text-align: justify;">
  What was my goal then? I wanted to build a setup that would allow me to plot a nice graph with a live readout from my plants&#8217; soil humidity. Two problems there: to plot a graph you&#8217;ll need to store the data somewhere and&#8230; with the cheap soil moisture sensors I had bought, &#8220;live&#8221; was not going to be possible. <strong>This is something I cannot stress enough: if you&#8217;ll use the same sensors as me, do NOT leave them powered for longer than what is needed to take the readout.</strong> Below in this post I explain why.
</p>

<p style="text-align: justify;">
  So in the end, I setup the following (photo below):
</p>

<p style="text-align: justify;">
  &#8211; Raspberry Pi, connected to my home network (the red UTP cable).
</p>

<p style="text-align: justify;">
  &#8211; Arduino, plugged to the soil moisture sensors and connected via USB to the Raspberry Pi.
</p>

<div id="attachment_694" style="width: 522px" class="wp-caption alignleft">
  <a href="https://www.tiagoespinha.net/wp-content/uploads/2014/05/2014-05-09-12.13.19.jpg" rel="lightbox[689]" title="[Project] How to easily monitor your plants' soil humidity"><img class="wp-image-694" src="https://www.tiagoespinha.net/wp-content/uploads/2014/05/2014-05-09-12.13.19.jpg" alt="Raspberry Pi + Arduino wired together" width="512" height="384" /></a>
  
  <p class="wp-caption-text">
    Raspberry Pi + Arduino wired together
  </p>
</div>

<p style="text-align: justify;">
  Then with some of my rusty C code I was able to get the Arduino up and running and sending data back to the Raspberry Pi.
</p>

<p style="text-align: justify;">
  At this point please understand that there are a <strong>multitude of ways</strong> in which the <strong>exact same thing can be achieved</strong>. This is just what I came up with after experimenting with a couple of ways.
</p>

<p style="text-align: justify;">
  In essence, what I have is: three DuPont cables going from separate digital pins on the RPi which in turn connect to separate digital pins on the Arduino Nano. The Arduino Nano has one digital pin per soil moisture sensor (which is plugged to the VCC in each of the small devices on the right&#8230; they are YL-38 sensors and are explained later) and one analog pin also per soil moisture sensor (plugged to the A0 in the same YL-38 devices, to take the soil moisture readings).
</p>

<p style="text-align: justify;">
  The idea is that periodically the Raspberry Pi will send a signal to the Arduino on a specific digital pin which will then cause the Arduino board to power the small bridge device which in turn outputs an analog readout (essentially an AC wave) which the Arduino listens on and prints to the serial console.
</p>

<p style="text-align: justify;">
  <strong>FRIENDLY ADVICE: </strong>After reading around, I learned it is best to do this for short periods of time &#8211; namely, not for longer than just a few seconds. If you keep the bridge device powered at all times, your sensor probes will rust within the hour due to the electrolysis which the DC current will cause to the plates. After that happens, your sensor is pretty much garbage as the sensor probes will have corroded and the moisture readouts will have become inaccurate.
</p>

<p style="text-align: justify;">
  Also of note is how the readings might fluctuate just after you powered the sensor. For this reason it is wise to take a series of readings (I take 20) and discard the first few (I discard the first half). Then you might as well just store a burst of readings which you can later plot into a graph.
</p>

<h3 style="text-align: justify;">
  What do you need exactly?
</h3>

<p style="text-align: justify;">
  My goal is to merely give you the idea and the very general pointers of how to get around doing something like this. It&#8217;s most definitely not difficult and anyone with a basic understanding of electronics can get it up and running in a matter of hours. This was a lot of fun for me to figure out myself and for this reason I will not publish the code but merely give you, the reader, a general idea of what has to be done. With this and some programming knowledge, you should be able get this up and running in no time. Here&#8217;s a very general walkthrough:
</p>

<ul style="text-align: justify;">
  <li>
    Get both a Raspberry Pi and an Arduino board. It doesn&#8217;t matter which Arduino. There&#8217;s many different types and I&#8217;ve chosen the Nano variant because it strikes a great balance between functionality and form-factor.
  </li>
  <li>
    You&#8217;ll also need a breadboard and DuPont wires. You can get these cheaply off eBay and I found that for most of these usages, male to female cables are ideal (the male end goes into the breadboard whereas the female end can plug directly into sensors&#8217; pins).
  </li>
  <li>
    Obviously you&#8217;ll also need soil moisture sensors (photo below). There&#8217;s a lot of variety here both in quality and price range. To get started I suggest you look for the cheap kind on eBay where you can get a Chinese-built YL-69 (although I normally just search for &#8216;soil moisture sensor&#8217;) for a little over 2 euro. These sensors also come with a &#8216;middle-man&#8217; circuit which allows you to get two outputs: one is an analog readout of the resistance between the sensor&#8217;s two plates and the second is a digital output (essentially, HIGH or LOW, 5v or 0v) depending on whether the humidity is above or below a threshold which can in turn be adjusted by a built-in POTS. Personally I just take the analog readout and ignore the digital one. This allows me to make pretty graphs like you can see later in this post.
  </li>
</ul>

<div id="attachment_701" style="width: 522px" class="wp-caption alignleft">
  <a href="https://www.tiagoespinha.net/wp-content/uploads/2014/05/2014-05-09-12.51.20.jpg" rel="lightbox[689]" title="[Project] How to easily monitor your plants' soil humidity"><img class="wp-image-701" src="https://www.tiagoespinha.net/wp-content/uploads/2014/05/2014-05-09-12.51.20.jpg" alt="Above, the soil moisture sensor itself (YL-69). Below, the bridge device which you'll need to use (YL-38)." width="512" height="384" /></a>
  
  <p class="wp-caption-text">
    Above, the soil moisture sensor itself (YL-69). Below, the bridge device which you&#8217;ll need to use (YL-38).
  </p>
</div>

<p style="text-align: justify;">
  After you have all the materials, it&#8217;s very simple to get started. The <strong>YL-69</strong> sensor itself has two pins which need to be wired to the two pins on the <strong>YL-38</strong> bridge (specifically, the two isolated pins). On the other end of the YL-38, you have four pins which (top to bottom) represent VCC, GND, D0 and A0. VCC and GND are your power pins which should be set to 3.3/5V and Ground (respectively) and your A0 is an analog output which you will connect to an analog input on the Arduino board (the Arduino Nano has 8 analog pins) via the breadboard.
</p>

<p style="text-align: justify;">
  <strong>FRIENDLY REMINDER: </strong>DO NOT keep the YL-38 bridge powered for long periods of time. If you leave it permanently on, it will keep applying DC current to the YL-69 sensor which will cause corrosion due to electrolysis. If you want to keep your sensors in good shape for as long as possible, you will only apply power to VCC before you make a reading. Additionally, be sure to at least every week switch the two cables going to the YL-69 sensor as to slow down corrosion as much as possible.
</p>

<p style="text-align: justify;">
  This being said, you&#8217;ll want to plug the VCC on the YL-38 bridge to a digital pin on the Arduino board which you will set to HIGH (thus effectively powering the bridge) before making a reading.
</p>

<p style="text-align: justify;">
  When you have the Arduino and the sensors all hooked up, you&#8217;ll want to get this plugged to your laptop so you can start experimenting with the code. If you need further help with this part, please drop me a comment or an e-mail (tiagoRemove-me-and-add-at-or-elseEspinha.nl)!
</p>

<p style="text-align: justify;">
  After that&#8217;s done, all you have to do is use one of the GPIO pins in the Raspberry Pi as a signal for the Arduino to start a reading. Essentially my (Python) script does the following goes something like:
</p>

<ul style="text-align: justify;">
  <li>
    This script first sets a GPIO pin to HIGH.
  </li>
  <li>
    The Arduino is continuously listening to this pin and once it is raised to HIGH, sets the sensor&#8217;s VCC to HIGH.
  </li>
  <li>
    The Arduino continuously prints readouts from the sensor to the serial console.
  </li>
  <li>
    The Python script is reading the USB output (i.e. the serial console) of the Arduino board and storing the readouts.
  </li>
  <li>
    The Python script sends the readouts to my webserver where they are stored in a database.
  </li>
</ul>

<p style="text-align: justify;">
  Obviously, for this to work you&#8217;ll need the Python libraries for the Raspberry Pi GPIO and I recommend the Python library for dealing with serial devices.
</p>

<p style="text-align: justify;">
  After all&#8217;s said and done, I can generate a graph such as this:
</p>

<h3 style="text-align: justify;">
  <a href="https://www.tiagoespinha.net/wp-content/uploads/2014/05/Screenshot-2014-05-13-20.35.53.png" rel="lightbox[689]" title="[Project] How to easily monitor your plants' soil humidity"><img class="alignleft wp-image-699" src="https://www.tiagoespinha.net/wp-content/uploads/2014/05/Screenshot-2014-05-13-20.35.53.png" alt="Screenshot 2014-05-13 20.35.53" width="512" height="185" /></a>But wait, there&#8217;s more!
</h3>

<p style="text-align: justify;">
  I&#8217;m also the proud owner of a Pebble watch, so why not put this to good use, I thought! Everything was already in place so all I had to do was set up an alert system that monitors the last collected data. If it&#8217;s above a &#8220;drought threshold&#8221;, I receive an alert on my Pebble. But there&#8217;s still more! As soon as I water my plants, I get another alert as seen below:
</p>

# <a href="https://www.tiagoespinha.net/wp-content/uploads/2014/05/2014-04-28-08.41.21.jpg" rel="lightbox[689]" title="[Project] How to easily monitor your plants' soil humidity"><img class="wp-image-700 aligncenter" src="https://www.tiagoespinha.net/wp-content/uploads/2014/05/2014-04-28-08.41.21.jpg" alt="2014-04-28 08.41.21" width="360" height="480" /></a>

&nbsp;

<h3 style="text-align: justify;">
  To conclude
</h3>

<p style="text-align: justify;">
  Thanks for reading all the way here! I hope my post was of some help for you to start in a similar endeavor. I tried to keep the technicalities (scripts, etc) down to a minimum because, well, that was the most fun part of it and I wouldn&#8217;t want to spoil any of it for you! However, if you get yourself into some trouble and you need some help to move forward, feel free to drop me a comment or, more wisely, drop me an e-mail. You can reach me at tiagoRemove-me-and-add-at-or-elseEspinha.nl.
</p>

<p style="text-align: justify;">