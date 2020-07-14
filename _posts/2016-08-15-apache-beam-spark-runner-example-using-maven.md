---
layout: post
title: Apache Beam Spark Runner example using Maven
date: 2016-08-15 11:39:47.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Big Data
tags:
- apache Beam
- hadoop
- java
- spark
meta:
  _edit_last: '1'
  interface_sidebarlayout: default
  _yoast_wpseo_content_score: '30'
  _yoast_wpseo_primary_category: '6'
  _yoast_wpseo_focuskw_text_input: Apache Beam Spark Runner example using Maven eclipse
  _yoast_wpseo_focuskw: Apache Beam Spark Runner example using Maven eclipse
  _yoast_wpseo_title: Apache Beam Spark Runner example using Maven
  _yoast_wpseo_linkdex: '67'
  _yoast_wpseo_metadesc: Steps by step guide to create Apache Beam Spark Runner example
    using Maven eclipse.
  dsq_thread_id: '5066596040'
  wp-syntax-cache-content: "a:9:{i:1;s:1434:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"code\"><pre class=\"xml\" style=\"font-family:monospace;\"><span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;repository<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n      <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;id<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>cloudera<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/id<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n      <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;url<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>https://repository.cloudera.com/artifactory/cloudera-repos/<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/url<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/repository<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">&lt;repository&gt;\r\n      &lt;id&gt;cloudera&lt;/id&gt;\r\n
    \     &lt;url&gt;https://repository.cloudera.com/artifactory/cloudera-repos/&lt;/url&gt;\r\n
    \   &lt;/repository&gt;</p></div>\n\";i:2;s:6939:\"\n<div class=\"wp_syntax\"
    style=\"position:relative;\"><table><tr><td class=\"code\"><pre class=\"xml\"
    style=\"font-family:monospace;\"><span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;settings<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span><span style=\"color: #000000; font-weight: bold;\">&lt;/settings<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span><span style=\"color:
    #000000; font-weight: bold;\">&lt;profiles<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span><span style=\"color: #000000; font-weight: bold;\">&lt;profile<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n      <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;id<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>cld<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/id<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n&nbsp;\n
    \     <span style=\"color: #009900;\"><span style=\"color: #000000; font-weight:
    bold;\">&lt;repositories<span style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n
    \      <span style=\"color: #009900;\"><span style=\"color: #000000; font-weight:
    bold;\">&lt;repository<span style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n
    \     <span style=\"color: #009900;\"><span style=\"color: #000000; font-weight:
    bold;\">&lt;id<span style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>cloudera<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/id<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n      <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;url<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>https://repository.cloudera.com/artifactory/cloudera-repos/<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/url<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/repository<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n     <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;repository<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n      <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;id<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>mvn<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/id<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n      <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;url<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>http://repo1.maven.org/maven2/<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/url<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;release<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n    \t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;enabled<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>true<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/enabled<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/release<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;snapshots<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n    \t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;enabled<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>true<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/enabled<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/snapshots<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/repository<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n      <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/repositories<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n&nbsp;\n
    \   <span style=\"color: #009900;\"><span style=\"color: #000000; font-weight:
    bold;\">&lt;/profile<span style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>
    <span style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/profiles<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span> <span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;activeProfiles<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;activeProfile<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>cld<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/activeProfile<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n  <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/activeProfiles<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n&nbsp;\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/settings<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">&lt;settings&gt;&lt;/settings&gt;&lt;profiles&gt;&lt;profile&gt;\r\n
    \     &lt;id&gt;cld&lt;/id&gt;\r\n\r\n      &lt;repositories&gt;\r\n       &lt;repository&gt;\r\n
    \     &lt;id&gt;cloudera&lt;/id&gt;\r\n      &lt;url&gt;https://repository.cloudera.com/artifactory/cloudera-repos/&lt;/url&gt;\r\n
    \   &lt;/repository&gt;\r\n     &lt;repository&gt;\r\n      &lt;id&gt;mvn&lt;/id&gt;\r\n
    \     &lt;url&gt;http://repo1.maven.org/maven2/&lt;/url&gt;\r\n    &lt;release&gt;\r\n
    \   \t&lt;enabled&gt;true&lt;/enabled&gt;\r\n    &lt;/release&gt;\r\n    &lt;snapshots&gt;\r\n
    \   \t&lt;enabled&gt;true&lt;/enabled&gt;\r\n    &lt;/snapshots&gt;\r\n    &lt;/repository&gt;\r\n
    \     &lt;/repositories&gt;\r\n      \r\n    &lt;/profile&gt; &lt;/profiles&gt;
    &lt;activeProfiles&gt;\r\n    &lt;activeProfile&gt;cld&lt;/activeProfile&gt;\r\n
    \ &lt;/activeProfiles&gt;\r\n\r\n&lt;/settings&gt;</p></div>\n\";i:3;s:898:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"code\"><pre
    class=\"java\" style=\"font-family:monospace;\">mvn archetype<span style=\"color:
    #339933;\">:</span>generate <span style=\"color: #339933;\">-</span>DgroupId<span
    style=\"color: #339933;\">=</span>com.<span style=\"color: #006633;\">ts</span>.<span
    style=\"color: #006633;\">spark</span>\n   <span style=\"color: #339933;\">-</span>DartifactId<span
    style=\"color: #339933;\">=</span>beam<span style=\"color: #339933;\">-</span>spark\n
    \  <span style=\"color: #339933;\">-</span>DarchetypeArtifactId<span style=\"color:
    #339933;\">=</span>maven<span style=\"color: #339933;\">-</span>archetype<span
    style=\"color: #339933;\">-</span>quickstart</pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">mvn archetype:generate -DgroupId=com.ts.spark\r\n   -DartifactId=beam-spark\r\n
    \  -DarchetypeArtifactId=maven-archetype-quickstart</p></div>\n\";i:4;s:25065:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"code\"><pre
    class=\"xml\" style=\"font-family:monospace;\"><span style=\"color: #009900;\"><span
    style=\"color: #000000; font-weight: bold;\">&lt;project</span> <span style=\"color:
    #000066;\">xmlns</span>=<span style=\"color: #ff0000;\">&quot;http://maven.apache.org/POM/4.0.0&quot;</span>
    <span style=\"color: #000066;\">xmlns:xsi</span>=<span style=\"color: #ff0000;\">&quot;http://www.w3.org/2001/XMLSchema-instance&quot;</span></span>\n<span
    style=\"color: #009900;\">\t<span style=\"color: #000066;\">xsi:schemaLocation</span>=<span
    style=\"color: #ff0000;\">&quot;http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n\t<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;modelVersion<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>4.0.0<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/modelVersion<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n&nbsp;\n\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>com.ts.spark<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>beam-spark<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>0.0.1-SNAPSHOT<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;packaging<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>jar<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/packaging<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n&nbsp;\n\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;name<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>beam-spark<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/name<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;url<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>http://maven.apache.org<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/url<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n&nbsp;\n\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;properties<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n        <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;project.build.sourceEncoding<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>UTF-8<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/project.build.sourceEncoding<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n        <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;project.reporting.outputEncoding<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>UTF-8<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/project.reporting.outputEncoding<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n        <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;java.version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>1.7<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/java.version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n        <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;spark.version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>1.5.2<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/spark.version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n        <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;google-cloud-dataflow-version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>1.3.0<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/google-cloud-dataflow-version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/properties<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n&nbsp;\n\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;dependencies<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>org.testng<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>testng<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>6.8<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;scope<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>test<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/scope<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>com.cloudera.dataflow.spark<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>spark-dataflow<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>0.4.2<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n            <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>org.apache.spark<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n            <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>spark-core_2.10<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n            <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>${spark.version}<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n        <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n        <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n            <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>org.apache.spark<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n            <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>spark-streaming_2.10<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n            <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>${spark.version}<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n            <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;scope<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>provided<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/scope<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n        <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n        <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n            <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>com.google.cloud.dataflow<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n            <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>google-cloud-dataflow-java-sdk-all<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n            <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>${google-cloud-dataflow-version}<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n            <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;exclusions<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n                <span
    style=\"color: #808080; font-style: italic;\">&lt;!-- Use Hadoop/Spark's backend
    logger --&gt;</span>\n                <span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;exclusion<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n                    <span style=\"color: #009900;\"><span
    style=\"color: #000000; font-weight: bold;\">&lt;groupId<span style=\"color: #000000;
    font-weight: bold;\">&gt;</span></span></span>org.slf4j<span style=\"color: #009900;\"><span
    style=\"color: #000000; font-weight: bold;\">&lt;/groupId<span style=\"color:
    #000000; font-weight: bold;\">&gt;</span></span></span>\n                    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>slf4j-jdk14<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n                <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/exclusion<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n            <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/exclusions<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n        <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n        <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n            <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>com.google.cloud.dataflow<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n            <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>google-cloud-dataflow-java-examples-all<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n            <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>${google-cloud-dataflow-version}<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n            <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;exclusions<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n                <span
    style=\"color: #808080; font-style: italic;\">&lt;!-- Use Hadoop/Spark's backend
    logger --&gt;</span>\n                <span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;exclusion<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n                    <span style=\"color: #009900;\"><span
    style=\"color: #000000; font-weight: bold;\">&lt;groupId<span style=\"color: #000000;
    font-weight: bold;\">&gt;</span></span></span>org.slf4j<span style=\"color: #009900;\"><span
    style=\"color: #000000; font-weight: bold;\">&lt;/groupId<span style=\"color:
    #000000; font-weight: bold;\">&gt;</span></span></span>\n                    <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>slf4j-jdk14<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n                <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/exclusion<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n            <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/exclusions<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n        <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n       \t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/dependencies<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n&nbsp;\n
    \   <span style=\"color: #009900;\"><span style=\"color: #000000; font-weight:
    bold;\">&lt;build<span style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n
    \       <span style=\"color: #009900;\"><span style=\"color: #000000; font-weight:
    bold;\">&lt;plugins<span style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n
    \           <span style=\"color: #009900;\"><span style=\"color: #000000; font-weight:
    bold;\">&lt;plugin<span style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n
    \               <span style=\"color: #009900;\"><span style=\"color: #000000;
    font-weight: bold;\">&lt;groupId<span style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>org.apache.maven.plugins<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n                <span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>maven-compiler-plugin<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/artifactId<span
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
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n&nbsp;\n
    \       <span style=\"color: #009900;\"><span style=\"color: #000000; font-weight:
    bold;\">&lt;/plugins<span style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n&nbsp;\n
    \   <span style=\"color: #009900;\"><span style=\"color: #000000; font-weight:
    bold;\">&lt;/build<span style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/project<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">&lt;project xmlns=&quot;http://maven.apache.org/POM/4.0.0&quot;
    xmlns:xsi=&quot;http://www.w3.org/2001/XMLSchema-instance&quot;\r\n\txsi:schemaLocation=&quot;http://maven.apache.org/POM/4.0.0
    http://maven.apache.org/xsd/maven-4.0.0.xsd&quot;&gt;\r\n\t&lt;modelVersion&gt;4.0.0&lt;/modelVersion&gt;\r\n\r\n\t&lt;groupId&gt;com.ts.spark&lt;/groupId&gt;\r\n\t&lt;artifactId&gt;beam-spark&lt;/artifactId&gt;\r\n\t&lt;version&gt;0.0.1-SNAPSHOT&lt;/version&gt;\r\n\t&lt;packaging&gt;jar&lt;/packaging&gt;\r\n\r\n\t&lt;name&gt;beam-spark&lt;/name&gt;\r\n\t&lt;url&gt;http://maven.apache.org&lt;/url&gt;\r\n\r\n\t&lt;properties&gt;\r\n
    \       &lt;project.build.sourceEncoding&gt;UTF-8&lt;/project.build.sourceEncoding&gt;\r\n
    \       &lt;project.reporting.outputEncoding&gt;UTF-8&lt;/project.reporting.outputEncoding&gt;\r\n
    \       &lt;java.version&gt;1.7&lt;/java.version&gt;\r\n        &lt;spark.version&gt;1.5.2&lt;/spark.version&gt;\r\n
    \       &lt;google-cloud-dataflow-version&gt;1.3.0&lt;/google-cloud-dataflow-version&gt;\r\n
    \   &lt;/properties&gt;\r\n\r\n\t&lt;dependencies&gt;\r\n\t\t&lt;dependency&gt;\r\n\t\t\t&lt;groupId&gt;org.testng&lt;/groupId&gt;\r\n\t\t\t&lt;artifactId&gt;testng&lt;/artifactId&gt;\r\n\t\t\t&lt;version&gt;6.8&lt;/version&gt;\r\n\t\t\t&lt;scope&gt;test&lt;/scope&gt;\r\n\t\t&lt;/dependency&gt;\r\n\t\t&lt;dependency&gt;\r\n\t\t\t&lt;groupId&gt;com.cloudera.dataflow.spark&lt;/groupId&gt;\r\n\t\t\t&lt;artifactId&gt;spark-dataflow&lt;/artifactId&gt;\r\n\t\t\t&lt;version&gt;0.4.2&lt;/version&gt;\r\n\t\t&lt;/dependency&gt;\r\n\t\t&lt;dependency&gt;\r\n
    \           &lt;groupId&gt;org.apache.spark&lt;/groupId&gt;\r\n            &lt;artifactId&gt;spark-core_2.10&lt;/artifactId&gt;\r\n
    \           &lt;version&gt;${spark.version}&lt;/version&gt;\r\n        &lt;/dependency&gt;\r\n
    \       &lt;dependency&gt;\r\n            &lt;groupId&gt;org.apache.spark&lt;/groupId&gt;\r\n
    \           &lt;artifactId&gt;spark-streaming_2.10&lt;/artifactId&gt;\r\n            &lt;version&gt;${spark.version}&lt;/version&gt;\r\n
    \           &lt;scope&gt;provided&lt;/scope&gt;\r\n        &lt;/dependency&gt;\r\n
    \       &lt;dependency&gt;\r\n            &lt;groupId&gt;com.google.cloud.dataflow&lt;/groupId&gt;\r\n
    \           &lt;artifactId&gt;google-cloud-dataflow-java-sdk-all&lt;/artifactId&gt;\r\n
    \           &lt;version&gt;${google-cloud-dataflow-version}&lt;/version&gt;\r\n
    \           &lt;exclusions&gt;\r\n                &lt;!-- Use Hadoop/Spark's backend
    logger --&gt;\r\n                &lt;exclusion&gt;\r\n                    &lt;groupId&gt;org.slf4j&lt;/groupId&gt;\r\n
    \                   &lt;artifactId&gt;slf4j-jdk14&lt;/artifactId&gt;\r\n                &lt;/exclusion&gt;\r\n
    \           &lt;/exclusions&gt;\r\n        &lt;/dependency&gt;\r\n        &lt;dependency&gt;\r\n
    \           &lt;groupId&gt;com.google.cloud.dataflow&lt;/groupId&gt;\r\n            &lt;artifactId&gt;google-cloud-dataflow-java-examples-all&lt;/artifactId&gt;\r\n
    \           &lt;version&gt;${google-cloud-dataflow-version}&lt;/version&gt;\r\n
    \           &lt;exclusions&gt;\r\n                &lt;!-- Use Hadoop/Spark's backend
    logger --&gt;\r\n                &lt;exclusion&gt;\r\n                    &lt;groupId&gt;org.slf4j&lt;/groupId&gt;\r\n
    \                   &lt;artifactId&gt;slf4j-jdk14&lt;/artifactId&gt;\r\n                &lt;/exclusion&gt;\r\n
    \           &lt;/exclusions&gt;\r\n        &lt;/dependency&gt;\r\n       \t&lt;/dependencies&gt;\r\n\r\n
    \   &lt;build&gt;\r\n        &lt;plugins&gt;\r\n            &lt;plugin&gt;\r\n
    \               &lt;groupId&gt;org.apache.maven.plugins&lt;/groupId&gt;\r\n                &lt;artifactId&gt;maven-compiler-plugin&lt;/artifactId&gt;\r\n
    \               &lt;configuration&gt;\r\n                    &lt;source&gt;1.8&lt;/source&gt;\r\n
    \                   &lt;target&gt;1.8&lt;/target&gt;\r\n                &lt;/configuration&gt;\r\n
    \           &lt;/plugin&gt;\r\n\r\n        &lt;/plugins&gt;\r\n\r\n    &lt;/build&gt;\r\n&lt;/project&gt;</p></div>\n\";i:5;s:4789:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"code\"><pre
    class=\"java\" style=\"font-family:monospace;\"><span style=\"color: #000000;
    font-weight: bold;\">static</span> <span style=\"color: #000000; font-weight:
    bold;\">class</span> ExtractWordsFn <span style=\"color: #000000; font-weight:
    bold;\">extends</span> DoFn<span style=\"color: #339933;\">&lt;</span><span style=\"color:
    #003399;\">String</span>, String<span style=\"color: #339933;\">&gt;</span> <span
    style=\"color: #009900;\">&#123;</span>\n\t\t<span style=\"color: #000000; font-weight:
    bold;\">private</span> <span style=\"color: #000000; font-weight: bold;\">final</span>
    Aggregator<span style=\"color: #339933;\">&lt;</span><span style=\"color: #003399;\">Long</span>,
    Long<span style=\"color: #339933;\">&gt;</span> emptyLines <span style=\"color:
    #339933;\">=</span>\n\t\t\t\tcreateAggregator<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;emptyLines&quot;</span>, <span style=\"color:
    #000000; font-weight: bold;\">new</span> Sum.<span style=\"color: #006633;\">SumLongFn</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n\t\t@Override\n\t\t<span
    style=\"color: #000000; font-weight: bold;\">public</span> <span style=\"color:
    #000066; font-weight: bold;\">void</span> processElement<span style=\"color: #009900;\">&#40;</span>ProcessContext
    c<span style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n\t\t\t<span
    style=\"color: #000000; font-weight: bold;\">if</span> <span style=\"color: #009900;\">&#40;</span>c.<span
    style=\"color: #006633;\">element</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span>.<span style=\"color: #006633;\">trim</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">isEmpty</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#123;</span>\n\t\t\t\temptyLines.<span style=\"color:
    #006633;\">addValue</span><span style=\"color: #009900;\">&#40;</span>1L<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n\t\t\t<span
    style=\"color: #009900;\">&#125;</span>\n&nbsp;\n\t\t\t<span style=\"color: #666666;
    font-style: italic;\">// Split the line into words.</span>\n\t\t\t<span style=\"color:
    #003399;\">String</span><span style=\"color: #009900;\">&#91;</span><span style=\"color:
    #009900;\">&#93;</span> words <span style=\"color: #339933;\">=</span> c.<span
    style=\"color: #006633;\">element</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span>.<span style=\"color: #006633;\">split</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #0000ff;\">&quot;[^a-zA-Z']+&quot;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n\t\t\t<span
    style=\"color: #666666; font-style: italic;\">// Output each word encountered
    into the output PCollection.</span>\n\t\t\t<span style=\"color: #000000; font-weight:
    bold;\">for</span> <span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #003399;\">String</span> word <span style=\"color: #339933;\">:</span> words<span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n\t\t\t\t<span
    style=\"color: #000000; font-weight: bold;\">if</span> <span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #339933;\">!</span>word.<span style=\"color: #006633;\">isEmpty</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n\t\t\t\t\tc.<span
    style=\"color: #006633;\">output</span><span style=\"color: #009900;\">&#40;</span>word<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n\t\t\t\t<span
    style=\"color: #009900;\">&#125;</span>\n\t\t\t<span style=\"color: #009900;\">&#125;</span>\n\t\t<span
    style=\"color: #009900;\">&#125;</span>\n\t<span style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">static class ExtractWordsFn extends
    DoFn&lt;String, String&gt; {\r\n\t\tprivate final Aggregator&lt;Long, Long&gt;
    emptyLines =\r\n\t\t\t\tcreateAggregator(&quot;emptyLines&quot;, new Sum.SumLongFn());\r\n\r\n\t\t@Override\r\n\t\tpublic
    void processElement(ProcessContext c) {\r\n\t\t\tif (c.element().trim().isEmpty())
    {\r\n\t\t\t\temptyLines.addValue(1L);\r\n\t\t\t}\r\n\r\n\t\t\t// Split the line
    into words.\r\n\t\t\tString[] words = c.element().split(&quot;[^a-zA-Z']+&quot;);\r\n\r\n\t\t\t//
    Output each word encountered into the output PCollection.\r\n\t\t\tfor (String
    word : words) {\r\n\t\t\t\tif (!word.isEmpty()) {\r\n\t\t\t\t\tc.output(word);\r\n\t\t\t\t}\r\n\t\t\t}\r\n\t\t}\r\n\t}</p></div>\n\";i:6;s:4024:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"code\"><pre
    class=\"java\" style=\"font-family:monospace;\">\t<span style=\"color: #000000;
    font-weight: bold;\">public</span> <span style=\"color: #000000; font-weight:
    bold;\">static</span> <span style=\"color: #000000; font-weight: bold;\">class</span>
    CountWords <span style=\"color: #000000; font-weight: bold;\">extends</span> PTransform<span
    style=\"color: #339933;\">&lt;</span>PCollection<span style=\"color: #339933;\">&lt;</span>String<span
    style=\"color: #339933;\">&gt;</span>, PCollection<span style=\"color: #339933;\">&lt;</span>String<span
    style=\"color: #339933;\">&gt;&gt;</span> <span style=\"color: #009900;\">&#123;</span>\n\t\t@Override\n\t\t<span
    style=\"color: #000000; font-weight: bold;\">public</span> PCollection<span style=\"color:
    #339933;\">&lt;</span>String<span style=\"color: #339933;\">&gt;</span> apply<span
    style=\"color: #009900;\">&#40;</span>PCollection<span style=\"color: #339933;\">&lt;</span>String<span
    style=\"color: #339933;\">&gt;</span> lines<span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#123;</span>\n&nbsp;\n\t\t\t<span style=\"color:
    #666666; font-style: italic;\">// Convert lines of text into individual words.</span>\n\t\t\tPCollection<span
    style=\"color: #339933;\">&lt;</span>String<span style=\"color: #339933;\">&gt;</span>
    words <span style=\"color: #339933;\">=</span> lines.<span style=\"color: #006633;\">apply</span><span
    style=\"color: #009900;\">&#40;</span>\n\t\t\t\t\tParDo.<span style=\"color: #006633;\">of</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #000000; font-weight:
    bold;\">new</span> ExtractWordsFn<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n\t\t\t<span
    style=\"color: #666666; font-style: italic;\">// Count the number of times each
    word occurs.</span>\n\t\t\tPCollection<span style=\"color: #339933;\">&lt;</span>KV<span
    style=\"color: #339933;\">&lt;</span><span style=\"color: #003399;\">String</span>,
    Long<span style=\"color: #339933;\">&gt;&gt;</span> wordCounts <span style=\"color:
    #339933;\">=</span>\n\t\t\t\t\twords.<span style=\"color: #006633;\">apply</span><span
    style=\"color: #009900;\">&#40;</span>Count.<span style=\"color: #339933;\">&lt;</span>String<span
    style=\"color: #339933;\">&gt;</span>perElement<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\n\t\t\t<span style=\"color: #666666;
    font-style: italic;\">// Format each word and count into a printable string.</span>\n\t\t\t<span
    style=\"color: #000000; font-weight: bold;\">return</span> wordCounts.<span style=\"color:
    #006633;\">apply</span><span style=\"color: #009900;\">&#40;</span>ParDo.<span
    style=\"color: #006633;\">of</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #000000; font-weight: bold;\">new</span> FormatCountsFn<span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n\t\t<span style=\"color: #009900;\">&#125;</span>\n&nbsp;\n\t<span
    style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">\tpublic static class CountWords extends PTransform&lt;PCollection&lt;String&gt;,
    PCollection&lt;String&gt;&gt; {\r\n\t\t@Override\r\n\t\tpublic PCollection&lt;String&gt;
    apply(PCollection&lt;String&gt; lines) {\r\n\r\n\t\t\t// Convert lines of text
    into individual words.\r\n\t\t\tPCollection&lt;String&gt; words = lines.apply(\r\n\t\t\t\t\tParDo.of(new
    ExtractWordsFn()));\r\n\r\n\t\t\t// Count the number of times each word occurs.\r\n\t\t\tPCollection&lt;KV&lt;String,
    Long&gt;&gt; wordCounts =\r\n\t\t\t\t\twords.apply(Count.&lt;String&gt;perElement());\r\n\r\n\t\t\t//
    Format each word and count into a printable string.\r\n\t\t\treturn wordCounts.apply(ParDo.of(new
    FormatCountsFn()));\r\n\t\t}\r\n\r\n\t}</p></div>\n\";i:7;s:2189:\"\n<div class=\"wp_syntax\"
    style=\"position:relative;\"><table><tr><td class=\"code\"><pre class=\"java\"
    style=\"font-family:monospace;\"><span style=\"color: #000000; font-weight: bold;\">private</span>
    <span style=\"color: #000000; font-weight: bold;\">static</span> <span style=\"color:
    #000000; font-weight: bold;\">class</span> FormatCountsFn <span style=\"color:
    #000000; font-weight: bold;\">extends</span> DoFn<span style=\"color: #339933;\">&lt;</span>KV<span
    style=\"color: #339933;\">&lt;</span><span style=\"color: #003399;\">String</span>,
    Long<span style=\"color: #339933;\">&gt;</span>, String<span style=\"color: #339933;\">&gt;</span>
    <span style=\"color: #009900;\">&#123;</span>\n\t\t@Override\n\t\t<span style=\"color:
    #000000; font-weight: bold;\">public</span> <span style=\"color: #000066; font-weight:
    bold;\">void</span> processElement<span style=\"color: #009900;\">&#40;</span>ProcessContext
    c<span style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n\t\t\tc.<span
    style=\"color: #006633;\">output</span><span style=\"color: #009900;\">&#40;</span>c.<span
    style=\"color: #006633;\">element</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span>.<span style=\"color: #006633;\">getKey</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #339933;\">+</span> <span style=\"color: #0000ff;\">&quot;:
    &quot;</span> <span style=\"color: #339933;\">+</span> c.<span style=\"color:
    #006633;\">element</span><span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #009900;\">&#41;</span>.<span style=\"color: #006633;\">getValue</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n\t\t<span style=\"color:
    #009900;\">&#125;</span>\n\t<span style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">private static class FormatCountsFn
    extends DoFn&lt;KV&lt;String, Long&gt;, String&gt; {\r\n\t\t@Override\r\n\t\tpublic
    void processElement(ProcessContext c) {\r\n\t\t\tc.output(c.element().getKey()
    + &quot;: &quot; + c.element().getValue());\r\n\t\t}\r\n\t}</p></div>\n\";i:8;s:6624:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"code\"><pre
    class=\"java\" style=\"font-family:monospace;\"><span style=\"color: #000000;
    font-weight: bold;\">public</span> <span style=\"color: #000000; font-weight:
    bold;\">class</span> WordCount <span style=\"color: #009900;\">&#123;</span>\n<span
    style=\"color: #000000; font-weight: bold;\">private</span> <span style=\"color:
    #000000; font-weight: bold;\">static</span> <span style=\"color: #000000; font-weight:
    bold;\">final</span> <span style=\"color: #003399;\">String</span><span style=\"color:
    #009900;\">&#91;</span><span style=\"color: #009900;\">&#93;</span> WORDS_ARRAY
    <span style=\"color: #339933;\">=</span> <span style=\"color: #009900;\">&#123;</span>\n\t\t\t<span
    style=\"color: #0000ff;\">&quot;hi there&quot;</span>, <span style=\"color: #0000ff;\">&quot;hi&quot;</span>,
    <span style=\"color: #0000ff;\">&quot;hi sue bob&quot;</span>,\n\t\t\t<span style=\"color:
    #0000ff;\">&quot;hi sue&quot;</span>, <span style=\"color: #0000ff;\">&quot;&quot;</span>,
    <span style=\"color: #0000ff;\">&quot;bob hi&quot;</span><span style=\"color:
    #009900;\">&#125;</span><span style=\"color: #339933;\">;</span>\n\t<span style=\"color:
    #000000; font-weight: bold;\">private</span> <span style=\"color: #000000; font-weight:
    bold;\">static</span> <span style=\"color: #000000; font-weight: bold;\">final</span>
    List<span style=\"color: #339933;\">&lt;</span>String<span style=\"color: #339933;\">&gt;</span>
    WORDS <span style=\"color: #339933;\">=</span> <span style=\"color: #003399;\">Arrays</span>.<span
    style=\"color: #006633;\">asList</span><span style=\"color: #009900;\">&#40;</span>WORDS_ARRAY<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n\t<span
    style=\"color: #000000; font-weight: bold;\">private</span> <span style=\"color:
    #000000; font-weight: bold;\">static</span> <span style=\"color: #000000; font-weight:
    bold;\">final</span> Set<span style=\"color: #339933;\">&lt;</span>String<span
    style=\"color: #339933;\">&gt;</span> EXPECTED_COUNT_SET <span style=\"color:
    #339933;\">=</span>\n\t\t\tImmutableSet.<span style=\"color: #006633;\">of</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #0000ff;\">&quot;hi:
    5&quot;</span>, <span style=\"color: #0000ff;\">&quot;there: 1&quot;</span>, <span
    style=\"color: #0000ff;\">&quot;sue: 2&quot;</span>, <span style=\"color: #0000ff;\">&quot;bob:
    2&quot;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n&nbsp;\n\t<span style=\"color: #000000; font-weight: bold;\">public</span>
    <span style=\"color: #000000; font-weight: bold;\">static</span> <span style=\"color:
    #000066; font-weight: bold;\">void</span> main<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #003399;\">String</span><span style=\"color: #009900;\">&#91;</span><span
    style=\"color: #009900;\">&#93;</span> args<span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#123;</span>\n\t\tSparkPipelineOptions options
    <span style=\"color: #339933;\">=</span> SparkPipelineOptionsFactory.<span style=\"color:
    #006633;\">create</span><span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n\t\toptions.<span
    style=\"color: #006633;\">setRunner</span><span style=\"color: #009900;\">&#40;</span>SparkPipelineRunner.<span
    style=\"color: #000000; font-weight: bold;\">class</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n\t\tPipeline
    p <span style=\"color: #339933;\">=</span> Pipeline.<span style=\"color: #006633;\">create</span><span
    style=\"color: #009900;\">&#40;</span>options<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n\t\tPCollection<span style=\"color: #339933;\">&lt;</span>String<span
    style=\"color: #339933;\">&gt;</span> output<span style=\"color: #339933;\">=</span>p.<span
    style=\"color: #006633;\">apply</span><span style=\"color: #009900;\">&#40;</span>Create.<span
    style=\"color: #006633;\">of</span><span style=\"color: #009900;\">&#40;</span>WORDS<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">setCoder</span><span style=\"color: #009900;\">&#40;</span>StringUtf8Coder.<span
    style=\"color: #006633;\">of</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">apply</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #000000; font-weight: bold;\">new</span> CountWords<span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n\t\tSparkPipelineRunner
    runner <span style=\"color: #339933;\">=</span> SparkPipelineRunner.<span style=\"color:
    #006633;\">create</span><span style=\"color: #009900;\">&#40;</span>options<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n\t\tEvaluationResult
    result <span style=\"color: #339933;\">=</span> runner.<span style=\"color: #006633;\">run</span><span
    style=\"color: #009900;\">&#40;</span>p<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n\t\tDataflowAssert.<span style=\"color: #006633;\">that</span><span
    style=\"color: #009900;\">&#40;</span>output<span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">containsInAnyOrder</span><span style=\"color: #009900;\">&#40;</span>EXPECTED_COUNT_SET<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n\t\t\t<span
    style=\"color: #009900;\">&#125;</span><span style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">public class WordCount {\r\nprivate
    static final String[] WORDS_ARRAY = {\r\n\t\t\t&quot;hi there&quot;, &quot;hi&quot;,
    &quot;hi sue bob&quot;,\r\n\t\t\t&quot;hi sue&quot;, &quot;&quot;, &quot;bob hi&quot;};\r\n\tprivate
    static final List&lt;String&gt; WORDS = Arrays.asList(WORDS_ARRAY);\r\n\tprivate
    static final Set&lt;String&gt; EXPECTED_COUNT_SET =\r\n\t\t\tImmutableSet.of(&quot;hi:
    5&quot;, &quot;there: 1&quot;, &quot;sue: 2&quot;, &quot;bob: 2&quot;);\r\n\r\n\tpublic
    static void main(String[] args) {\r\n\t\tSparkPipelineOptions options = SparkPipelineOptionsFactory.create();\r\n\r\n\t\toptions.setRunner(SparkPipelineRunner.class);\r\n\t\tPipeline
    p = Pipeline.create(options);\r\n\t\tPCollection&lt;String&gt; output=p.apply(Create.of(WORDS)).setCoder(StringUtf8Coder.of()).apply(new
    CountWords());\r\n\t\tSparkPipelineRunner runner = SparkPipelineRunner.create(options);\r\n\t\tEvaluationResult
    result = runner.run(p);\r\n\t\tDataflowAssert.that(output).containsInAnyOrder(EXPECTED_COUNT_SET);\r\n\t\t\t}}</p></div>\n\";i:9;s:21457:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"code\"><pre
    class=\"java\" style=\"font-family:monospace;\"><span style=\"color: #000000;
    font-weight: bold;\">package</span> <span style=\"color: #006699;\">com.ts.beam.spark</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">com.cloudera.dataflow.spark.EvaluationResult</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">com.cloudera.dataflow.spark.SparkPipelineOptions</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">com.cloudera.dataflow.spark.SparkPipelineOptionsFactory</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">com.cloudera.dataflow.spark.SparkPipelineRunner</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">com.google.cloud.dataflow.sdk.Pipeline</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">com.google.cloud.dataflow.sdk.coders.StringUtf8Coder</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">com.google.cloud.dataflow.sdk.io.TextIO</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">com.google.cloud.dataflow.sdk.options.PipelineOptions</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">com.google.cloud.dataflow.sdk.repackaged.com.google.common.collect.ImmutableSet</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">com.google.cloud.dataflow.sdk.testing.DataflowAssert</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">com.google.cloud.dataflow.sdk.transforms.*</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">com.google.cloud.dataflow.sdk.util.SystemDoFnInternal</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">com.google.cloud.dataflow.sdk.values.KV</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">com.google.cloud.dataflow.sdk.values.PCollection</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">java.nio.channels.Pipe</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">java.util.Arrays</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">java.util.List</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">java.util.Set</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\n<span style=\"color: #000000; font-weight:
    bold;\">public</span> <span style=\"color: #000000; font-weight: bold;\">class</span>
    WordCount <span style=\"color: #009900;\">&#123;</span>\n\t<span style=\"color:
    #000000; font-weight: bold;\">private</span> <span style=\"color: #000000; font-weight:
    bold;\">static</span> <span style=\"color: #000000; font-weight: bold;\">final</span>
    <span style=\"color: #003399;\">String</span><span style=\"color: #009900;\">&#91;</span><span
    style=\"color: #009900;\">&#93;</span> WORDS_ARRAY <span style=\"color: #339933;\">=</span>
    <span style=\"color: #009900;\">&#123;</span>\n\t\t\t<span style=\"color: #0000ff;\">&quot;hi
    there&quot;</span>, <span style=\"color: #0000ff;\">&quot;hi&quot;</span>, <span
    style=\"color: #0000ff;\">&quot;hi sue bob&quot;</span>,\n\t\t\t<span style=\"color:
    #0000ff;\">&quot;hi sue&quot;</span>, <span style=\"color: #0000ff;\">&quot;&quot;</span>,
    <span style=\"color: #0000ff;\">&quot;bob hi&quot;</span><span style=\"color:
    #009900;\">&#125;</span><span style=\"color: #339933;\">;</span>\n\t<span style=\"color:
    #000000; font-weight: bold;\">private</span> <span style=\"color: #000000; font-weight:
    bold;\">static</span> <span style=\"color: #000000; font-weight: bold;\">final</span>
    List<span style=\"color: #339933;\">&lt;</span>String<span style=\"color: #339933;\">&gt;</span>
    WORDS <span style=\"color: #339933;\">=</span> <span style=\"color: #003399;\">Arrays</span>.<span
    style=\"color: #006633;\">asList</span><span style=\"color: #009900;\">&#40;</span>WORDS_ARRAY<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n\t<span
    style=\"color: #000000; font-weight: bold;\">private</span> <span style=\"color:
    #000000; font-weight: bold;\">static</span> <span style=\"color: #000000; font-weight:
    bold;\">final</span> Set<span style=\"color: #339933;\">&lt;</span>String<span
    style=\"color: #339933;\">&gt;</span> EXPECTED_COUNT_SET <span style=\"color:
    #339933;\">=</span>\n\t\t\tImmutableSet.<span style=\"color: #006633;\">of</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #0000ff;\">&quot;hi:
    5&quot;</span>, <span style=\"color: #0000ff;\">&quot;there: 1&quot;</span>, <span
    style=\"color: #0000ff;\">&quot;sue: 2&quot;</span>, <span style=\"color: #0000ff;\">&quot;bob:
    2&quot;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n&nbsp;\n\t<span style=\"color: #000000; font-weight: bold;\">public</span>
    <span style=\"color: #000000; font-weight: bold;\">static</span> <span style=\"color:
    #000066; font-weight: bold;\">void</span> main<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #003399;\">String</span><span style=\"color: #009900;\">&#91;</span><span
    style=\"color: #009900;\">&#93;</span> args<span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#123;</span>\n\t\tSparkPipelineOptions options
    <span style=\"color: #339933;\">=</span> SparkPipelineOptionsFactory.<span style=\"color:
    #006633;\">create</span><span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n\t\toptions.<span
    style=\"color: #006633;\">setRunner</span><span style=\"color: #009900;\">&#40;</span>SparkPipelineRunner.<span
    style=\"color: #000000; font-weight: bold;\">class</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n\t\tPipeline
    p <span style=\"color: #339933;\">=</span> Pipeline.<span style=\"color: #006633;\">create</span><span
    style=\"color: #009900;\">&#40;</span>options<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n\t\tPCollection<span style=\"color: #339933;\">&lt;</span>String<span
    style=\"color: #339933;\">&gt;</span> output<span style=\"color: #339933;\">=</span>p.<span
    style=\"color: #006633;\">apply</span><span style=\"color: #009900;\">&#40;</span>Create.<span
    style=\"color: #006633;\">of</span><span style=\"color: #009900;\">&#40;</span>WORDS<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">setCoder</span><span style=\"color: #009900;\">&#40;</span>StringUtf8Coder.<span
    style=\"color: #006633;\">of</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">apply</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #000000; font-weight: bold;\">new</span> CountWords<span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n\t\tSparkPipelineRunner
    runner <span style=\"color: #339933;\">=</span> SparkPipelineRunner.<span style=\"color:
    #006633;\">create</span><span style=\"color: #009900;\">&#40;</span>options<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n\t\tEvaluationResult
    result <span style=\"color: #339933;\">=</span> runner.<span style=\"color: #006633;\">run</span><span
    style=\"color: #009900;\">&#40;</span>p<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n\t\tDataflowAssert.<span style=\"color: #006633;\">that</span><span
    style=\"color: #009900;\">&#40;</span>output<span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">containsInAnyOrder</span><span style=\"color: #009900;\">&#40;</span>EXPECTED_COUNT_SET<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n\t<span
    style=\"color: #009900;\">&#125;</span>\n&nbsp;\n\t<span style=\"color: #000000;
    font-weight: bold;\">static</span> <span style=\"color: #000000; font-weight:
    bold;\">class</span> ExtractWordsFn <span style=\"color: #000000; font-weight:
    bold;\">extends</span> DoFn<span style=\"color: #339933;\">&lt;</span><span style=\"color:
    #003399;\">String</span>, String<span style=\"color: #339933;\">&gt;</span> <span
    style=\"color: #009900;\">&#123;</span>\n\t\t<span style=\"color: #000000; font-weight:
    bold;\">private</span> <span style=\"color: #000000; font-weight: bold;\">final</span>
    Aggregator<span style=\"color: #339933;\">&lt;</span><span style=\"color: #003399;\">Long</span>,
    Long<span style=\"color: #339933;\">&gt;</span> emptyLines <span style=\"color:
    #339933;\">=</span>\n\t\t\t\tcreateAggregator<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;emptyLines&quot;</span>, <span style=\"color:
    #000000; font-weight: bold;\">new</span> Sum.<span style=\"color: #006633;\">SumLongFn</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n\t\t@Override\n\t\t<span
    style=\"color: #000000; font-weight: bold;\">public</span> <span style=\"color:
    #000066; font-weight: bold;\">void</span> processElement<span style=\"color: #009900;\">&#40;</span>ProcessContext
    c<span style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n\t\t\t<span
    style=\"color: #000000; font-weight: bold;\">if</span> <span style=\"color: #009900;\">&#40;</span>c.<span
    style=\"color: #006633;\">element</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span>.<span style=\"color: #006633;\">trim</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">isEmpty</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#123;</span>\n\t\t\t\temptyLines.<span style=\"color:
    #006633;\">addValue</span><span style=\"color: #009900;\">&#40;</span>1L<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n\t\t\t<span
    style=\"color: #009900;\">&#125;</span>\n&nbsp;\n\t\t\t<span style=\"color: #666666;
    font-style: italic;\">// Split the line into words.</span>\n\t\t\t<span style=\"color:
    #003399;\">String</span><span style=\"color: #009900;\">&#91;</span><span style=\"color:
    #009900;\">&#93;</span> words <span style=\"color: #339933;\">=</span> c.<span
    style=\"color: #006633;\">element</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span>.<span style=\"color: #006633;\">split</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #0000ff;\">&quot;[^a-zA-Z']+&quot;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n\t\t\t<span
    style=\"color: #666666; font-style: italic;\">// Output each word encountered
    into the output PCollection.</span>\n\t\t\t<span style=\"color: #000000; font-weight:
    bold;\">for</span> <span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #003399;\">String</span> word <span style=\"color: #339933;\">:</span> words<span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n\t\t\t\t<span
    style=\"color: #000000; font-weight: bold;\">if</span> <span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #339933;\">!</span>word.<span style=\"color: #006633;\">isEmpty</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n\t\t\t\t\tc.<span
    style=\"color: #006633;\">output</span><span style=\"color: #009900;\">&#40;</span>word<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n\t\t\t\t<span
    style=\"color: #009900;\">&#125;</span>\n\t\t\t<span style=\"color: #009900;\">&#125;</span>\n\t\t<span
    style=\"color: #009900;\">&#125;</span>\n\t<span style=\"color: #009900;\">&#125;</span>\n\t<span
    style=\"color: #000000; font-weight: bold;\">public</span> <span style=\"color:
    #000000; font-weight: bold;\">static</span> <span style=\"color: #000000; font-weight:
    bold;\">class</span> CountWords <span style=\"color: #000000; font-weight: bold;\">extends</span>
    PTransform<span style=\"color: #339933;\">&lt;</span>PCollection<span style=\"color:
    #339933;\">&lt;</span>String<span style=\"color: #339933;\">&gt;</span>, PCollection<span
    style=\"color: #339933;\">&lt;</span>String<span style=\"color: #339933;\">&gt;&gt;</span>
    <span style=\"color: #009900;\">&#123;</span>\n\t\t@Override\n\t\t<span style=\"color:
    #000000; font-weight: bold;\">public</span> PCollection<span style=\"color: #339933;\">&lt;</span>String<span
    style=\"color: #339933;\">&gt;</span> apply<span style=\"color: #009900;\">&#40;</span>PCollection<span
    style=\"color: #339933;\">&lt;</span>String<span style=\"color: #339933;\">&gt;</span>
    lines<span style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n&nbsp;\n\t\t\t<span
    style=\"color: #666666; font-style: italic;\">// Convert lines of text into individual
    words.</span>\n\t\t\tPCollection<span style=\"color: #339933;\">&lt;</span>String<span
    style=\"color: #339933;\">&gt;</span> words <span style=\"color: #339933;\">=</span>
    lines.<span style=\"color: #006633;\">apply</span><span style=\"color: #009900;\">&#40;</span>\n\t\t\t\t\tParDo.<span
    style=\"color: #006633;\">of</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #000000; font-weight: bold;\">new</span> ExtractWordsFn<span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n&nbsp;\n\t\t\t<span style=\"color: #666666; font-style: italic;\">//
    Count the number of times each word occurs.</span>\n\t\t\tPCollection<span style=\"color:
    #339933;\">&lt;</span>KV<span style=\"color: #339933;\">&lt;</span><span style=\"color:
    #003399;\">String</span>, Long<span style=\"color: #339933;\">&gt;&gt;</span>
    wordCounts <span style=\"color: #339933;\">=</span>\n\t\t\t\t\twords.<span style=\"color:
    #006633;\">apply</span><span style=\"color: #009900;\">&#40;</span>Count.<span
    style=\"color: #339933;\">&lt;</span>String<span style=\"color: #339933;\">&gt;</span>perElement<span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n\t\t\t<span
    style=\"color: #666666; font-style: italic;\">// Format each word and count into
    a printable string.</span>\n\t\t\t<span style=\"color: #000000; font-weight: bold;\">return</span>
    wordCounts.<span style=\"color: #006633;\">apply</span><span style=\"color: #009900;\">&#40;</span>ParDo.<span
    style=\"color: #006633;\">of</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #000000; font-weight: bold;\">new</span> FormatCountsFn<span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n\t\t<span style=\"color: #009900;\">&#125;</span>\n&nbsp;\n\t<span
    style=\"color: #009900;\">&#125;</span>\n\t<span style=\"color: #000000; font-weight:
    bold;\">private</span> <span style=\"color: #000000; font-weight: bold;\">static</span>
    <span style=\"color: #000000; font-weight: bold;\">class</span> FormatCountsFn
    <span style=\"color: #000000; font-weight: bold;\">extends</span> DoFn<span style=\"color:
    #339933;\">&lt;</span>KV<span style=\"color: #339933;\">&lt;</span><span style=\"color:
    #003399;\">String</span>, Long<span style=\"color: #339933;\">&gt;</span>, String<span
    style=\"color: #339933;\">&gt;</span> <span style=\"color: #009900;\">&#123;</span>\n\t\t@Override\n\t\t<span
    style=\"color: #000000; font-weight: bold;\">public</span> <span style=\"color:
    #000066; font-weight: bold;\">void</span> processElement<span style=\"color: #009900;\">&#40;</span>ProcessContext
    c<span style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n\t\t\tc.<span
    style=\"color: #006633;\">output</span><span style=\"color: #009900;\">&#40;</span>c.<span
    style=\"color: #006633;\">element</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span>.<span style=\"color: #006633;\">getKey</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #339933;\">+</span> <span style=\"color: #0000ff;\">&quot;:
    &quot;</span> <span style=\"color: #339933;\">+</span> c.<span style=\"color:
    #006633;\">element</span><span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #009900;\">&#41;</span>.<span style=\"color: #006633;\">getValue</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n\t\t<span style=\"color:
    #009900;\">&#125;</span>\n\t<span style=\"color: #009900;\">&#125;</span>\n&nbsp;\n<span
    style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">package com.ts.beam.spark;\r\n\r\nimport com.cloudera.dataflow.spark.EvaluationResult;\r\nimport
    com.cloudera.dataflow.spark.SparkPipelineOptions;\r\nimport com.cloudera.dataflow.spark.SparkPipelineOptionsFactory;\r\nimport
    com.cloudera.dataflow.spark.SparkPipelineRunner;\r\nimport com.google.cloud.dataflow.sdk.Pipeline;\r\nimport
    com.google.cloud.dataflow.sdk.coders.StringUtf8Coder;\r\nimport com.google.cloud.dataflow.sdk.io.TextIO;\r\nimport
    com.google.cloud.dataflow.sdk.options.PipelineOptions;\r\nimport com.google.cloud.dataflow.sdk.repackaged.com.google.common.collect.ImmutableSet;\r\nimport
    com.google.cloud.dataflow.sdk.testing.DataflowAssert;\r\nimport com.google.cloud.dataflow.sdk.transforms.*;\r\nimport
    com.google.cloud.dataflow.sdk.util.SystemDoFnInternal;\r\nimport com.google.cloud.dataflow.sdk.values.KV;\r\nimport
    com.google.cloud.dataflow.sdk.values.PCollection;\r\n\r\nimport java.nio.channels.Pipe;\r\nimport
    java.util.Arrays;\r\nimport java.util.List;\r\nimport java.util.Set;\r\n\r\npublic
    class WordCount {\r\n\tprivate static final String[] WORDS_ARRAY = {\r\n\t\t\t&quot;hi
    there&quot;, &quot;hi&quot;, &quot;hi sue bob&quot;,\r\n\t\t\t&quot;hi sue&quot;,
    &quot;&quot;, &quot;bob hi&quot;};\r\n\tprivate static final List&lt;String&gt;
    WORDS = Arrays.asList(WORDS_ARRAY);\r\n\tprivate static final Set&lt;String&gt;
    EXPECTED_COUNT_SET =\r\n\t\t\tImmutableSet.of(&quot;hi: 5&quot;, &quot;there:
    1&quot;, &quot;sue: 2&quot;, &quot;bob: 2&quot;);\r\n\r\n\tpublic static void
    main(String[] args) {\r\n\t\tSparkPipelineOptions options = SparkPipelineOptionsFactory.create();\r\n\r\n\t\toptions.setRunner(SparkPipelineRunner.class);\r\n\t\tPipeline
    p = Pipeline.create(options);\r\n\t\tPCollection&lt;String&gt; output=p.apply(Create.of(WORDS)).setCoder(StringUtf8Coder.of()).apply(new
    CountWords());\r\n\t\tSparkPipelineRunner runner = SparkPipelineRunner.create(options);\r\n\t\tEvaluationResult
    result = runner.run(p);\r\n\t\tDataflowAssert.that(output).containsInAnyOrder(EXPECTED_COUNT_SET);\r\n\r\n\t}\r\n\r\n\tstatic
    class ExtractWordsFn extends DoFn&lt;String, String&gt; {\r\n\t\tprivate final
    Aggregator&lt;Long, Long&gt; emptyLines =\r\n\t\t\t\tcreateAggregator(&quot;emptyLines&quot;,
    new Sum.SumLongFn());\r\n\r\n\t\t@Override\r\n\t\tpublic void processElement(ProcessContext
    c) {\r\n\t\t\tif (c.element().trim().isEmpty()) {\r\n\t\t\t\temptyLines.addValue(1L);\r\n\t\t\t}\r\n\r\n\t\t\t//
    Split the line into words.\r\n\t\t\tString[] words = c.element().split(&quot;[^a-zA-Z']+&quot;);\r\n\r\n\t\t\t//
    Output each word encountered into the output PCollection.\r\n\t\t\tfor (String
    word : words) {\r\n\t\t\t\tif (!word.isEmpty()) {\r\n\t\t\t\t\tc.output(word);\r\n\t\t\t\t}\r\n\t\t\t}\r\n\t\t}\r\n\t}\r\n\tpublic
    static class CountWords extends PTransform&lt;PCollection&lt;String&gt;, PCollection&lt;String&gt;&gt;
    {\r\n\t\t@Override\r\n\t\tpublic PCollection&lt;String&gt; apply(PCollection&lt;String&gt;
    lines) {\r\n\r\n\t\t\t// Convert lines of text into individual words.\r\n\t\t\tPCollection&lt;String&gt;
    words = lines.apply(\r\n\t\t\t\t\tParDo.of(new ExtractWordsFn()));\r\n\r\n\t\t\t//
    Count the number of times each word occurs.\r\n\t\t\tPCollection&lt;KV&lt;String,
    Long&gt;&gt; wordCounts =\r\n\t\t\t\t\twords.apply(Count.&lt;String&gt;perElement());\r\n\r\n\t\t\t//
    Format each word and count into a printable string.\r\n\t\t\treturn wordCounts.apply(ParDo.of(new
    FormatCountsFn()));\r\n\t\t}\r\n\r\n\t}\r\n\tprivate static class FormatCountsFn
    extends DoFn&lt;KV&lt;String, Long&gt;, String&gt; {\r\n\t\t@Override\r\n\t\tpublic
    void processElement(ProcessContext c) {\r\n\t\t\tc.output(c.element().getKey()
    + &quot;: &quot; + c.element().getValue());\r\n\t\t}\r\n\t}\r\n\r\n}</p></div>\n\";}"
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/apache-beam-spark-runner-example-using-maven/"
---
In this post I will show you how to create Apache Beam Spark Runner project using Maven.

Tools/ Frameworks used:

- Java 8
- Apache Spark
- Maven
- Intellij
- Apache Beam

  
1. Add Cloudera repository in maven settings.xml

```
<repository>
      <id>cloudera</id>
      <url>https://repository.cloudera.com/artifactory/cloudera-repos/</url>
    </repository>
```

full settings.xml file:

```
<settings></settings><profiles><profile>
      <id>cld</id>

      <repositories>
       <repository>
      <id>cloudera</id>
      <url>https://repository.cloudera.com/artifactory/cloudera-repos/</url>
    </repository>
     <repository>
      <id>mvn</id>
      <url>http://repo1.maven.org/maven2/</url>
    <release>
    	<enabled>true</enabled>
    </release>
    <snapshots>
    	<enabled>true</enabled>
    </snapshots>
    </repository>
      </repositories>
      
    </profile> </profiles> <activeprofiles>
    <activeprofile>cld</activeprofile>
  </activeprofiles>
```

2. Create maven project

```
mvn archetype:generate -DgroupId=com.ts.spark -DartifactId=beam-spark -DarchetypeArtifactId=maven-archetype-quickstart
```

3. Add Below dependencies to pom file:

```
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemalocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelversion>4.0.0</modelversion>

	<groupid>com.ts.spark</groupid>
	<artifactid>beam-spark</artifactid>
	<version>0.0.1-SNAPSHOT</version>
	<packaging>jar</packaging>

	<name>beam-spark</name>
	<url>http://maven.apache.org</url>

	<properties>
        <project.build.sourceencoding>UTF-8</project.build.sourceencoding>
        <project.reporting.outputencoding>UTF-8</project.reporting.outputencoding>
        <java.version>1.7</java.version>
        <spark.version>1.5.2</spark.version>
        <google-cloud-dataflow-version>1.3.0</google-cloud-dataflow-version>
    </properties>

	<dependencies>
		<dependency>
			<groupid>org.testng</groupid>
			<artifactid>testng</artifactid>
			<version>6.8</version>
			<scope>test</scope>
		</dependency>
		<dependency>
			<groupid>com.cloudera.dataflow.spark</groupid>
			<artifactid>spark-dataflow</artifactid>
			<version>0.4.2</version>
		</dependency>
		<dependency>
            <groupid>org.apache.spark</groupid>
            <artifactid>spark-core_2.10</artifactid>
            <version>${spark.version}</version>
        </dependency>
        <dependency>
            <groupid>org.apache.spark</groupid>
            <artifactid>spark-streaming_2.10</artifactid>
            <version>${spark.version}</version>
            <scope>provided</scope>
        </dependency>
        <dependency>
            <groupid>com.google.cloud.dataflow</groupid>
            <artifactid>google-cloud-dataflow-java-sdk-all</artifactid>
            <version>${google-cloud-dataflow-version}</version>
            <exclusions>
                <!-- Use Hadoop/Spark's backend logger -->
                <exclusion>
                    <groupid>org.slf4j</groupid>
                    <artifactid>slf4j-jdk14</artifactid>
                </exclusion>
            </exclusions>
        </dependency>
        <dependency>
            <groupid>com.google.cloud.dataflow</groupid>
            <artifactid>google-cloud-dataflow-java-examples-all</artifactid>
            <version>${google-cloud-dataflow-version}</version>
            <exclusions>
                <!-- Use Hadoop/Spark's backend logger -->
                <exclusion>
                    <groupid>org.slf4j</groupid>
                    <artifactid>slf4j-jdk14</artifactid>
                </exclusion>
            </exclusions>
        </dependency>
       	</dependencies>

    <build>
        <plugins>
            <plugin>
                <groupid>org.apache.maven.plugins</groupid>
                <artifactid>maven-compiler-plugin</artifactid>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>

        </plugins>

    </build>
</project>
```

4. Function to extract words:

```
static class ExtractWordsFn extends DoFn<string string> {
		private final Aggregator<long long> emptyLines =
				createAggregator("emptyLines", new Sum.SumLongFn());

		@Override
		public void processElement(ProcessContext c) {
			if (c.element().trim().isEmpty()) {
				emptyLines.addValue(1L);
			}

			// Split the line into words.
			String[] words = c.element().split("[^a-zA-Z']+");

			// Output each word encountered into the output PCollection.
			for (String word : words) {
				if (!word.isEmpty()) {
					c.output(word);
				}
			}
		}
	}</long></string>
```

5. Count words function:

```
public static class CountWords extends PTransform<pcollection>, PCollection<string>&gt; {
		@Override
		public PCollection<string> apply(PCollection<string> lines) {

			// Convert lines of text into individual words.
			PCollection<string> words = lines.apply(
					ParDo.of(new ExtractWordsFn()));

			// Count the number of times each word occurs.
			PCollection<kv long>&gt; wordCounts =
					words.apply(Count.<string>perElement());

			// Format each word and count into a printable string.
			return wordCounts.apply(ParDo.of(new FormatCountsFn()));
		}

	}</string></kv></string></string></string></string></pcollection>
```

6. Format output:

```
private static class FormatCountsFn extends DoFn<kv long>, String&gt; {
		@Override
		public void processElement(ProcessContext c) {
			c.output(c.element().getKey() + ": " + c.element().getValue());
		}
	}</kv>
```

7. Driver Method:

```
public class WordCount { private static final String[] WORDS\_ARRAY = { "hi there", "hi", "hi sue bob", "hi sue", "", "bob hi"}; private static final List<string> WORDS = Arrays.asList(WORDS_ARRAY);
	private static final Set<string> EXPECTED_COUNT_SET =
			ImmutableSet.of("hi: 5", "there: 1", "sue: 2", "bob: 2");

	public static void main(String[] args) {
		SparkPipelineOptions options = SparkPipelineOptionsFactory.create();

		options.setRunner(SparkPipelineRunner.class);
		Pipeline p = Pipeline.create(options);
		PCollection<string> output=p.apply(Create.of(WORDS)).setCoder(StringUtf8Coder.of()).apply(new CountWords());
		SparkPipelineRunner runner = SparkPipelineRunner.create(options);
		EvaluationResult result = runner.run(p);
		DataflowAssert.that(output).containsInAnyOrder(EXPECTED_COUNT_SET);
			}}</string></string></string>
```

8. Full Driver class:

```
package com.ts.beam.spark; import com.cloudera.dataflow.spark.EvaluationResult; import com.cloudera.dataflow.spark.SparkPipelineOptions; import com.cloudera.dataflow.spark.SparkPipelineOptionsFactory; import com.cloudera.dataflow.spark.SparkPipelineRunner; import com.google.cloud.dataflow.sdk.Pipeline; import com.google.cloud.dataflow.sdk.coders.StringUtf8Coder; import com.google.cloud.dataflow.sdk.io.TextIO; import com.google.cloud.dataflow.sdk.options.PipelineOptions; import com.google.cloud.dataflow.sdk.repackaged.com.google.common.collect.ImmutableSet; import com.google.cloud.dataflow.sdk.testing.DataflowAssert; import com.google.cloud.dataflow.sdk.transforms.\*; import com.google.cloud.dataflow.sdk.util.SystemDoFnInternal; import com.google.cloud.dataflow.sdk.values.KV; import com.google.cloud.dataflow.sdk.values.PCollection; import java.nio.channels.Pipe; import java.util.Arrays; import java.util.List; import java.util.Set; public class WordCount { private static final String[] WORDS\_ARRAY = { "hi there", "hi", "hi sue bob", "hi sue", "", "bob hi"}; private static final List<string> WORDS = Arrays.asList(WORDS_ARRAY);
	private static final Set<string> EXPECTED_COUNT_SET =
			ImmutableSet.of("hi: 5", "there: 1", "sue: 2", "bob: 2");

	public static void main(String[] args) {
		SparkPipelineOptions options = SparkPipelineOptionsFactory.create();

		options.setRunner(SparkPipelineRunner.class);
		Pipeline p = Pipeline.create(options);
		PCollection<string> output=p.apply(Create.of(WORDS)).setCoder(StringUtf8Coder.of()).apply(new CountWords());
		SparkPipelineRunner runner = SparkPipelineRunner.create(options);
		EvaluationResult result = runner.run(p);
		DataflowAssert.that(output).containsInAnyOrder(EXPECTED_COUNT_SET);

	}

	static class ExtractWordsFn extends DoFn<string string> {
		private final Aggregator<long long> emptyLines =
				createAggregator("emptyLines", new Sum.SumLongFn());

		@Override
		public void processElement(ProcessContext c) {
			if (c.element().trim().isEmpty()) {
				emptyLines.addValue(1L);
			}

			// Split the line into words.
			String[] words = c.element().split("[^a-zA-Z']+");

			// Output each word encountered into the output PCollection.
			for (String word : words) {
				if (!word.isEmpty()) {
					c.output(word);
				}
			}
		}
	}
	public static class CountWords extends PTransform<pcollection>, PCollection<string>&gt; {
		@Override
		public PCollection<string> apply(PCollection<string> lines) {

			// Convert lines of text into individual words.
			PCollection<string> words = lines.apply(
					ParDo.of(new ExtractWordsFn()));

			// Count the number of times each word occurs.
			PCollection<kv long>&gt; wordCounts =
					words.apply(Count.<string>perElement());

			// Format each word and count into a printable string.
			return wordCounts.apply(ParDo.of(new FormatCountsFn()));
		}

	}
	private static class FormatCountsFn extends DoFn<kv long>, String&gt; {
		@Override
		public void processElement(ProcessContext c) {
			c.output(c.element().getKey() + ": " + c.element().getValue());
		}
	}

}
</kv></string></kv></string></string></string></string></pcollection></long></string></string></string></string>
```
