--- 
layout: post
title: "Get Sitecore Item SiteInfo"
author: "Ke"
comments: true
---
Problem rises when the site index contains items from multiple sites and they need to have accurate urls gengerated for the items returned. And in this case, one site is a descendant of another site in Sitecore content tree.

I got the idea from a post in [stackoverflow](http://stackoverflow.com/questions/14200864/how-to-find-out-with-which-sitecore-site-an-item-is-associated), however improved it a bit so it matches the site more accurately.

```csharp
public static SiteInfo GetSite(this Item item)
{
	var siteInfoList = Sitecore.Configuration.Factory.GetSiteInfoList();

	SiteInfo currentSiteinfo = null;
	var matchLength = 0;
	foreach (var siteInfo in siteInfoList)
	{
		if (item.Paths.FullPath.StartsWith(siteInfo.RootPath, StringComparison.OrdinalIgnoreCase) && siteInfo.RootPath.Length > matchLength)
		{
			matchLength = siteInfo.RootPath.Length;
			currentSiteinfo = siteInfo;
		}
	}

	return currentSiteinfo;
}
```

Then you can use urlOption with Sitecore LinkManager to generate urls:

```csharp
var urlOptions = UrlOptions.DefaultOptions;
var siteInfo = item.GetSite();
if (siteInfo != null)
{
	urlOptions.Site = new SiteContext(siteInfo);
}
var url = LinkManager.GetItemUrl(item, urlOptions);
```