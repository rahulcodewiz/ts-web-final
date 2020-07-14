---
layout: post
title: 'UNIX: Zombie processes'
date: 2014-09-29 13:04:12.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Build &amp; Release
tags:
- UNIX
- Zombie
meta:
  _edit_last: '3'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: unix zombie processes
  _yoast_wpseo_metadesc: 'UNIX: Zombie processes'
  _yoast_wpseo_linkdex: '64'
  dsq_thread_id: '3067599179'
  wp-syntax-cache-content: "a:4:{i:1;s:584:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"code\"><pre class=\"powershell\" style=\"font-family:monospace;\">$ <span
    style=\"color: #008080; font-weight: bold;\">ps</span> aux <span style=\"color:
    pink;\">|</span> awk <span style=\"color: #800000;\">'{print $2, $8}'</span> <span
    style=\"color: pink;\">|</span> grep <span style=\"color: pink;\">-</span>w <span
    style=\"color: #800000;\">'Z'</span>\n<span style=\"color: #804000;\">7963</span>
    Z</pre></td></tr></table><p class=\"theCode\" style=\"display:none;\">$ ps aux
    | awk '{print $2, $8}' | grep -w 'Z'\r\n7963 Z</p></div>\n\";i:2;s:402:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"code\"><pre
    class=\"powershell\" style=\"font-family:monospace;\">$ <span style=\"color: #008080;
    font-weight: bold;\">kill</span> <span style=\"color: pink;\">-</span><span style=\"color:
    #804000;\">9</span> <span style=\"color: #804000;\">7963</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">$ kill -9 7963</p></div>\n\";i:3;s:662:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"code\"><pre
    class=\"powershell\" style=\"font-family:monospace;\">$ <span style=\"color: #008080;
    font-weight: bold;\">kill</span> <span style=\"color: pink;\">-</span><span style=\"color:
    #804000;\">9</span> $<span style=\"color: #000000;\">&#40;</span><span style=\"color:
    #008080; font-weight: bold;\">ps</span> aux <span style=\"color: pink;\">|</span>
    awk <span style=\"color: #800000;\">'$8 == &quot;Z&quot; {print $2}'</span><span
    style=\"color: #000000;\">&#41;</span></pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">$ kill -9 $(ps aux | awk '$8 == &quot;Z&quot; {print $2}')</p></div>\n\";i:4;s:453:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"code\"><pre
    class=\"powershell\" style=\"font-family:monospace;\">$ <span style=\"color: #008080;
    font-weight: bold;\">ps</span> aux <span style=\"color: pink;\">|</span> awk <span
    style=\"color: #800000;\">'$8 == &quot;Z&quot; || NR == 1 {print $0}'</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">$ ps aux | awk '$8 == &quot;Z&quot;
    || NR == 1 {print $0}'</p></div>\n\";}"
author:
  login: Nikhil
  email: coolnicks.nikhil@gmail.com
  name: Nikhil
  display_name: Nikhil Gupta
  first_name: Nikhil
  last_name: Gupta
permalink: "/br/unix-zombie-processes/"
---
In this part I am going to answer below questions regarding zombie process

- What are zombie process?
- Why do it exist in unix?
- Will it occupy memory and resources?
- How to view a zombie process and kill it?

There are 2 types of processes : Zombie and Orphan Processes

1. **Orphan Processes:**  
Normally, when a child process is killed, the parent process is told via a SIGCHLD signal. Then the parent can do some other task or restart a new child as needed. However, sometimes the parent process is killed before its child is killed. In this case, the "parent of all processes," init process, becomes the new PPID (parent process ID). Sometime these processes are called orphan process.
2. **Zombie Processes:**  
When a process is killed, a ps listing may still show the process with a Z state. This is a zombie, or defunct, process. The process is dead and not being used. These processes are different from orphan processes.They are the processes that has completed execution but still has an entry in the process table.

**To find the Zombie process:**

&nbsp;

```
$ ps aux | awk '{print $2, $8}' | grep -w 'Z' 7963 Z
```

It will give you process ID then you can kill the process.

```
$ kill -9 7963
```

Or you can use one liner:

```
$ kill -9 $(ps aux | awk '$8 == "Z" {print $2}')
```

Resources and memory:

I checked in my system and it is showing 0% CPU and memory use.

```
$ ps aux | awk '$8 == "Z" || NR == 1 {print $0}'
```

USER PID %CPU %MEM VSZ RSS TTY STAT START TIME COMMAND  
root 7963 0.0 0.0 0 0 ? Z Apr16 0:00 [modprobe]

Resources and Memory allocated to a process are deallocated when it killed so they can be used by other processes. However, the process's entry in the process table remains

