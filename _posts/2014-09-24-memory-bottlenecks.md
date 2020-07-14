---
layout: post
title: How to Pinpoint Memory bottlenecks
date: 2014-09-24 11:32:44.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Performance Testing
tags:
- memory leak
- Performance bottlenecks
meta:
  _edit_last: '2'
  _layout: inherit
  dsq_thread_id: '4075631094'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: memory bottlenecks
  _yoast_wpseo_metadesc: The basic symptoms of memory bottlenecks that affect application
    performance are - Memory leak, Excessive memory footprint, Inefficient allocation
    of memory
  _wp_old_slug: how-to-pinpoint-memory-related-performance-bottlenecks
  _yoast_wpseo_linkdex: '57'
author:
  login: ceekay
  email: ceekay.chandrakant88@gmail.com
  name: Chandrakant
  display_name: Chandrakant Singh
  first_name: Chandrakant
  last_name: Singh
permalink: "/pt/memory-bottlenecks/"
---
 **The basic symptoms of memory bottlenecks that affect application performance are -**

1. **Memory leak**

- Memory usage slowly increases over time
- Performance degrades
- Application will freeze/crash requiring a restart
- After restart application is running fine again, and the behavior continues

1. **Excessive memory footprint**

- Application is slow to load
- After load, other application runs slower than expected

1. **&nbsp;Inefficient allocation**

- Application performance suddenly degrades and then recovers quickly
- % Time in GC Statistic in PerfMon is greater than 20–30%
