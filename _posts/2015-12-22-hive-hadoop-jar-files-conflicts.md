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

I have faced this problem very often and it takes long time figureout how to resolve libraries conflicts.  
This happens because default Mapreduce libraries gets preferences when you launch Mapreduce job or hive and suppose your custom library required the latest version of jars which is already present in Hadoop class path. This error won't get resolve even when you add your jars hive classpath or auxiliary class path this issue still occur. You need to tell Mapreduce engine or hive to use user provided jars first in the classpath.

E.g.  

- Let's add jar to Hadoop class path-
```
export HADOOP\_CLASSPATH=/xxx/noggit-0.6.jar:/xxx/httpclient-4.5.1.jar
```

- Add your libraries to HADOOP_TASKTRACKER_OPTS
```
HADOOP_TASKTRACKER_OPTS="-classpath<colon-separated-paths-to-your-jars>"
```

You can also add jars to map reduce class path by adding class to mapreduce job builder-

```
Job job = new Job(conf); job.setJarByClass(<any class from third party jar file>.class);
</any>
```
### This is the way to use user classpath first-
```
set mapreduce.task.classpath.first=true; set mapreduce.job.user.classpath.first=true;
```
