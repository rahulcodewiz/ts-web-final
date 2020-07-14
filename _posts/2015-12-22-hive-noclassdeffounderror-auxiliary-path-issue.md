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
  wp-syntax-cache-content: "a:3:{i:1;s:377:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"line_numbers\"><pre>1\n2\n</pre></td><td class=\"code\"><pre class=\"unix\"
    style=\"font-family:monospace;\">add jar /xxx/hive-customserde.jar;\r\nadd jar
    /xxx/solr-solrj.jar;</pre></td></tr></table><p class=\"theCode\" style=\"display:none;\">add
    jar /xxx/hive-customserde.jar;\r\nadd jar /xxx/solr-solrj.jar;</p></div>\n\";i:2;s:8481:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n9\n10\n11\n12\n13\n14\n</pre></td><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\"><span style=\"color:
    #003399;\">Exception</span> in thread <span style=\"color: #0000ff;\">&quot;main&quot;</span>
    java.<span style=\"color: #006633;\">lang</span>.<span style=\"color: #003399;\">NoClassDefFoundError</span><span
    style=\"color: #339933;\">:</span> org<span style=\"color: #339933;\">/</span>apache<span
    style=\"color: #339933;\">/</span>solr<span style=\"color: #339933;\">/</span>client<span
    style=\"color: #339933;\">/</span>solrj<span style=\"color: #339933;\">/</span>SolrServerException\nat
    com.<span style=\"color: #006633;\">aexp</span>.<span style=\"color: #006633;\">ims</span>.<span
    style=\"color: #006633;\">atworks</span>.<span style=\"color: #006633;\">hive</span>.<span
    style=\"color: #006633;\">solr</span>.<span style=\"color: #006633;\">SolrSplit</span>.<span
    style=\"color: #006633;\">getSplits</span><span style=\"color: #009900;\">&#40;</span>SolrSplit.<span
    style=\"color: #006633;\">java</span><span style=\"color: #339933;\">:</span><span
    style=\"color: #cc66cc;\">84</span><span style=\"color: #009900;\">&#41;</span>\nat
    com.<span style=\"color: #006633;\">aexp</span>.<span style=\"color: #006633;\">ims</span>.<span
    style=\"color: #006633;\">atworks</span>.<span style=\"color: #006633;\">hive</span>.<span
    style=\"color: #006633;\">solr</span>.<span style=\"color: #006633;\">SolrInputFormat</span>.<span
    style=\"color: #006633;\">getSplits</span><span style=\"color: #009900;\">&#40;</span>SolrInputFormat.<span
    style=\"color: #006633;\">java</span><span style=\"color: #339933;\">:</span><span
    style=\"color: #cc66cc;\">91</span><span style=\"color: #009900;\">&#41;</span>\nat
    org.<span style=\"color: #006633;\">apache</span>.<span style=\"color: #006633;\">hadoop</span>.<span
    style=\"color: #006633;\">hive</span>.<span style=\"color: #006633;\">ql</span>.<span
    style=\"color: #006633;\">exec</span>.<span style=\"color: #006633;\">FetchOperator</span>.<span
    style=\"color: #006633;\">getRecordReader</span><span style=\"color: #009900;\">&#40;</span>FetchOperator.<span
    style=\"color: #006633;\">java</span><span style=\"color: #339933;\">:</span><span
    style=\"color: #cc66cc;\">419</span><span style=\"color: #009900;\">&#41;</span>\nat
    org.<span style=\"color: #006633;\">apache</span>.<span style=\"color: #006633;\">hadoop</span>.<span
    style=\"color: #006633;\">hive</span>.<span style=\"color: #006633;\">ql</span>.<span
    style=\"color: #006633;\">exec</span>.<span style=\"color: #006633;\">FetchOperator</span>.<span
    style=\"color: #006633;\">getNextRow</span><span style=\"color: #009900;\">&#40;</span>FetchOperator.<span
    style=\"color: #006633;\">java</span><span style=\"color: #339933;\">:</span><span
    style=\"color: #cc66cc;\">573</span><span style=\"color: #009900;\">&#41;</span>\nat
    org.<span style=\"color: #006633;\">apache</span>.<span style=\"color: #006633;\">hadoop</span>.<span
    style=\"color: #006633;\">hive</span>.<span style=\"color: #006633;\">ql</span>.<span
    style=\"color: #006633;\">exec</span>.<span style=\"color: #006633;\">FetchOperator</span>.<span
    style=\"color: #006633;\">pushRow</span><span style=\"color: #009900;\">&#40;</span>FetchOperator.<span
    style=\"color: #006633;\">java</span><span style=\"color: #339933;\">:</span><span
    style=\"color: #cc66cc;\">546</span><span style=\"color: #009900;\">&#41;</span>\nat
    org.<span style=\"color: #006633;\">apache</span>.<span style=\"color: #006633;\">hadoop</span>.<span
    style=\"color: #006633;\">hive</span>.<span style=\"color: #006633;\">ql</span>.<span
    style=\"color: #006633;\">exec</span>.<span style=\"color: #006633;\">FetchTask</span>.<span
    style=\"color: #006633;\">fetch</span><span style=\"color: #009900;\">&#40;</span>FetchTask.<span
    style=\"color: #006633;\">java</span><span style=\"color: #339933;\">:</span><span
    style=\"color: #cc66cc;\">138</span><span style=\"color: #009900;\">&#41;</span>\nat
    org.<span style=\"color: #006633;\">apache</span>.<span style=\"color: #006633;\">hadoop</span>.<span
    style=\"color: #006633;\">hive</span>.<span style=\"color: #006633;\">ql</span>.<span
    style=\"color: #003399;\">Driver</span>.<span style=\"color: #006633;\">getResults</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #003399;\">Driver</span>.<span
    style=\"color: #006633;\">java</span><span style=\"color: #339933;\">:</span><span
    style=\"color: #cc66cc;\">1595</span><span style=\"color: #009900;\">&#41;</span>\nat
    org.<span style=\"color: #006633;\">apache</span>.<span style=\"color: #006633;\">hadoop</span>.<span
    style=\"color: #006633;\">hive</span>.<span style=\"color: #006633;\">cli</span>.<span
    style=\"color: #006633;\">CliDriver</span>.<span style=\"color: #006633;\">processLocalCmd</span><span
    style=\"color: #009900;\">&#40;</span>CliDriver.<span style=\"color: #006633;\">java</span><span
    style=\"color: #339933;\">:</span><span style=\"color: #cc66cc;\">285</span><span
    style=\"color: #009900;\">&#41;</span>\nat org.<span style=\"color: #006633;\">apache</span>.<span
    style=\"color: #006633;\">hadoop</span>.<span style=\"color: #006633;\">hive</span>.<span
    style=\"color: #006633;\">cli</span>.<span style=\"color: #006633;\">CliDriver</span>.<span
    style=\"color: #006633;\">processCmd</span><span style=\"color: #009900;\">&#40;</span>CliDriver.<span
    style=\"color: #006633;\">java</span><span style=\"color: #339933;\">:</span><span
    style=\"color: #cc66cc;\">220</span><span style=\"color: #009900;\">&#41;</span>\nat
    org.<span style=\"color: #006633;\">apache</span>.<span style=\"color: #006633;\">hadoop</span>.<span
    style=\"color: #006633;\">hive</span>.<span style=\"color: #006633;\">cli</span>.<span
    style=\"color: #006633;\">CliDriver</span>.<span style=\"color: #006633;\">processLine</span><span
    style=\"color: #009900;\">&#40;</span>CliDriver.<span style=\"color: #006633;\">java</span><span
    style=\"color: #339933;\">:</span><span style=\"color: #cc66cc;\">423</span><span
    style=\"color: #009900;\">&#41;</span>\nat org.<span style=\"color: #006633;\">apache</span>.<span
    style=\"color: #006633;\">hadoop</span>.<span style=\"color: #006633;\">hive</span>.<span
    style=\"color: #006633;\">cli</span>.<span style=\"color: #006633;\">CliDriver</span>.<span
    style=\"color: #006633;\">executeDriver</span><span style=\"color: #009900;\">&#40;</span>CliDriver.<span
    style=\"color: #006633;\">java</span><span style=\"color: #339933;\">:</span><span
    style=\"color: #cc66cc;\">792</span><span style=\"color: #009900;\">&#41;</span>\nat
    org.<span style=\"color: #006633;\">apache</span>.<span style=\"color: #006633;\">hadoop</span>.<span
    style=\"color: #006633;\">hive</span>.<span style=\"color: #006633;\">cli</span>.<span
    style=\"color: #006633;\">CliDriver</span>.<span style=\"color: #006633;\">run</span><span
    style=\"color: #009900;\">&#40;</span>CliDriver.<span style=\"color: #006633;\">java</span><span
    style=\"color: #339933;\">:</span><span style=\"color: #cc66cc;\">686</span><span
    style=\"color: #009900;\">&#41;</span>\nat org.<span style=\"color: #006633;\">apache</span>.<span
    style=\"color: #006633;\">hadoop</span>.<span style=\"color: #006633;\">hive</span>.<span
    style=\"color: #006633;\">cli</span>.<span style=\"color: #006633;\">CliDriver</span>.<span
    style=\"color: #006633;\">main</span><span style=\"color: #009900;\">&#40;</span>CliDriver.<span
    style=\"color: #006633;\">java</span><span style=\"color: #339933;\">:</span><span
    style=\"color: #cc66cc;\">625</span><span style=\"color: #009900;\">&#41;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">Exception in thread &quot;main&quot;
    java.lang.NoClassDefFoundError: org/apache/solr/client/solrj/SolrServerException\r\nat
    com.aexp.ims.atworks.hive.solr.SolrSplit.getSplits(SolrSplit.java:84)\r\nat com.aexp.ims.atworks.hive.solr.SolrInputFormat.getSplits(SolrInputFormat.java:91)\r\nat
    org.apache.hadoop.hive.ql.exec.FetchOperator.getRecordReader(FetchOperator.java:419)\r\nat
    org.apache.hadoop.hive.ql.exec.FetchOperator.getNextRow(FetchOperator.java:573)\r\nat
    org.apache.hadoop.hive.ql.exec.FetchOperator.pushRow(FetchOperator.java:546)\r\nat
    org.apache.hadoop.hive.ql.exec.FetchTask.fetch(FetchTask.java:138)\r\nat org.apache.hadoop.hive.ql.Driver.getResults(Driver.java:1595)\r\nat
    org.apache.hadoop.hive.cli.CliDriver.processLocalCmd(CliDriver.java:285)\r\nat
    org.apache.hadoop.hive.cli.CliDriver.processCmd(CliDriver.java:220)\r\nat org.apache.hadoop.hive.cli.CliDriver.processLine(CliDriver.java:423)\r\nat
    org.apache.hadoop.hive.cli.CliDriver.executeDriver(CliDriver.java:792)\r\nat org.apache.hadoop.hive.cli.CliDriver.run(CliDriver.java:686)\r\nat
    org.apache.hadoop.hive.cli.CliDriver.main(CliDriver.java:625)</p></div>\n\";i:3;s:381:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n</pre></td><td
    class=\"code\"><pre class=\"unix\" style=\"font-family:monospace;\">hive --auxpath
    /xxx/solr-solrj-5.2.1.jar, /xxx/httpclient-4.5.1.jar</pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">hive --auxpath /xxx/solr-solrj-5.2.1.jar,
    /xxx/httpclient-4.5.1.jar</p></div>\n\";}"
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/hive-noclassdeffounderror-auxiliary-path-issue/"
---
Hive NoClassDefFoundError error auxiliary path issue is very common. Sometimes even you add jar into classpath using below hive command, hive throws NoClassDefFound error-

