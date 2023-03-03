---
layout: post
title: Hive NoClassDefFoundError auxiliary path issue
date: 2015-12-22 23:15:52.000000000 -08:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Big Data
- hive
- java
tags:
- bigdata
- hive
- java
meta:
  _edit_last: '1'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: Hive NoClassDefFoundError error auxiliary path issue
  _yoast_wpseo_title: Hive NoClassDefFoundError error auxiliary path issue
  _yoast_wpseo_metadesc: Hive NoClassDefFoundError error auxiliary path issue. Resolve
    hive auxiliary path issue
  _yoast_wpseo_linkdex: '77'
  dsq_thread_id: '4425834153'
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/hive-noclassdeffounderror-auxiliary-path-issue/"
---

## Hive NoClassDefFoundError error auxiliary path issue

Hive NoClassDefFoundError error auxiliary path issue is very common. Sometimes even you add jar into classpath using below hive command, hive throws NoClassDefFound error-


```
Exception in thread "main" java.lang.NoClassDefFoundError: 
org/apache/solr/client/solrj/SolrServerException at 
com.aexp.ims.atworks.hive.solr.SolrSplit.getSplits(SolrSplit.java:84) at com.aexp.ims.atworks.hive.solr.SolrInputFormat.getSplits(SolrInputFormat.java:91)
 at org.apache.hadoop.hive.ql.exec.FetchOperator.getRecordReader(FetchOperator.java:419) 
 at org.apache.hadoop.hive.ql.exec.FetchOperator.getNextRow(FetchOperator.java:573) 
 at org.apache.hadoop.hive.ql.exec.FetchOperator.pushRow(FetchOperator.java:546) at org.apache.hadoop.hive.ql.exec.FetchTask.fetch(FetchTask.java:138)
(CliDriver.java:686) at org.apache.hadoop.hive.cli.CliDriver.main(CliDriver.java:625)
```


Let's add a jar to hive using console (e.g. add jar /xxx/hive-customserde.jar), it add resource to hive class path but suppose your custom library has a dependency on other jar then you need to do some work around to resolve class path issue. My custom serde is dependent on Solr libraries and jar file is already added to class path but still it is not getting reflected to class path.  


The simple solution to handle this situation is to add dependent libraries to Hive auxiliary path using below command-

```
hive --auxpath /xxx/solr-solrj-5.2.1.jar, /xxx/httpclient-4.5.1.jar
```

If you still face any class path issue then post your queries in comment :)

