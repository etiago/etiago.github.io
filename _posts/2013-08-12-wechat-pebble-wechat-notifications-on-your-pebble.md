---
id: 595
title: 'WeChat Pebble &#8211; WeChat notifications on your Pebble!'
date: 2013-08-12T17:04:38+00:00
author: tiago
layout: post
guid: http://www.tiagoespinha.net/?p=595
permalink: /2013/08/wechat-pebble-wechat-notifications-on-your-pebble/
categories:
  - Android
  - Software
tags:
  - Android
  - Android app
  - notifications
  - Pebble
  - Pebble Smartwatch
  - Pebble Unicode
  - Pebble watchapp
  - Smartwatch
  - Unicode support Pebble
  - WeChat
  - WeChat notifications
  - WeChat notifications Pebble
  - WeChat Pebble
---
As the [Pebble smartwatch](http://getpebble.com/) is becoming more and more mainstream, so is the need for supporting a wider range of messaging applications. While much of the Western world does not know about [WeChat](http://www.wechat.com/), surely everyone has at some point or another heard of WhatsApp or Blackberry Messenger. Well, WeChat is very much the same thing but it&#8217;s the most popular mobile instant messaging chat in China with over **300 million users**! The single one feature that makes WeChat unique is having a walkie-talkie feature in its very core. At the literal push and release of a single button, WeChat users can send voice messages to each other, thus avoiding all the trouble of typing.

Because WeChat is popular in China, it is bound to push notifications which include Chinese characters. These characters are currently not supported in the Pebble (it uses Unicode for character encoding but due to space restriction it does not include fonts for characters beyond the Latin alphabet) and WeChat Pebble also takes this issue out of the way.

Adding a font with 2000~3000 characters seems to be troublesome due to severe space restrictions in the Pebble firmware. Therefore, I came up with an approach which makes use of the [Unifont character library](http://unifoundry.com/unifont.html) to render messages on the Android app and send them to the Pebble watch as a bitmap. This effectively solves the problem not only for Chinese but also for Russian, Hebrew, you name it!

<div id="attachment_600" style="width: 287px" class="wp-caption aligncenter">
  <a href="https://www.tiagoespinha.net/wp-content/uploads/2013/08/2013-07-31-13.57.36.jpg" rel="lightbox[595]" title="WeChat Pebble - WeChat notifications on your Pebble!"><img class="wp-image-600" alt="WeChat Pebble in action!" src="https://www.tiagoespinha.net/wp-content/uploads/2013/08/2013-07-31-13.57.36.jpg" width="277" height="368" /></a>
  
  <p class="wp-caption-text">
    WeChat Pebble in action!
  </p>
</div>

All of this is available as open-source and for free.

-> **If you are a developer**, read past the installation steps for some hardcore open-source goodies

-> **If you just want to use this** and don&#8217;t care about the source code, just read the following two simple steps!

<span style="line-height: 16px;">1 &#8211; Install the Android app available in the Play Store <a href="http://play.google.com/store/apps/details?id=com.espinhasoftware.wechatpebble">here</a> or by scanning the QR code below.<br /> </span>

**NOTE: **For the app to actually push the WeChat notifications you have to first start the app and follow the instructions. Also keep in mind that in the Settings you can choose different types of notifications.

<div id="attachment_596" style="width: 178px" class="wp-caption aligncenter">
  <a href="https://www.tiagoespinha.net/wp-content/uploads/2013/08/market.png" rel="lightbox[595]" title="WeChat Pebble - WeChat notifications on your Pebble!"><img class="wp-image-596" alt="Play Store" src="https://www.tiagoespinha.net/wp-content/uploads/2013/08/market.png" width="168" height="168" /></a>
  
  <p class="wp-caption-text">
    Play Store
  </p>
</div>

<span style="line-height: 16px;">(N.B. If for some reason you cannot access the Android Play Store, the .apk is also available directly from my website by clicking <a href="http://www.tiagoespinha.net/wechatpebble/WeChatPebble.apk">here</a>.)</span>

&nbsp;

2 &#8211; Install the Pebble watchapp by installing this [.pbw](http://www.tiagoespinha.net/wechatpebble/watchface.pbw) or by scanning the QR code below.

<div id="attachment_597" style="width: 178px" class="wp-caption aligncenter">
  <a href="https://www.tiagoespinha.net/wp-content/uploads/2013/08/watchapp.png" rel="lightbox[595]" title="WeChat Pebble - WeChat notifications on your Pebble!"><img class="wp-image-597" alt="Pebble Watch App (.pbw)" src="https://www.tiagoespinha.net/wp-content/uploads/2013/08/watchapp.png" width="168" height="168" /></a>
  
  <p class="wp-caption-text">
    Pebble Watch App (.pbw)
  </p>
</div>

&nbsp;

After this you&#8217;re pretty much done! Just enjoy and feel free to drop me a comment below or visit the Pebble forums&#8217; [here](http://forums.getpebble.com/discussion/6719/working-full-unicode-font-support-in-the-pebble)! I will keep updating this post with news on the WeChat Pebble app.

The source code is available for free on GitHub: <https://github.com/etiago/WeChatPebble>