```
add jar /xxx/hive-customserde.jar; add jar /xxx/solr-solrj.jar;
```

Above commands will add resource to hive class path but suppose your custom library has a dependency on other jar then you need to do some work around to resolve class path issue. My custom serde is dependent on Solr libraries and jar file is already added to class path but still it is not getting reflected to class path.  
Exception trace-

```
Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/solr/client/solrj/SolrServerException at com.aexp.ims.atworks.hive.solr.SolrSplit.getSplits(SolrSplit.java:84) at com.aexp.ims.atworks.hive.solr.SolrInputFormat.getSplits(SolrInputFormat.java:91) at org.apache.hadoop.hive.ql.exec.FetchOperator.getRecordReader(FetchOperator.java:419) at org.apache.hadoop.hive.ql.exec.FetchOperator.getNextRow(FetchOperator.java:573) at org.apache.hadoop.hive.ql.exec.FetchOperator.pushRow(FetchOperator.java:546) at org.apache.hadoop.hive.ql.exec.FetchTask.fetch(FetchTask.java:138) at org.apache.hadoop.hive.ql.Driver.getResults(Driver.java:1595) at org.apache.hadoop.hive.cli.CliDriver.processLocalCmd(CliDriver.java:285) at org.apache.hadoop.hive.cli.CliDriver.processCmd(CliDriver.java:220) at org.apache.hadoop.hive.cli.CliDriver.processLine(CliDriver.java:423) at org.apache.hadoop.hive.cli.CliDriver.executeDriver(CliDriver.java:792) at org.apache.hadoop.hive.cli.CliDriver.run(CliDriver.java:686) at org.apache.hadoop.hive.cli.CliDriver.main(CliDriver.java:625)
```

Solution is you need to add dependent libraries to Hive auxiliary path. Use below command to add libraries to hive aux path-

```
hive --auxpath /xxx/solr-solrj-5.2.1.jar, /xxx/httpclient-4.5.1.jar
```

If you still face any class path issue then post your queries in comment :)

