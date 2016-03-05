--- 
layout: post
title: "Sonos with Airsonos on Windows and Mac"
author: "Ke"
comments: true
---
Installing on Mac was very smooth, and playback is perfect, I used it for about 5 to 6 songs, no problems at all. So I'll say it's great on Mac.

Though my home server is running Windows Home server 2011, I don't want to keep my Mac air on all the time, so obviously it'd be must better if home server can run Airsonos. But then nightmare begins.

I had

* Couldn't locate vcbuild.exe
* fatal error c1083: cannot open include file
* something something is not build for x64 platform
* Need python

errors.

So after:

* Using 32 bit Node.js
* Installed Python 2.7
* Installed VS ++ 2010
* Installed Bonjour SDK

I was finally be able to start Airsonos on my windows server and successfully located my sonos player.

However then when I connect to it on iPhone, it stuck and disappears, over and over again, wouldn't play at all. I tried disabling the windows firewall, didn't work.

So anyway, just want to help those people who are trying it on windows. Good luck!