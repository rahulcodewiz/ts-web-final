---
layout: post
title: Spark Dataset Operations in java
date: 2017-02-23 09:57:12.000000000 -08:00
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
  _yoast_wpseo_content_score: '30'
  _yoast_wpseo_primary_category: '6'
  _yoast_wpseo_focuskw_text_input: Spark Dataset Operations using java, FilterFunction,
    SparkSession
  _yoast_wpseo_focuskw: Spark Dataset Operations using java, FilterFunction, SparkSession
  _yoast_wpseo_linkdex: '45'
  dsq_thread_id: '5576718005'
  _yoast_wpseo_metadesc: Spark Dataset Operations in java, FilterFunction, SparkSession
  wp-syntax-cache-content: "a:3:{i:1;s:10733:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"code\"><pre class=\"xml\" style=\"font-family:monospace;\"><span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;?xml</span>
    <span style=\"color: #000066;\">version</span>=<span style=\"color: #ff0000;\">&quot;1.0&quot;</span>
    <span style=\"color: #000066;\">encoding</span>=<span style=\"color: #ff0000;\">&quot;UTF-8&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">?&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;project</span>
    <span style=\"color: #000066;\">xmlns</span>=<span style=\"color: #ff0000;\">&quot;http://maven.apache.org/POM/4.0.0&quot;</span></span>\n<span
    style=\"color: #009900;\">         <span style=\"color: #000066;\">xmlns:xsi</span>=<span
    style=\"color: #ff0000;\">&quot;http://www.w3.org/2001/XMLSchema-instance&quot;</span></span>\n<span
    style=\"color: #009900;\">         <span style=\"color: #000066;\">xsi:schemaLocation</span>=<span
    style=\"color: #ff0000;\">&quot;http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n    <span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;modelVersion<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>4.0.0<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/modelVersion<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>com.ts.spark<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>api<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>1.0-SNAPSHOT<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n&nbsp;\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;dependencies<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n        <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>org.apache.spark<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n        <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>spark-core_2.11<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n        <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>2.0.0<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n        <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>org.apache.spark<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n        <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>spark-sql_2.11<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n        <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>2.0.0<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n&nbsp;\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/dependencies<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;build<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n        <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;plugins<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n            <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;plugin<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n                <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>org.apache.maven.plugins<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n                <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>maven-compiler-plugin<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n                <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>3.5.1<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n                <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;configuration<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n                    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;source<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>1.8<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/source<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n                    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;target<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>1.8<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/target<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n                <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/configuration<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n            <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/plugin<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n        <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/plugins<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/build<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/project<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">&lt;?xml version=&quot;1.0&quot; encoding=&quot;UTF-8&quot;?&gt;\r\n&lt;project
    xmlns=&quot;http://maven.apache.org/POM/4.0.0&quot;\r\n         xmlns:xsi=&quot;http://www.w3.org/2001/XMLSchema-instance&quot;\r\n
    \        xsi:schemaLocation=&quot;http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd&quot;&gt;\r\n
    \   &lt;modelVersion&gt;4.0.0&lt;/modelVersion&gt;\r\n    &lt;groupId&gt;com.ts.spark&lt;/groupId&gt;\r\n
    \   &lt;artifactId&gt;api&lt;/artifactId&gt;\r\n    &lt;version&gt;1.0-SNAPSHOT&lt;/version&gt;\r\n\r\n&lt;dependencies&gt;\r\n
    \   &lt;dependency&gt;\r\n        &lt;groupId&gt;org.apache.spark&lt;/groupId&gt;\r\n
    \       &lt;artifactId&gt;spark-core_2.11&lt;/artifactId&gt;\r\n        &lt;version&gt;2.0.0&lt;/version&gt;\r\n
    \   &lt;/dependency&gt;\r\n    &lt;dependency&gt;\r\n        &lt;groupId&gt;org.apache.spark&lt;/groupId&gt;\r\n
    \       &lt;artifactId&gt;spark-sql_2.11&lt;/artifactId&gt;\r\n        &lt;version&gt;2.0.0&lt;/version&gt;\r\n
    \   &lt;/dependency&gt;\r\n\r\n&lt;/dependencies&gt;\r\n    &lt;build&gt;\r\n
    \       &lt;plugins&gt;\r\n            &lt;plugin&gt;\r\n                &lt;groupId&gt;org.apache.maven.plugins&lt;/groupId&gt;\r\n
    \               &lt;artifactId&gt;maven-compiler-plugin&lt;/artifactId&gt;\r\n
    \               &lt;version&gt;3.5.1&lt;/version&gt;\r\n                &lt;configuration&gt;\r\n
    \                   &lt;source&gt;1.8&lt;/source&gt;\r\n                    &lt;target&gt;1.8&lt;/target&gt;\r\n
    \               &lt;/configuration&gt;\r\n            &lt;/plugin&gt;\r\n        &lt;/plugins&gt;\r\n
    \   &lt;/build&gt;\r\n&lt;/project&gt;</p></div>\n\";i:2;s:4083:\"\n<div class=\"wp_syntax\"
    style=\"position:relative;\"><table><tr><td class=\"code\"><pre class=\"java\"
    style=\"font-family:monospace;\"><span style=\"color: #000000; font-weight: bold;\">public</span>
    <span style=\"color: #000000; font-weight: bold;\">class</span> People <span style=\"color:
    #000000; font-weight: bold;\">implements</span> <span style=\"color: #003399;\">Serializable</span>
    <span style=\"color: #009900;\">&#123;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">private</span> <span style=\"color: #003399;\">String</span> name<span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">private</span> <span style=\"color: #003399;\">Long</span> age<span style=\"color:
    #339933;\">;</span>\n&nbsp;\n<span style=\"color: #000000; font-weight: bold;\">public</span>
    People<span style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#123;</span>\n&nbsp;\n<span style=\"color: #009900;\">&#125;</span>\n&nbsp;\n<span
    style=\"color: #000000; font-weight: bold;\">public</span> People<span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #003399;\">String</span> name, <span
    style=\"color: #003399;\">Long</span> age<span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#123;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">this</span>.<span style=\"color: #006633;\">name</span> <span style=\"color:
    #339933;\">=</span> name<span style=\"color: #339933;\">;</span>\n<span style=\"color:
    #000000; font-weight: bold;\">this</span>.<span style=\"color: #006633;\">age</span>
    <span style=\"color: #339933;\">=</span> age<span style=\"color: #339933;\">;</span>\n<span
    style=\"color: #009900;\">&#125;</span>\n&nbsp;\n<span style=\"color: #000000;
    font-weight: bold;\">public</span> <span style=\"color: #003399;\">String</span>
    getName<span style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#123;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">return</span> name<span style=\"color: #339933;\">;</span>\n<span style=\"color:
    #009900;\">&#125;</span>\n&nbsp;\n<span style=\"color: #000000; font-weight: bold;\">public</span>
    <span style=\"color: #000066; font-weight: bold;\">void</span> setName<span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #003399;\">String</span> name<span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n<span
    style=\"color: #000000; font-weight: bold;\">this</span>.<span style=\"color:
    #006633;\">name</span> <span style=\"color: #339933;\">=</span> name<span style=\"color:
    #339933;\">;</span>\n<span style=\"color: #009900;\">&#125;</span>\n&nbsp;\n<span
    style=\"color: #000000; font-weight: bold;\">public</span> <span style=\"color:
    #003399;\">Long</span> getAge<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n<span
    style=\"color: #000000; font-weight: bold;\">return</span> age<span style=\"color:
    #339933;\">;</span>\n<span style=\"color: #009900;\">&#125;</span>\n&nbsp;\n<span
    style=\"color: #000000; font-weight: bold;\">public</span> <span style=\"color:
    #000066; font-weight: bold;\">void</span> setAge<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #003399;\">Long</span> age<span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#123;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">this</span>.<span style=\"color: #006633;\">age</span> <span style=\"color:
    #339933;\">=</span> age<span style=\"color: #339933;\">;</span>\n<span style=\"color:
    #009900;\">&#125;</span>\n<span style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">public class People implements Serializable
    {\r\nprivate String name;\r\nprivate Long age;\r\n\r\npublic People() {\r\n\r\n}\r\n\r\npublic
    People(String name, Long age) {\r\nthis.name = name;\r\nthis.age = age;\r\n}\r\n\r\npublic
    String getName() {\r\nreturn name;\r\n}\r\n\r\npublic void setName(String name)
    {\r\nthis.name = name;\r\n}\r\n\r\npublic Long getAge() {\r\nreturn age;\r\n}\r\n\r\npublic
    void setAge(Long age) {\r\nthis.age = age;\r\n}\r\n}</p></div>\n\";i:3;s:4748:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"code\"><pre
    class=\"java\" style=\"font-family:monospace;\"><span style=\"color: #000000;
    font-weight: bold;\">public</span> <span style=\"color: #000000; font-weight:
    bold;\">class</span> Application <span style=\"color: #009900;\">&#123;</span>\n
    \   <span style=\"color: #000000; font-weight: bold;\">public</span> <span style=\"color:
    #000000; font-weight: bold;\">static</span> <span style=\"color: #000066; font-weight:
    bold;\">void</span> main<span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #003399;\">String</span><span style=\"color: #009900;\">&#91;</span><span style=\"color:
    #009900;\">&#93;</span> args<span style=\"color: #009900;\">&#41;</span> <span
    style=\"color: #009900;\">&#123;</span>\n       SparkSession session<span style=\"color:
    #339933;\">=</span>SparkSession.<span style=\"color: #006633;\">builder</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">appName</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;dataset example&quot;</span><span style=\"color:
    #009900;\">&#41;</span>.<span style=\"color: #006633;\">getOrCreate</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n        <span style=\"color: #008000; font-style:
    italic; font-weight: bold;\">/**\n         * Define encoder, used to convert data
    to binary format in jvm\n         */</span>\n        Encoder encode<span style=\"color:
    #339933;\">=</span> Encoders.<span style=\"color: #006633;\">bean</span><span
    style=\"color: #009900;\">&#40;</span>People.<span style=\"color: #000000; font-weight:
    bold;\">class</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n&nbsp;\n        <span style=\"color: #008000; font-style:
    italic; font-weight: bold;\">/**\n         * Load dataset from json\n         */</span>\n
    \       Dataset ds<span style=\"color: #339933;\">=</span> session.<span style=\"color:
    #006633;\">read</span><span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #009900;\">&#41;</span>.<span style=\"color: #006633;\">json</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #003399;\">Thread</span>.<span style=\"color:
    #006633;\">currentThread</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span>.\n<span style=\"color: #006633;\">getContextClassLoader</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">getResource</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;people.json&quot;</span><span style=\"color: #009900;\">&#41;</span>.\n<span
    style=\"color: #006633;\">getPath</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">as</span><span style=\"color: #009900;\">&#40;</span>encode<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n
    \       ds.<span style=\"color: #006633;\">filter</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#40;</span>FilterFunction<span style=\"color: #339933;\">&lt;</span>People<span
    style=\"color: #339933;\">&gt;</span><span style=\"color: #009900;\">&#41;</span>s<span
    style=\"color: #339933;\">-&gt;</span> <span style=\"color: #009900;\">&#40;</span>s.<span
    style=\"color: #006633;\">getAge</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">&gt;</span><span
    style=\"color: #cc66cc;\">30</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span>.<span style=\"color: #006633;\">show</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\n&nbsp;\n&nbsp;\n    <span style=\"color:
    #009900;\">&#125;</span>\n<span style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">public class Application {\r\n    public
    static void main(String[] args) {\r\n       SparkSession session=SparkSession.builder().appName(&quot;dataset
    example&quot;).getOrCreate();\r\n        /**\r\n         * Define encoder, used
    to convert data to binary format in jvm\r\n         */\r\n        Encoder encode=
    Encoders.bean(People.class);\r\n\r\n        /**\r\n         * Load dataset from
    json\r\n         */\r\n        Dataset ds= session.read().json(Thread.currentThread().\r\ngetContextClassLoader().getResource(&quot;people.json&quot;).\r\ngetPath()).as(encode);\r\n\r\n
    \       ds.filter((FilterFunction&lt;People&gt;)s-&gt; (s.getAge()&gt;30)).show();\r\n\r\n\r\n\r\n
    \   }\r\n}</p></div>\n\";}"
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/spark-dataset-operations-java/"
---
I am gonna demonstrate step by step setup of spark project in this post and explore few basics Spark dataset operations in Java.

