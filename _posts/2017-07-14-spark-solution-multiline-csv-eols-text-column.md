---
layout: post
title: Spark solution for multiline csv which has EOLs in text column
date: 2017-07-14 06:36:08.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Big Data
- java
tags:
- bigdata
- java
- spark
meta:
  _edit_last: '1'
  interface_sidebarlayout: default
  _yoast_wpseo_content_score: '30'
  _yoast_wpseo_primary_category: '6'
  _yoast_wpseo_focuskw_text_input: Spark solution for multiline csv which has EOLs
    in text column
  _yoast_wpseo_focuskw: Spark solution for multiline csv which has EOLs in text column
  _yoast_wpseo_linkdex: '28'
  dsq_thread_id: '5987415303'
  _wp_old_slug: spark-multiline-csv-eols-in-column
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/spark-solution-multiline-csv-eols-text-column/"
---

 **Spark processing multiline csv EOLs in text column**

The multi line support for CSV will be added in spark version 2.2 [JIRA](https://issues.apache.org/jira/browse/SPARK-19610) and for now you can try below steps if you are facing issue while processing CSV:

Get InputFormat and reader classes from [git](https://github.com/benleon/NewLineRemover/blob/master/MultiLine/src/org/apache/ben/FileCleaningInputFormat.java) to your code base and implement use it:  



```java
   import org.apache.hadoop.conf.Configuration;
    import org.apache.hadoop.io.LongWritable;
    import org.apache.hadoop.io.Text;
    import org.apache.spark.api.java.JavaPairRDD;
    import org.apache.spark.api.java.JavaRDD;
    import org.apache.spark.api.java.JavaSparkContext;
    
    JavaPairRDD<longwritable, text=""> rdd = context.newAPIHadoopFile(<CSV file path>, FileCleaningInputFormat.class, null, null, new Configuration());
    JavaRDD inputWithMultiline= rdd.map(s -> s._2().toString())
    
    
 ```

Another solution for this problem is [Apache Crunch CSV reader](https://github.com/apache/crunch/blob/master/crunch-core/src/main/java/org/apache/crunch/io/text/csv/CSVInputFormat.java). This reader can be used like above FileCleaningInputFormat implementation.

