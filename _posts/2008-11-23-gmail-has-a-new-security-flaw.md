---
id: 146
title: GMail has a new security flaw
date: 2008-11-23T12:20:40+00:00
author: Tiago Espinha
guid: http://www.tiagoespinha.net/?p=146
permalink: /2008/11/gmail-has-a-new-security-flaw/
categories:
  - Security
tags:
  - GMail
  - GMail Flaw
  - Google Mail
  - Security Flaw
---
<p style="text-align: justify;">
  That&#8217;s right folks GMail has a massive security hole which, to the extent of my knowledge, remains unpatched. Aibek at MakeUseOf.com has <a href="http://www.makeuseof.com/tag/breaking-gmail-security-flaw-more-domains-get-stollen/" target="_blank">thoroughly explained</a> what happened to him and to others, and if you are really curious about the detauks, then it is definitely worth checking out.
</p>

<p style="text-align: justify;">
  I will, in a brief and resumed way, describe the situation and what you can do to play it safe(r).
</p>

<p style="text-align: justify;">
  What happens is that through a trick with URLs and attacking websites, an attacker can effectively enable your e-mail forwarding to whichever e-mail the said attacker wants to. Basically, this way, they get access to all your incoming e-mail because it gets forwarded to their inbox.
</p>

<p style="text-align: justify;">
  In Aibek&#8217;s case, the attacker managed to somehow steal the e-mail that contained the password to access his domain registrar account. The attacker then transfered the domain to another registrar and started to blackmail Aibek, claiming that he wanted $2000 for the domain that he originally owned.
</p>

<p style="text-align: justify;">
  This is a very serious situation, and maybe this is just the tip of the iceberg; a lot of malicious actions can be conducted this way and the first and foremost thing you should do right now if you own a GMail account, is to check under Settings -> &#8220;Forwarding and POP/IMAP&#8221; if your forwarding is set to some unknown address. If it is, then you are highly advised to disable the forwarding and <strong>change all your passwords</strong>. Especially if you have received e-mails from password recovery systems that you didn&#8217;t ask for in the first place.
</p>

<p style="text-align: justify;">
  The next tip is to never open links that come within e-mails that you don&#8217;t totally trust. If you must open the link anyway, then rather than clicking it, copy the link, logout from your GMail account and then visit the link. When you&#8217;re done, log back in and you should be safe.
</p>

<p style="text-align: justify;">
  It is yet to be known if this flaw affects Google Apps accounts as well. In a wild guess I would say it does, but it would have to be customized to attack a specific domain belonging to Google Apps, so everyone, be wary.
</p>