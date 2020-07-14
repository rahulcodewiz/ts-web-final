---
layout: post
title: Debugging custom libraries hive update logging to console
date: 2015-12-23 00:05:17.000000000 -08:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Big Data
- hive
tags:
- bigdata
- hive
- java
meta:
  _edit_last: '1'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: Debugging custom libraries hive update logging to console
  _yoast_wpseo_title: Debugging custom libraries hive update logging to console
  _yoast_wpseo_metadesc: Debugging custom libraries hive update logging to console
  _yoast_wpseo_linkdex: '56'
  dsq_thread_id: '4657893272'
  wp-syntax-cache-content: |-
    a:2:{i:1;s:322:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="unix" style="font-family:monospace;">hive --hiveconf hive.root.logger=&lt;INFO|DEBUG&gt;,console</pre></td></tr></table><p class="theCode" style="display:none;">hive --hiveconf hive.root.logger=&lt;INFO|DEBUG&gt;,console</p></div>
    ";i:2;s:464:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="html" style="font-family:monospace;">http://jobtracker:&lt;job tracker port e.g. 50030&gt;/jobdetails.jsp?jobid=&lt;job id&gt; then go to map or reduce and browse logs</pre></td></tr></table><p class="theCode" style="display:none;">http://jobtracker:&lt;job tracker port e.g. 50030&gt;/jobdetails.jsp?jobid=&lt;job id&gt; then go to map or reduce and browse logs</p></div>
    ";}
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/debugging-custom-libraries-hive-update-logging-to-console/"
---
 **Debugging custom libraries hive update logging to console**.  
When launch Hive cli change logging set root logging or your library logging to DEBUG or INFO and print to console-

```
hive --hiveconf hive.root.logger=<info>,console
</info>
```

Check Mapreduce jobs logs-

```
http://jobtracker:<job tracker port e.g.>/jobdetails.jsp?jobid=<job id> then go to map or reduce and browse logs</job></job>
```
