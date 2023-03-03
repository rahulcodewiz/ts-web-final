---
layout: post
title: How to identify performance bottlenecks in Linux system
date: 2014-09-24 11:27:29.000000000 -07:00
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
  _yoast_wpseo_focuskw: performance bottlenecks in linux
  _yoast_wpseo_title: Identify performance bottlenecks in Linux system - TechSquids
  _yoast_wpseo_metadesc: Step by step guide to find performance bottlenecks in Linux
    system:- Run top command on the command line, Check the Load Average - If load
    average starts
  _yoast_wpseo_linkdex: '79'
  dsq_thread_id: '3074863248'
  _wp_old_slug: how-to-identify-performance-bottlenecks-in-a-linux-system
author:
  login: ceekay
  email: ceekay.chandrakant88@gmail.com
  name: Chandrakant
  display_name: Chandrakant Singh
  first_name: Chandrakant
  last_name: Singh
permalink: "/pt/performance-bottlenecks-in-linux/"
---
 **Step by step guide to find performance bottlenecks in Linux system:-**

- Run&nbsp; **top&nbsp;** command on the command line
- Check the Load Average

If load average starts increasing beyond a limit, it means that the number of processes in the queue starts increasing (see points to remember section below). Load average represents the average number of processes that have to wait for CPU time during the last 1, 5 or 15 minutes. High load is mostly because of 3 reasons -&nbsp;CPU bound load, load caused by out of memory issues and I/O-bound load

- Is the load CPU bound? Check the user (us) and system (sy) columns in the output of&nbsp; **top&nbsp;** command

If you find a high percentage in the user or system columns, there are good chances that your load is CPU-bound. To drill down to the root cause of it, scroll down a few lines to where top displays a list of current processes running on the system. By default, top will sort these based on the percentage of CPU used with the processes using the most on top. You may find the culprit processes which are utilizing most of your CPU time

- Is the load because of memory (RAM) issues? Run&nbsp; **vmstat** to calculate the free memory

**​​​Never conclude on the available memory just by looking at the 'free' column in the output of vmstat.&nbsp;** &nbsp;The available memory in Linux systems is used for caching and is governed by internal memory management system. To calculate the available memory - add the value in “free" and "cache" columns. If there is less amount of memory available in the system, it may start swapping and the performance will get impacted. To find the process consuming most of the RAM,&nbsp;go back to the same process output from top, and look in the %MEM column. By default, top will sort by the %CPU column, so simply type M and it will re-sort to show you which processes are using the highest percentage of RAM.

&nbsp;

- Is the load I/O bound? Run&nbsp; **iostat&nbsp;** command to look into the disk I/O statistics

Track down the issues related to disk partitions. I/O-bound load can be tricky to track down sometimes. As a matter of fact, if your system is swapping, it can make the load appear to be I/O-bound. Once you rule out swapping though, if you do have a high I/O wait, the next step is to attempt to track down which disk and partition is getting the bulk of the I/O traffic.&nbsp;Like with top, iostat gives you the CPU percentage output. Below that, it provides a breakdown of each drive and partition on your system and statistics for each:

The abbreviations used in iostat are described below :-

Tps- transactions per second  
Blk\_read/s- blocks read per second  
Blk\_wrtn/- blocks written per second  
Blk\_read- total blocks read  
Blk\_wrtn- total blocks written

By looking at these different values and comparing them to each other, ideally you will be able to find out first, which partition (or partitions) is getting the bulk of the I/O traffic, and second, whether the majority of that traffic is reads (Blk\_read/s) or writes (Blk\_wrtn/s). It can be tricky to track down the I/O related issues but these values will be helpful in identifying the process that is causing the load.

For instance, if you have an I/O-bound load and you suspect that your remote backup job might be the culprit, compare the read and write statistics. Because you know that a remote backup job is primarily going to read from your disk, if you see that the majority of the disk I/O is writes, you reasonably can assume it's not from the backup job. If, on the other hand, you do see a heavy amount of read I/O on a particular partition, you might run the lsof command and grep for that backup process and see whether it does in fact have some open file handles on that partition.

You can also try iotop tool (may not be there in your box, by default) to track down on which process is the I/O going on.

**Points to remember:-**

- The free memory displayed by&nbsp; **vmstat** is usually in KBs. This can be confirmed by using **&nbsp;sar -r** &nbsp;command
- Even if there is very less free memory shown in vmstat results, it does not indicate that there is a memory crunch in the system as Linux memory management automatically uses free memory for caching to improve performance.&nbsp;If there is enough free RAM available, the kernel tries to cache as many files as it can into RAM, if you access the file a second time, the kernel can retrieve it from RAM instead of the disk and give much better performance. The memory is taken back from the cached pool, if required by some process in the system. Look out for Si/So table in VMstat, as if there is any memory crunch in system, it will start reading/writing from/to disk
- 1 core can process Load Average of 1.0 with 100% utilization. Similarly dual core (2 core) system can process Load average of 1.0 with 50% utilization and load average of 2.0 with 100% utilization
- lsof is a command line utility which is used to list the information about the files that are opened by various processes. lsof will provide a list of all open files belonging to all active processes
