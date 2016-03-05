--- 
layout: post
title: "Sitecore session expires(timeout) quickly(1 min) when not logged in"
author: "Ke"
comments: true
---


*Can only consider this as a note to my self since it's all over the internet already.*

## Symptoms:

Session expires very quickly for Sitecore websites. Like only 1 minute.

## Cause and solution:

In config file:

> Sitecore.Analytics.Tracking.config

Robots' session timeout is set to 1 minute

```xml
<!--  ANALYTICS ROBOTS SESSION TIMEOUT
        The ASP.NET Session Timeout for auto detected robots. 
        When the automatic robot detection identifies a session as being a robot, the ASP.NET
        Session Timeout is set to this value (in minutes).
        Default: 1
  -->
  <setting name="Analytics.Robots.SessionTimeout" value="1" />
```
And this

```asp
<sc:VisitorIdentification id="VisitorIdentification" runat="server" />
```

is not in website layout causing all visitors to be considered as robots.

For Sitecore MVC, please check [asp.net mvc - Sitecore 7.5 MVC and HttpContext.Session.Timeout set to 1 min - Stack Overflow](http://stackoverflow.com/questions/28626563/sitecore-7-5-mvc-and-httpcontext-session-timeout-set-to-1-min) out.

## Addtional Info:

While searching for this issue, I came across something that has always been bothering us, it's the CMS editor's session expires quickly. The message

>The operation could not be completed. Your session may have been lost due to a timeout or a server failure. Please try again.

shows up always when I try to select images or files. For this issue, sitecore actually has a patch, please go [Session timeout when saving Rich Text fields](https://kb.sitecore.net/articles/135940) to check it out.

For actually the places to set the session timeout for sitecore, please Google, there're plenty out there.