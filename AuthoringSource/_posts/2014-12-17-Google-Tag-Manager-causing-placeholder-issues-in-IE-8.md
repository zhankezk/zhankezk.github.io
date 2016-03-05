--- 
layout: post
title: "Google Tag Manager causing placeholder issues in IE 8"
author: "Ke"
comments: true
---
__Issue:__
On form submit, if the field doesn't have content. Placeholder text are being submitted with form post.

__Background:__
I am not front-end, so can't guarantee following are 100% correct regarding our FE setup.
So basically we have forms, we use placeholder attributes for form fields, however IE8 doesn't support this HTML5 feature, so we added third party plugin to support IE8 (I assume it's jQuery.Placeholder).

Also the site is using Google Tag Manager with Google Universal Analytics. It has the Form Submit Listener tag setup with "Wait for tags" and "Check validation" both checked. And it has 2 firing rules:
url contains xxxx - this is matches when accessing the page
Url contains yyyy and {event} = gtm.formSubmit - this one doesn't because it's matching itself's event

__Findings:__
If this tag is fired, which means at least one of the 2 rules must match, because this incorrect criteria "{event} = gtm.formSubmit". It somehow blocks or interfere with form submit event, must have submitted the form before some other JavaScript functions get triggered.

__Solution:__
Remove the incorrect rule, issues are gone.