--- 
layout: post
title: "Schedule tasks not running on CDS in Sitecore"
author: "Ke"
comments: true
---
Had a schedule task setup to generate sitemap.xml for the client, however found that it's working on CAS, but not on CDS.

Turns out since SwitchMasterToWeb.config is used when setting up CDS environment, it removes scheduling agents, only leave core in there. 

So the solution is to add a new agent in there and set the <param desc="database"> to web. Wait for interval time, things should start working.

And the way to check this is from the log file, search for "Examining schedules", then you will know if your setups are successful or not. 