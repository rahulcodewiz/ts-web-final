---
layout: post
title: Lanuch Hbase Mapreduce Job
date: 2015-01-11 03:09:37.000000000 -08:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Big Data
- hbase
- java
tags:
- hadoop
- hbase
- java
meta:
  _edit_last: '1'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: Lanuch Hbase Mapreduce Job
  _yoast_wpseo_title: Lanuch Hbase Mapreduce Job
  _yoast_wpseo_metadesc: Lanuch Hbase Mapreduce Job
  _yoast_wpseo_linkdex: '63'
  dsq_thread_id: '4406334215'
  wp-syntax-cache-content: "a:5:{i:1;s:645:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n</pre></td><td class=\"code\"><pre
    class=\"script\" style=\"font-family:monospace;\">jar=/home/hadoop/Desktop/techsquids/repos/techsquids/map-reduce/target/map-reduce-1.0-SNAPSHOT.jar\r\nclasspath=$jar\r\nfor
    f in $HBASE_HOME/lib/*.jar;do\r\nclasspath=&quot;${classpath},$f&quot;\r\ndone</pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">jar=/home/hadoop/Desktop/techsquids/repos/techsquids/map-reduce/target/map-reduce-1.0-SNAPSHOT.jar\r\nclasspath=$jar\r\nfor
    f in $HBASE_HOME/lib/*.jar;do\r\nclasspath=&quot;${classpath},$f&quot;\r\ndone</p></div>\n\";i:2;s:325:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n</pre></td><td
    class=\"code\"><pre class=\"script\" style=\"font-family:monospace;\">path=`echo
    $classpath | sed 's/,/:/g'`</pre></td></tr></table><p class=\"theCode\" style=\"display:none;\">path=`echo
    $classpath | sed 's/,/:/g'`</p></div>\n\";i:3;s:401:\"\n<div class=\"wp_syntax\"
    style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n</pre></td><td
    class=\"code\"><pre class=\"script\" style=\"font-family:monospace;\">export LIBJARS=`hadoop
    classpath`:$classpath\r\nexport HADOOP_CLASSPATH=$path</pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">export LIBJARS=`hadoop classpath`:$classpath\r\nexport
    HADOOP_CLASSPATH=$path</p></div>\n\";i:4;s:429:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"line_numbers\"><pre>1\n</pre></td><td class=\"code\"><pre class=\"script\"
    style=\"font-family:monospace;\">hadoop jar $jar com.ts.mapreduce.hbase.ColumnsCounter
    -libjars ${classpath} &quot;$@&quot;</pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">hadoop jar $jar com.ts.mapreduce.hbase.ColumnsCounter
    -libjars ${classpath} &quot;$@&quot;</p></div>\n\";i:5;s:1913:\"\n<div class=\"wp_syntax\"
    style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n3\n4\n</pre></td><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\">HBaseConfiguration.<span
    style=\"color: #006633;\">addHbaseResources</span><span style=\"color: #009900;\">&#40;</span>job.<span
    style=\"color: #006633;\">getConfiguration</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\nTableMapReduceUtil.<span style=\"color: #006633;\">addDependencyJars</span><span
    style=\"color: #009900;\">&#40;</span>job<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\nTableMapReduceUtil.<span style=\"color: #006633;\">addDependencyJars</span><span
    style=\"color: #009900;\">&#40;</span>job.<span style=\"color: #006633;\">getConfiguration</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>,
    org.<span style=\"color: #006633;\">apache</span>.<span style=\"color: #006633;\">hadoop</span>.<span
    style=\"color: #006633;\">hbase</span>.<span style=\"color: #006633;\">client</span>.<span
    style=\"color: #006633;\">Put</span>.<span style=\"color: #000000; font-weight:
    bold;\">class</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\njob.<span style=\"color: #006633;\">setJarByClass</span><span
    style=\"color: #009900;\">&#40;</span>ColumnsCounter.<span style=\"color: #000000;
    font-weight: bold;\">class</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span></pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">HBaseConfiguration.addHbaseResources(job.getConfiguration());\r\nTableMapReduceUtil.addDependencyJars(job);\r\nTableMapReduceUtil.addDependencyJars(job.getConfiguration(),
    org.apache.hadoop.hbase.client.Put.class);\r\njob.setJarByClass(ColumnsCounter.class);</p></div>\n\";}"
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/lanuch-hbase-mapreduce-job/"
---
Lanuch Hbase Mapreduce Job  
Add all the required jars to a variable separated by(,)  
like jar=a,b  
in my case I want to supply all hbase jars to job

```
jar=/home/hadoop/Desktop/techsquids/repos/techsquids/map-reduce/target/map-reduce-1.0-SNAPSHOT.jar classpath=$jar for f in $HBASE\_HOME/lib/\*.jar;do classpath="${classpath},$f" done
```

Next prepare the Hadoop classpath from previously formed jar files and jars separated by colon(:).

```
path=`echo $classpath | sed 's/,/:/g'`
```

Export LIBJARS & HADOOP\_CLASSPATH\

```
export LIBJARS=`hadoop classpath`:$classpath export HADOOP\_CLASSPATH=$path
```

Run Hadoop job

```
hadoop jar $jar com.ts.mapreduce.hbase.ColumnsCounter -libjars ${classpath} "$@"
```

if you get ClassNotFountException in java then register your jars

```
HBaseConfiguration.addHbaseResources(job.getConfiguration()); TableMapReduceUtil.addDependencyJars(job); TableMapReduceUtil.addDependencyJars(job.getConfiguration(), org.apache.hadoop.hbase.client.Put.class); job.setJarByClass(ColumnsCounter.class);
```

Complete source at git([techsquids](https://github.com/rahul86s/techsquids/blob/master/hbase/runjob.sh "runjob.sh"))

