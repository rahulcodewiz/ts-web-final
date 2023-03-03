---
layout: post
title: How to detect a memory leak
date: 2014-09-24 11:34:51.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Performance Testing
tags:
- memory leak
meta:
  _edit_last: '2'
  _layout: inherit
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: memory leak
  _yoast_wpseo_metadesc: Finding memory leaks is all about identifying objects that
    are created but never garbage collected. Memory leaks always get worse so, in
    theory, the longer
  _yoast_wpseo_linkdex: '81'
  dsq_thread_id: '4075630279'
author:
  login: ceekay
  email: ceekay.chandrakant88@gmail.com
  name: Chandrakant
  display_name: Chandrakant Singh
  first_name: Chandrakant
  last_name: Singh
permalink: "/pt/how-to-detect-a-memory-leak/"
---
 ## How to detect a memory leak 

Finding memory leak is all about identifying objects that are created but never garbage collected. Memory leaks always get worse so, in theory, the longer the application runs, the bigger the leak will get, and the easier it will be to find.

You can identify a memory leak by running a load test on application for a prolonged duration of 10-12 hours and monitoring the memory utilization. That doesn't really help when profiling, though, because you need to be able to identify a leak quickly.

Profiling tools help leak detection by allowing you to take memory snapshots. A snapshot usually involves forcing a garbage collection and then recording all of the objects that are left behind in memory. Objects that repeatedly survive garbage collection should be investigated further.

If objects of the same type continually survive garbage collection and keep building up in memory, you need to investigate the references that are keeping those objects in memory. Tracking object references back to source code allows you to find the cause of the leak in your own code, which means you can fix it.

Some profilers track memory allocation by function calls, which allows you to see the functions that are potentially leaking memory. This can also be a highly effective technique for finding a memory leak.

