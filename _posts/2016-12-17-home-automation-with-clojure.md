---
id: 775
title: 'Home Automation with Clojure (part 1)'
date: 2016-12-17T00:00:00+00:00
author: Tiago Espinha
guid: https://www.tiagoespinha.net/?p=775
permalink: /2016/12/home-automation-with-clojure-part-1/
categories:
  - Software
tags:
  - home automation
  - clojure
  - home api
---
Those who know me, know that I like simplifying things. Tasks that are repetitive quickly become chores which nobody wants to do. That's probably one of the reasons why humanity started automating things from production pipelines to software testing.
{: style="text-align: justify;"}

One of the things I've been building along the past few months is a home automation API. Specifically a web API which allows me, via HTTP calls, to control various aspects of my wannabe-smart home.
{: style="text-align: justify;"}

What do I have in my smart home, you ask? I have:

- Philips Hue lights in my kitchen, living room and house entrance.

- Surveillance cameras with motion detection.

- Flic buttons to control those smart appliances.

# Hue lights

This all started with having the Hue lights. Once you have them, you realize how convenient it is to be in bed with your smartphone and not having to care whether you turned off the lights around the house, since you can just grab your phone and turn them all off. Still, once you're able to do that, you realize that you can no longer use your house's built-in light switches since the lights need to be always on in order to function (n.b., they are always supplied current in order to stay connected to the control base but they consume very little power when they are soft-shut down). Well, that sucks! Now you went from a situation where you could flip a switch and "let there be light!" to a situation where you always need your smartphone close by just to turn on your lights: not convenient.
{: style="text-align: justify;"}

# Enter the Flic buttons

At some point I read about the Flic buttons. They're basic tools really, just a push button attached to a bluetooth module which will pair to a device (e.g., an Android phone) and trigger whenever you click it, double click it or long click it. Then it's up to you to define what each trigger will do on the attached device.
{: style="text-align: justify;"}

Initially I bought these buttons and they were working out really fine. Their Android app is very decent and provides integration with, amongst others, Philips Hue. Still, I ran into a less than ideal scenario: if I configured the app on my phone, then whenever I wasn't home nobody else could turn on or turn off the lights using the Flic buttons (since my phone would not be in range of the bluetooth network). I could have also configured the app on my wife's phone but whenever my parents or anyone eelse would visit, the problem would remain. I would run into having to configure the app countless times for whoever would be visiting me at the time.
{: style="text-align: justify;"}

### Flic Linux SDK to the rescue

What Flic also provides is a [Linux SDK](https://github.com/50ButtonsEach/fliclib-linux-hci), meaning that if you have a Linux device with a supported bluetooth dongle, you can create a program that effectively does the same as Flic's own Android app: listen to specific events of specific buttons and perform tasks accordingly.
{: style="text-align: justify;"}

That's what I did. I created a Java program (a really simple and stupid one that I'm ashamed to show 😛) which on startup connects to all the buttons and stays in a while loop listening to events from the buttons. But what a minute! How am I going to control my lights now? Oh, that's right Hue has a Web API.
{: style="text-align: justify;"}

### Come the Hue web API

The Hue web API is fairly decent. They provide an online emulator straight from your Hue control base and from there it's fairly straight forward to get started. They have documentation which gets you up and running quite fast but... it's rather limited. In particular, there was a use case of mine which wasn't covered: toggling lights. Specifically I wanted to toggle a light on the click of a button so that rather than remembering "one click is for turning on, two clicks is for turning off" and effectively already wasting two actions of a Flic button, I could have an action that's just... toggle the light. If it's on, turn it off. If it's off, turn it to whatever state it last had.
{: style="text-align: justify;"}

This, sadly, is not possible (to the best of my knowledge). Philips has decided to implement a very purist (and thus inconvenient) REST API. In a REST API you're supposed to send a **new** and **wholesome** representation of the entity you are POST-ing or PUT-ing to. REST APIs, which are in principle stateless, should therefore not refer to the previous state. Technicalities aside, it's an inconvenient API.
{: style="text-align: justify;"}

**What to do then?** Simple. I built my own API, exposed to the Internet, which allows me to control my Hue lamps via (more convenient and flexible) HTTP requests. As some people have pointed out to me, it's something like a proxy... except it's a stateful one. By now it also has a lot more functionality than what I could squeeze out of a proxy.
{: style="text-align: justify;"}

The end result is a Clojure-based web API which allows me to remotely perform actions like toggling a particular light in my home. It also now supports geofencing (e.g., when someone arrives home and it's after sunset, turn on the entrance light) and voice commands but I will leave that to another post.
{: style="text-align: justify;"}
