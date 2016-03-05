--- 
layout: post
title: "Section references in Sitecore config files with ref attribute"
author: "Ke"
comments: true
---

Have seem a lot of usages with "ref" attributes when setting up Sitecore Lucene Indexes. Normally it's used to refer to another section of the config file. But I wanted to do more and couldn't find any more information about it. After some guessing and decompiling of Sitecore Dlls, here are some information I got.

* Attribute "ref" can be used to refer to another section of the configuration files in Sitecore.
* The value of attribute "ref" is using Xpath.
* Attribute "ref" are being used to create objects in all places and eventually come to this method:

```cs
public static object CreateObject(XmlNode configNode, string[] parameters, bool assert, IFactoryHelper helper)
{object obj = (((Factory.CreateFromFactory(configNode, parameters, assert) ?? Factory.CreateFromFactoryMethod(configNode, parameters, assert)) ?? Factory.CreateFromReference(configNode, parameters, assert)) ?? Factory.CreateFromTypeName(configNode, parameters, assert)) ?? Factory.CreateFromConnectionStringName(configNode, parameters, assert);}
```

* When obj is still null, it returns the value as string.

So this is always being used to create a obj to assign to a property of the parent node.

when a node has 'hint="list:xxx"', it means it's mapping to a method of the parent node's type("type" atttibute). (please ref to this [Sitecore configuration factory and dependency injection](http://www.sitecore.net/Learn/Blogs/Technical-Blogs/John-West-Sitecore-Blog/Posts/2011/02/The-Sitecore-ASPNET-CMS-Configuration-Factory.aspx) article on Sitecore Blog for more details)
Hope that helped you. Now if you still have time, you can keep reading to learn my story.

First, when setting up Sitecore 7 Lucene Index, you must have come across this line in the config:

```xml
<Analyzer ref="contentSearch/indexConfigurations/defaultLuceneIndexConfiguration/analyzer" />
```
This works great, but I wanted to use it for "ExcludeField" fields as well to keep my custom index configuration clean. The default configuration looks like this:

```xml
<exclude hint="list:ExcludeField">
<__display_name>{B5E02AD9-D56F-4C41-A065-A133DB87BDEB}</__display_name>
</exclude>
```

So I have tried to do this:

```xml
<exclude ref="contentSearch/indexConfigurations/defaultLuceneIndexConfiguration/exclude[@hint='list:ExcludeField']" />
and:
<exclude hint="list:ExcludeField" ref="contentSearch/indexConfigurations/defaultLuceneIndexConfiguration/exclude[@hint='list:ExcludeField']" />
```

None of them worked. Though the xpath is correct, but "ExcludeField" is a method and when you use "ref", it tries to create an object as a property, so it fails.

Therefore my conclusion is that you can't use "ref" in configuration files for referencing methods. This is bad news for my clean configuration initiative, I still need to do more digging on this, will post it in another post which will focus on Sitecore Custom Lucene Indexes.