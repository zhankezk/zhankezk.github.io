--- 
layout: post
title: "A New Back Engine for Blog"
author: "Ke"
comments: true
---

In order to stick to my previous post which states that I will not change the blog platform anymore but focus on writing content. I came up with an idea that to create an Asp.Net website to edit markdown files, generates the html site, then use git to commit to Github. 
 
I know, kind of ridiculous. Why do I bother? Just setup a dynamic blog! 
 
But you know, we, developers, always do stuff just because... we can... 
 
Of course there're more genuine reasons: 
 
1. Tiered of changing blog platform, will try to keep it as static html site from now on. 
2. Can utilize Github Page and Azure free App Service. Not saying hosting a website is too much money, just don't feel it's worth the money for me. 
3. As a practice for Asp.Net 5(or Core 1?) 
 
Did a quick research, this is achievable with the following libraries/tools: 
 
1. libgit2sharp - git api in C sharp - https://github.com/libgit2/libgit2sharp/ 
2. pretzel - static html site generator in C sharp - https://github.com/Code52/pretzel 
 
And a online markdown editor and file management definitely exist. 