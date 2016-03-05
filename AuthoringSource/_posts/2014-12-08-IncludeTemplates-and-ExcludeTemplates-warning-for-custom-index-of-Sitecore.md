--- 
layout: post
title: "IncludeTemplates and ExcludeTemplates warning for custom index of Sitecore"
author: "Ke"
comments: true
---
It all started with those lines in defaultIndexConfiguration from Sitecore.ContentSearch.Lucene.DefaultIndexConfiguration.config:

```xml
<!-- If no configuration is specified for an index, it uses the default configuration. The configurations are not merged if the index also has a configuration. The system uses either the default configuration or the index configuration. -->
<!-- GLOBALLY EXCLUDE TEMPLATES FROM BEING INDEXED
This setting allows you to exclude items that are based on a specific template.-->
<exclude hint="list:ExcludeTemplate">
      <bucketfoldertemplate>{ADB6CA4F-03EF-4F47-B9AC-9CE2BA53FF97}</bucketfoldertemplate>
</exclude>
```

So when I setup custom index for Sitecore, I created a new index configuration like this:

```xml
<configuration xmlns:patch="http://www.sitecore.net/xmlconfig/">
  <sitecore>
    <primary>
        <primaryluceneconfiguration type="Sitecore.ContentSearch.LuceneProvider.LuceneIndexConfiguration, Sitecore.ContentSearch.LuceneProvider">
          <include hint="list:IncludeTemplate">
            <sometemplate>{00000-000-0000-0000-0000000000</sometemplate>
          </include>
```

Then I set this configuration for our index:

```xml
<configuration xmlns:patch="http://www.sitecore.net/xmlconfig/">
  <sitecore>
    <contentsearch>
      <configuration type="Sitecore.ContentSearch.LuceneProvider.LuceneSearchConfiguration, Sitecore.ContentSearch.LuceneProvider">
        <indexes hint="list:AddIndex">
          <index id="Primary Site Search" type="Sitecore.ContentSearch.LuceneProvider.LuceneIndex, Sitecore.ContentSearch.LuceneProvider">
            <param desc="name">$(id)</param>
            <param desc="folder">$(id)</param>
            <param desc="propertyStore" ref="contentSearch/databasePropertyStore" param1="$(id)" />
            <configuration ref="primary/PrimaryLuceneConfiguration" />
```

Everything works fine, but here comes the issue, in Crawling.log.xxxx.txt log files. I got this warning 

>"XXXX 22:05:53 WARN You have specified both IncludeTemplates and ExcludeTemplates. This logic is not supported. Exclude templates will be ignored." 

for every item that it indexes.

If I remove the node `<exclude hint="list:ExcludeTemplate">` from the defaultIndexConfiguration, the warnings are gone.

Just don't understand why the excludes from the defaultconfiguration still affects my custom index when I have a complete different new index configuration.

Anyway, still trying to figure out what's wrong, will update if I have new findings.

Sitecore version: Sitecore.NET 7.1 (rev. 140324)