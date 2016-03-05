--- 
layout: post
title: "AnyoneHue? - Monitor multiple people with WIFI for Philips Hue controlling"
author: "Ke"
comments: true
---

Quite happy with Philips Hue 2nd Generation I recently bought (From Amazon Us, not available in Australia yet). Especially with Siri, although my wife is not very impressed because she can't just use the wall switch now XD.

Anyway, pretty good stuff for first step into Smart Home Automation, however it does give me a feeling that it's designed for single people who lives along :( Because Siri can't be shared between different Apple ID and Geo Fencing only works for a single device.

Siri issue can be resolved by setting up an iOS device at home only for home automation with "Hey Siri" enabled. But Geo Fencing is pretty much useless for me. 

So I wrote a Windows Console Application that pings mine and my wife's iPhone every few seconds and turn the lights off or on accordingly.

Few things before we continue:

* It runs on windows, you need to have a windows machine that is always on when you want it to do the work.
* You need to know your Bridge IP address and device names of the devices you want to monitor.
* You need to follow Philips Developer Guide to setup API Key for your local Bridge.

UI and non-tech people friendly version will come, but not much free time at the moment, will try.

### App Name: Anyone Hue ?

Download Link: [Direct](/files/AnyoneHue_Console_v1.0.zip)

Main functionalities:

* Check multiple devices presence in local network and turn off all lights when none is connected (It's like GEO fencing for multiple people, but instead of using location, it uses wifi)
* If any device comes back online, turn on a pre-defined light to full brightness
* Can stop monitoring for particular hours defined in config, it enters sleep mode for those hours.
* Can set retry numbers and retry waiting period

Below is the web.config setting, hopefully can help you understands what are configurable for the app.

```xml
	<!-- Device names to be monitored-->
    <add key="DeviceNamesByPipes" value="Device1|Device2" />	
	<!-- Ref to http://www.developers.meethue.com/documentation/getting-started to get an API key from your bridge -->
    <add key="HueBridgeApiKey" value="APIKey" />
    <add key="HueBridgeIpAddress" value="192.168.2.X" />
	<add key="LightNameToTurnOn" value="LightName" />	
    <add key="CheckIntervalInSeconds" value="5" />
    <add key="PingTimeoutInSeconds" value="1000" />    
    <add key="RetryNumber" value="3" />
    <add key="RetryIntervalInSeconds" value="60" />	
	<!-- Active hours in a day, value can be 0 to 23 -->
    <add key="ActiveHours" value="20,21,22,23" />
	<!-- Log file name will be appended with date -->
    <add key="LogFileName" value="Scanlog" />
	<!-- Only supports /24 subnet, value can be 0 to 254 -->
    <add key="ScanStartIp" value="0" />
    <add key="ScanEndIp" value="254" />
```