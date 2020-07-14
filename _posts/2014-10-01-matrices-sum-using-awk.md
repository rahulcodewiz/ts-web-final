---
layout: post
title: Matrices Sum using awk
date: 2014-10-01 07:44:18.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Build &amp; Release
tags:
- awk
- matrices
- UNIX
meta:
  _edit_last: '3'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: Matrices Sum using awk
  _yoast_wpseo_metadesc: Sum of Matrices using awk in one line
  _yoast_wpseo_linkdex: '68'
  dsq_thread_id: '3071474143'
  wp-syntax-cache-content: "a:1:{i:1;s:2491:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"code\"><pre class=\"powershell\" style=\"font-family:monospace;\">$ <span
    style=\"color: #008080; font-weight: bold;\">cat</span> f1\n<span style=\"color:
    #804000;\">1</span> <span style=\"color: #804000;\">1</span> <span style=\"color:
    #804000;\">1</span>\n<span style=\"color: #804000;\">1</span> <span style=\"color:
    #804000;\">1</span> <span style=\"color: #804000;\">1</span>\n<span style=\"color:
    #804000;\">1</span> <span style=\"color: #804000;\">1</span> <span style=\"color:
    #804000;\">1</span>\n$ <span style=\"color: #008080; font-weight: bold;\">cat</span>
    f2\n<span style=\"color: #804000;\">2</span> <span style=\"color: #804000;\">2</span>
    <span style=\"color: #804000;\">2</span>\n<span style=\"color: #804000;\">2</span>
    <span style=\"color: #804000;\">2</span> <span style=\"color: #804000;\">2</span>\n<span
    style=\"color: #804000;\">2</span> <span style=\"color: #804000;\">2</span> <span
    style=\"color: #804000;\">2</span>\n$ <span style=\"color: #008080; font-weight:
    bold;\">cat</span> f3\n<span style=\"color: #804000;\">3</span> <span style=\"color:
    #804000;\">3</span> <span style=\"color: #804000;\">3</span>\n<span style=\"color:
    #804000;\">3</span> <span style=\"color: #804000;\">3</span> <span style=\"color:
    #804000;\">3</span>\n<span style=\"color: #804000;\">3</span> <span style=\"color:
    #804000;\">3</span> <span style=\"color: #804000;\">3</span>\n$ awk <span style=\"color:
    #800000;\">'{for (i=1;i&amp;lt;=NF;i++) { arr[FNR,i] = arr[FNR,i] + $i; if(k &amp;lt;
    NF){k=NF} } } END { print &quot;Matrix Sum:&quot;; for(i=1;i&amp;lt;=FNR;i++)
    { for(j=1;j&amp;lt;=k;j++) { printf &quot;%s &quot;, arr[i,j] } print &quot;&quot;}}'</span>
    f1 f2 f3\nMatrix Sum:\n<span style=\"color: #804000;\">6</span> <span style=\"color:
    #804000;\">6</span> <span style=\"color: #804000;\">6</span>\n<span style=\"color:
    #804000;\">6</span> <span style=\"color: #804000;\">6</span> <span style=\"color:
    #804000;\">6</span>\n<span style=\"color: #804000;\">6</span> <span style=\"color:
    #804000;\">6</span> <span style=\"color: #804000;\">6</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">$ cat f1\r\n1 1 1\r\n1 1 1\r\n1 1 1\r\n$
    cat f2\r\n2 2 2\r\n2 2 2\r\n2 2 2\r\n$ cat f3\r\n3 3 3\r\n3 3 3\r\n3 3 3\r\n$
    awk '{for (i=1;i&amp;lt;=NF;i++) { arr[FNR,i] = arr[FNR,i] + $i; if(k &amp;lt;
    NF){k=NF} } } END { print &quot;Matrix Sum:&quot;; for(i=1;i&amp;lt;=FNR;i++)
    { for(j=1;j&amp;lt;=k;j++) { printf &quot;%s &quot;, arr[i,j] } print &quot;&quot;}}'
    f1 f2 f3\r\nMatrix Sum:\r\n6 6 6\r\n6 6 6\r\n6 6 6</p></div>\n\";}"
author:
  login: Nikhil
  email: coolnicks.nikhil@gmail.com
  name: Nikhil
  display_name: Nikhil Gupta
  first_name: Nikhil
  last_name: Gupta
permalink: "/br/matrices-sum-using-awk/"
---
Below program can provide sum of&nbsp;any number of matrices of any degree.

- &nbsp;Here, I am adding 3 matrices.
- Each matrix is stored in a file: 1 row in every line and columns are space separated.
- Each matrix is of 3x3. You can use it for matrix of any degree and it is not neessary that all the matrices will be of same degree 1.e. first one can be of 3x3, second one can be of 3x4 and so on.

&nbsp;

Below 3 files are containing row and column of each matrix.

```
$ cat f1 1 1 1 1 1 1 1 1 1 $ cat f2 2 2 2 2 2 2 2 2 2 $ cat f3 3 3 3 3 3 3 3 3 3 $ awk '{for (i=1;i\<=NF;i++) { arr[FNR,i] = arr[FNR,i] + $i; if(k \< NF){k=NF} } } END { print "Matrix Sum:"; for(i=1;i\<=FNR;i++) { for(j=1;j\<=k;j++) { printf "%s ", arr[i,j] } print ""}}' f1 f2 f3 Matrix Sum: 6 6 6 6 6 6 6 6 6
```

&nbsp;

Note: awk reads line by line

Here:

**NF** : Number of fields in cureent line which awk is reading

**FNR** : Line number of the current line being read of the file

**arr** : 2 dimensional array which will store the final sum of the matrices stored in file f1, f2 and f3

&nbsp;

Please feel free to contact in case of any doubt, suggestion.

