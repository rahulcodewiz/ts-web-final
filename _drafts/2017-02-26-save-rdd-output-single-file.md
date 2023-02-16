---
layout: post
title: how to save Spark RDD output in single file with header using java
date: 2017-02-26 12:22:17.000000000 -08:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Big Data
- java
tags:
- java
- spark
meta:
  _edit_last: '1'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw_text_input: Add header to spark RDD java and create save single
    file
  _yoast_wpseo_focuskw: Add header to spark RDD java and create save single file
  _yoast_wpseo_linkdex: '17'
  _yoast_wpseo_content_score: '60'
  _yoast_wpseo_primary_category: '6'
  _wp_old_slug: add-header-spark-rdd
  dsq_thread_id: '5585127882'
  _thumbnail_id: '627'
  _ez-toc-disabled: ''
  _ez-toc-insert: ''
  _ez-toc-heading-levels: a:0:{}
  _ez-toc-alttext: ''
  _ez-toc-exclude: ''
  wp-syntax-cache-content: "a:1:{i:1;s:4006:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\">        SparkConf
    conf <span style=\"color: #339933;\">=</span> <span style=\"color: #000000; font-weight:
    bold;\">new</span> SparkConf<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span>.<span style=\"color: #006633;\">setAppName</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #0000ff;\">&quot;test&quot;</span><span
    style=\"color: #009900;\">&#41;</span>.<span style=\"color: #006633;\">setMaster</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #0000ff;\">&quot;local[2]&quot;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n
    \       JavaSparkContext jsc <span style=\"color: #339933;\">=</span> <span style=\"color:
    #000000; font-weight: bold;\">new</span> JavaSparkContext<span style=\"color:
    #009900;\">&#40;</span>conf<span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n&nbsp;\n        JavaRDD headerRDD <span style=\"color: #339933;\">=</span>
    jsc.<span style=\"color: #006633;\">parallelize</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #003399;\">Arrays</span>.<span style=\"color: #006633;\">asList</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #000000; font-weight:
    bold;\">new</span> <span style=\"color: #003399;\">String</span><span style=\"color:
    #009900;\">&#91;</span><span style=\"color: #009900;\">&#93;</span><span style=\"color:
    #009900;\">&#123;</span><span style=\"color: #0000ff;\">&quot;name,address,city&quot;</span><span
    style=\"color: #009900;\">&#125;</span><span style=\"color: #009900;\">&#41;</span>,
    <span style=\"color: #cc66cc;\">1</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\n        JavaRDD dataRDD<span style=\"color:
    #339933;\">=</span>....<span style=\"color: #339933;\">;</span>\n&nbsp;\n        <span
    style=\"color: #666666; font-style: italic;\">//Make sure s.toString and header
    are in sync</span>\n        dataRDD<span style=\"color: #339933;\">=</span> dataRDD.<span
    style=\"color: #006633;\">map</span><span style=\"color: #009900;\">&#40;</span>s<span
    style=\"color: #339933;\">-&amp;</span>gt<span style=\"color: #339933;\">;</span>s.<span
    style=\"color: #006633;\">toString</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n        <span style=\"color: #666666; font-style:
    italic;\">//Joined RDD</span>\n       JavaRDD joinedRDD<span style=\"color: #339933;\">=</span>
    headerRDD.<span style=\"color: #006633;\">union</span><span style=\"color: #009900;\">&#40;</span>dataRDD<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n
    \       joinedRDD.<span style=\"color: #006633;\">repartition</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #cc66cc;\">1</span><span style=\"color:
    #009900;\">&#41;</span>.<span style=\"color: #006633;\">saveAsTextFile</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #0000ff;\">&quot;&lt;output&gt;&quot;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n<span
    style=\"color: #339933;\">&lt;/</span>output<span style=\"color: #339933;\">&gt;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">        SparkConf conf = new SparkConf().setAppName(&quot;test&quot;).setMaster(&quot;local[2]&quot;);\n
    \       JavaSparkContext jsc = new JavaSparkContext(conf);\n\n        JavaRDD
    headerRDD = jsc.parallelize(Arrays.asList(new String[]{&quot;name,address,city&quot;}),
    1);\n\n        JavaRDD dataRDD=....;\n\n        //Make sure s.toString and header
    are in sync\n        dataRDD= dataRDD.map(s-&amp;gt;s.toString());\n        //Joined
    RDD\n       JavaRDD joinedRDD= headerRDD.union(dataRDD);\n        \n        joinedRDD.repartition(1).saveAsTextFile(&quot;&lt;output&gt;&quot;);\n\n&lt;/output&gt;</p></div>\n\";}"
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/save-rdd-output-single-file/"
---
 **Below code snippet shows how to save RDD output input single file with header:**

```
SparkConf conf = new SparkConf().setAppName("test").setMaster("local[2]"); JavaSparkContext jsc = new JavaSparkContext(conf); JavaRDD headerRDD = jsc.parallelize(Arrays.asList(new String[]{"name,address,city"}), 1); JavaRDD dataRDD=....; //Make sure s.toString and header are in sync dataRDD= dataRDD.map(s-\>s.toString()); //Joined RDD JavaRDD joinedRDD= headerRDD.union(dataRDD); joinedRDD.repartition(1).saveAsTextFile("<output>");

</output>
```
