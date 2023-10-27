---
layout: post
title: hive hadoop jar files conflicts for custom UDF/Serde
date: 2015-12-22 23:55:45.000000000 -08:00
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
  _yoast_wpseo_focuskw: hive hadoop jar files conflicts for custom UDF/Serde
  _yoast_wpseo_title: hive hadoop jar files conflicts for custom UDF/Serde
  _yoast_wpseo_metadesc: hive hadoop jar files conflicts for custom UDF/Serde.I have
    faced this problem very often and it take long time figure to resolve libraries
    conflicts.
  _yoast_wpseo_linkdex: '62'
  dsq_thread_id: '4425931813'
  _yoast_wpseo_focuskw_text_input: hive hadoop jar files conflicts for custom UDF/Serde
  _yoast_wpseo_content_score: '30'
  _yoast_wpseo_primary_category: ''
  wp-syntax-cache-content: "a:4:{i:1;s:720:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"line_numbers\"><pre>1\n</pre></td><td class=\"code\"><pre class=\"java\"
    style=\"font-family:monospace;\"> export HADOOP_CLASSPATH<span style=\"color:
    #339933;\">=/</span>xxx<span style=\"color: #339933;\">/</span>noggit<span style=\"color:
    #339933;\">-</span><span style=\"color: #cc66cc;\">0.6</span>.<span style=\"color:
    #006633;\">jar</span><span style=\"color: #339933;\">:/</span>xxx<span style=\"color:
    #339933;\">/</span>httpclient<span style=\"color: #339933;\">-</span>4.5.1.<span
    style=\"color: #006633;\">jar</span></pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\"> export HADOOP_CLASSPATH=/xxx/noggit-0.6.jar:/xxx/httpclient-4.5.1.jar</p></div>\n\";i:2;s:513:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n</pre></td><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\">HADOOP_TASKTRACKER_OPTS<span
    style=\"color: #339933;\">=</span><span style=\"color: #0000ff;\">&quot;-classpath&amp;lt;colon-separated-paths-to-your-jars&amp;gt;&quot;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">HADOOP_TASKTRACKER_OPTS=&quot;-classpath&amp;lt;colon-separated-paths-to-your-jars&amp;gt;&quot;</p></div>\n\";i:3;s:1026:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n</pre></td><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\">         Job
    job <span style=\"color: #339933;\">=</span> <span style=\"color: #000000; font-weight:
    bold;\">new</span> Job<span style=\"color: #009900;\">&#40;</span>conf<span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n        job.<span
    style=\"color: #006633;\">setJarByClass</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #339933;\">&lt;</span>any <span style=\"color: #000000; font-weight:
    bold;\">class</span> from third party jar file<span style=\"color: #339933;\">&gt;</span>.<span
    style=\"color: #000000; font-weight: bold;\">class</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">         Job job = new Job(conf);\r\n
    \       job.setJarByClass(&lt;any class from third party jar file&gt;.class);</p></div>\n\";i:4;s:376:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"code\"><pre
    class=\"unix\" style=\"font-family:monospace;\">set mapreduce.task.classpath.first=true;\r\nset
    mapreduce.job.user.classpath.first=true;</pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">set mapreduce.task.classpath.first=true;\r\nset mapreduce.job.user.classpath.first=true;</p></div>\n\";}"
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/hive-hadoop-jar-files-conflicts/"
---
 ## Hive hadoop jar files conflicts for custom UDF and Serde

Are you struggling with JAR file conflicts in your Hive and Hadoop environment when working with custom User-Defined Functions (UDFs) and Serdes? You're not alone! In this blog post, we'll explore the common issues that arise due to library conflicts and discuss how to effectively resolve them.

The primary reason behind these issues is that the default MapReduce libraries often take precedence when you launch a MapReduce job or Hive query. However, your custom UDFs and Serdes may require the latest versions of JAR files that are already present in the Hadoop classpath. As a result, even if you add your JARs to Hive's classpath or auxiliary classpath, these conflicts can still persist.

To tackle these conflicts, you need to instruct the MapReduce engine or Hive to prioritize your user-provided JARs over the default libraries. Here's how you can do that:

- Add your JAR files to the Hadoop classpath using the `HADOOP_CLASSPATH` environment variable. For example:
```
export HADOOP\_CLASSPATH=/xxx/noggit-0.6.jar:/xxx/httpclient-4.5.1.jar
```

- Update the HADOOP_TASKTRACKER_OPTS environment variable to include your JARs in the classpath. This can be achieved as follows:

```
HADOOP_TASKTRACKER_OPTS="-classpath<colon-separated-paths-to-your-jars>"
```

- Now you need to set JARs in MapReduce Job Builder. Here's an example:

```
Job job = new Job(conf);
job.setJarByClass(<any class from the third-party JAR file>.class);

```

### Prioritizing User Classpath

To ensure that your custom JARs are used first, set the following MapReduce properties:

```
set mapreduce.task.classpath.first=true; set mapreduce.job.user.classpath.first=true;
```


In conclusion, with these steps you can easily resolve JAR file conflicts and ensure that your custom UDFs and Serdes work seamlessly in your Hive and Hadoop environment and focus on your data processing tasks.