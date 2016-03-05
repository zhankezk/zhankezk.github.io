--- 
layout: post
title: "Browser requests page twice"
author: "Ke"
comments: true
---

## Issue: Pages gets requested twice in browsers.

* Chrome - Requesting twice.
  * In Network Tab, Initiator says "Parser".
  * Message in console
    > Resource interpreted as Image but transferred with MIME type text/html: "http://pageurl"
* Firefox - No messages, but it is requesting twice.
* Fidder - Not requesting twice.
* When use Fidder to see Chrome and Firefox's requests, the second request head contains:
  > Accept: image/webp,*/*;q=0.8

## Cause: background-image: url

```html
<div class="some-class" style="background-image: url('')"></div>
```

Don't have much to say here, not sure if it's a bug or not.
