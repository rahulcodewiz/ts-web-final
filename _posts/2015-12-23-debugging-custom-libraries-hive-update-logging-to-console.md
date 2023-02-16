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
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/debugging-custom-libraries-hive-update-logging-to-console/"
---
 
# Debugging custom libraries hive update logging to console

For Data Engineers its common scenario when they would want to explore how `Hive` translate the `SQL` command to execution and troubleshoot the error. By default Hive cli the root log level is error which isn't sufficient for troubleshooting and you can set it to DEBUG or INFO to get the detailed logs on console-

```bash
hive --hiveconf hive.root.logger=<info>,console
</info>
```

You can also check job tracker for detailed log-

```
http://jobtracker:<job tracker port e.g.>/jobdetails.jsp?jobid=<job id> then go to map or reduce and browse logs</job></job>
```
