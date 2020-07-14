---
layout: post
title: Application Performance Tuning and Bottlenecks
date: 2014-09-24 11:30:54.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Performance Testing
tags: []
meta:
  _edit_last: '2'
  _layout: inherit
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: performance tuning
  _yoast_wpseo_metadesc: Below areas can be looked into for performance tuning an
    application:- 1. Wall-clock (elapsed) vs. CPU time 2. Resource bottlenecks 3.
    Call count 4. profil
  _yoast_wpseo_linkdex: '79'
  dsq_thread_id: '4064479752'
author:
  login: ceekay
  email: ceekay.chandrakant88@gmail.com
  name: Chandrakant
  display_name: Chandrakant Singh
  first_name: Chandrakant
  last_name: Singh
permalink: "/pt/application-performance-tuning-and-bottlenecks/"
---
 **Below areas can be looked into for performance tuning an application:-**

&nbsp;

1. **Wall-clock (elapsed) vs. CPU time**

A function may take a long time to execute, but use comparatively little CPU time because it is actually waiting for a database / web service call to return or for a thread synchronization lock to free up. Identifying Wait time can help you identify where your application may benefit from asynchronous processing.

At the same time, a CPU-intensive function is usually a good candidate for optimization, because the CPU is a finite resource and a potential bottleneck.

1. **Resource bottlenecks**

Resources such as disk space, network bandwidth, server availability, graphics cards, and shared threads can all create bottlenecks in an application. Identifying functions causing high levels of resource activity and contention is a key goal in profiling. This kind of activity, when scaled, could quickly become a problem and reduce the scalability of the application.

1. **Call count**

Function call count is the easiest statistic to look at first, because a non-trivial function with a high call count often indicates an immediate problem. It's always worth validating the origins of the high call count.

1. **Memory profiling**

The way you write your code directly impacts how and when the objects you create are allocated and destroyed. Get it right, and your application will use memory efficiently as needed, with minimal performance impact. Get it wrong, however, and your application could use more memory than necessary, which will cause the memory manager to work harder than it needs to, and this will directly impact performance.

Even worse than that, your application could just keep allocating memory until no more is left, causing the application or the machine to crash. This is the memory leak, which every developer fears.

Checking that an application doesn't have memory leaks, and that it uses memory efficiently, together with fixing any issues found, will improve its overall stability and performance.

1. **Garbage collection**

The Java/.NET memory management model ensures that any allocated objects which are no longer in use by the application will be reclaimed automatically. This relieves developers of the responsibility of having to free memory explicitly, which is something that was often omitted in native C/C++ applications, leading to memory leaks.

