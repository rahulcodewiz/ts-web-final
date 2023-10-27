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

Working with Hive in the big data ecosystem often involves dealing with various libraries and dependencies. In this environment, errors like the Hive NoClassDefFoundError are not uncommon. You might have encountered this error when trying to run Hive queries that involve custom libraries and their dependencies. However, there is a simple solution to this issue: the Hive Auxiliary Path. In this post, we'll explore the common `NoClassDefFoundError` problem and guide you on how to use the Hive Auxiliary Path to resolve it.


The NoClassDefFoundError is a Java runtime error that occurs when the Java Virtual Machine (JVM) can't find a particular class at runtime. This error can be frustrating, especially in the context of Hive, where you expect your custom libraries to work seamlessly. The error message might look something like this:

```
Exception in thread "main" java.lang.NoClassDefFoundError: 
org/apache/solr/client/solrj/SolrServerException at 
com.aexp.ims.atworks.hive.solr.SolrSplit.getSplits(SolrSplit.java:84) at com.aexp.ims.atworks.hive.solr.SolrInputFormat.getSplits(SolrInputFormat.java:91)
 at org.apache.hadoop.hive.ql.exec.FetchOperator.getRecordReader(FetchOperator.java:419) 
 at org.apache.hadoop.hive.ql.exec.FetchOperator.getNextRow(FetchOperator.java:573) 
 at org.apache.hadoop.hive.ql.exec.FetchOperator.pushRow(FetchOperator.java:546) at org.apache.hadoop.hive.ql.exec.FetchTask.fetch(FetchTask.java:138)
(CliDriver.java:686) at org.apache.hadoop.hive.cli.CliDriver.main(CliDriver.java:625)
```

To resolve the NoClassDefFoundError in Hive, you can leverage the Hive Auxiliary Path. This feature allows you to specify additional paths where Hive should look for classes and libraries. By adding the necessary dependencies to the auxiliary path, you ensure that Hive can access the required classes at runtime.


Here's how to do it:

- Open your Hive console or terminal.

- Use the following command to add your dependencies to the Hive Auxiliary Path: 

```
hive --auxpath /xxx/solr-solrj-5.2.1.jar, /xxx/httpclient-4.5.1.jar
```
In this command, replace `/path/to/` with the actual paths to your Solr-related JAR files and any other dependencies your custom serde relies on.


Feel free to leave a comment if you have any questions or need further assistance with Hive classpath management!