Create Maven project with POM:

```
<?xml version="1.0" encoding="UTF-8"?><project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemalocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelversion>4.0.0</modelversion>
    <groupid>com.ts.spark</groupid>
    <artifactid>api</artifactid>
    <version>1.0-SNAPSHOT</version>

<dependencies>
    <dependency>
        <groupid>org.apache.spark</groupid>
        <artifactid>spark-core_2.11</artifactid>
        <version>2.0.0</version>
    </dependency>
    <dependency>
        <groupid>org.apache.spark</groupid>
        <artifactid>spark-sql_2.11</artifactid>
        <version>2.0.0</version>
    </dependency>

</dependencies>
    <build>
        <plugins>
            <plugin>
                <groupid>org.apache.maven.plugins</groupid>
                <artifactid>maven-compiler-plugin</artifactid>
                <version>3.5.1</version>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
```

Project structure:

[![]({{ site.baseurl }}/assets/images/Screen-Shot-2017-02-22-at-9.25.53-PM-150x150.png)](http://www.techsquids.com/wp-content/uploads/2017/02/Screen-Shot-2017-02-22-at-9.25.53-PM.png)

Create Bean definition:

```
public class People implements Serializable { private String name; private Long age; public People() { } public People(String name, Long age) { this.name = name; this.age = age; } public String getName() { return name; } public void setName(String name) { this.name = name; } public Long getAge() { return age; } public void setAge(Long age) { this.age = age; } }
```

Create people.json file in resource directory:  
{"name":"PhilipHester","age":88}  
{"name":"DylanBecker","age":64}  
{"name":"JohnCarpenter","age":60}  
{"name":"DeclanBarton","age":64}  
{"name":"KennedySutton","age":91}  
{"name":"DolanRowland","age":96}  
{"name":"JonahWhitaker","age":41}

Filter content of dataset:

```
public class Application { public static void main(String[] args) { SparkSession session=SparkSession.builder().appName("dataset example").getOrCreate(); /\*\* \* Define encoder, used to convert data to binary format in jvm \*/ Encoder encode= Encoders.bean(People.class); /\*\* \* Load dataset from json \*/ Dataset ds= session.read().json(Thread.currentThread(). getContextClassLoader().getResource("people.json"). getPath()).as(encode); ds.filter((FilterFunction<people>)s-&gt; (s.getAge()&gt;30)).show();



    }
}

</people>
```
