--- 
layout: post
title: "IIS Http error 500.19 with web.config"
author: "Ke"
comments: true
---
Got this error again and again, always takes about half hour to remember that it's the IIS missing "Url rewrite" module!

>HTTP Error 500.19 - Internal Server Error
The requested page cannot be accessed because the related configuration data for the page is invalid.

>Detailed Error Information:
Module	   IIS Web Core
Notification	   Unknown
Handler	   Not yet determined
Error Code	   0x8007000d
Config Error	   
Config File	   \\?\X:\kb\web.config
Requested URL	   http://kb/
Physical Path	   
Logon Method	   Not yet determined
Logon User	   Not yet determined
