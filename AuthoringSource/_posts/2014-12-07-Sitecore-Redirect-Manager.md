--- 
layout: post
title: "Sitecore Redirect Manager"
author: "Ke"
comments: true
---
Installed a Redirect manager module for some client's sitecore, but it doesn't handle multiple sites so I had to customize it to support multiple sites.

After that, local and testing deployments went well, everything were working perfectly . But then it doesn't redirect at all on one of the sites when I deployed to Staging.

After some digging, I found that the module is using HttpContext.Current.Cache, which can't be shared across different App Domain. And this sitecore instance has 2 sites. On local and testing, they share the same app domain, however on Staging it's using different ones, and on production there's even one more app domain only for sitecore client.

So I have updated the code to use System.Runtime.Cahcing, solved the problem. Lots of examples online, I won't bother about showing code here. It's just 2 things I want to point out. First, use MemoryCahce.Default, Second, Don't use Add, it doesn't override. use Set.