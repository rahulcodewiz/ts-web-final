---
layout: post
title: Hbase tips and tricks
date: 2014-10-08 20:13:54.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Big Data
tags:
- bigdata
- hbase
meta:
  _edit_last: '1'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: Hbase tips and tricks
  _yoast_wpseo_title: Hbase tips and tricks
  _yoast_wpseo_metadesc: Hbase tips and tricks, avoid full table scan, set hbase history
    file, unset client block fache. Count Hbase rows, Scan command with RowFilter
  _yoast_wpseo_linkdex: '78'
  dsq_thread_id: '3097142015'
  wp-syntax-cache-content: "a:7:{i:1;s:1259:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"code\"><pre class=\"powershell\" style=\"font-family:monospace;\">more
    ~<span style=\"color: pink;\">/</span>.irbrc\nrequire <span style=\"color: #800000;\">'irb/ext/save-history'</span>\nIRB.conf<span
    style=\"color: #000000;\">&#91;</span>:SAVE_HISTORY<span style=\"color: #000000;\">&#93;</span>
    <span style=\"color: pink;\">=</span> <span style=\"color: #804000;\">100</span>\nIRB.conf<span
    style=\"color: #000000;\">&#91;</span>:HISTORY_FILE<span style=\"color: #000000;\">&#93;</span>
    <span style=\"color: pink;\">=</span> <span style=\"color: #800000;\">&quot;#{ENV['HOME']}/.irb_history&quot;</span>\nKernel.at_exit
    <span style=\"color: #0000FF;\">do</span>\n    IRB.conf<span style=\"color: #000000;\">&#91;</span>:AT_EXIT<span
    style=\"color: #000000;\">&#93;</span>.each <span style=\"color: #0000FF;\">do</span>
    <span style=\"color: pink;\">|</span>i<span style=\"color: pink;\">|</span>\n
    \       i.call\n    end\nend</pre></td></tr></table><p class=\"theCode\" style=\"display:none;\">more
    ~/.irbrc\r\nrequire 'irb/ext/save-history'\r\nIRB.conf[:SAVE_HISTORY] = 100\r\nIRB.conf[:HISTORY_FILE]
    = &quot;#{ENV['HOME']}/.irb_history&quot;\r\nKernel.at_exit do\r\n    IRB.conf[:AT_EXIT].each
    do |i|\r\n        i.call\r\n    end\r\nend</p></div>\n\";i:2;s:424:\"\n<div class=\"wp_syntax\"
    style=\"position:relative;\"><table><tr><td class=\"code\"><pre class=\"powershell\"
    style=\"font-family:monospace;\">hbase<span style=\"color: pink;\">&gt;</span>debug\nor\n.<span
    style=\"color: pink;\">/</span>bin<span style=\"color: pink;\">/</span>hbase shell
    <span style=\"color: pink;\">-</span>d</pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">hbase&gt;debug\r\nor\r\n./bin/hbase shell -d</p></div>\n\";i:3;s:1990:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"code\"><pre
    class=\"powershell\" style=\"font-family:monospace;\">hbase<span style=\"color:
    #000000;\">&#40;</span>main<span style=\"color: #000000;\">&#41;</span>:001:<span
    style=\"color: #804000;\">0</span><span style=\"color: pink;\">&gt;</span> create
    <span style=\"color: #800000;\">'account'</span><span style=\"color: pink;\">,</span>
    <span style=\"color: #800000;\">'id'</span>\n<span style=\"color: #804000;\">0</span>
    row<span style=\"color: #000000;\">&#40;</span>s<span style=\"color: #000000;\">&#41;</span>
    <span style=\"color: #0000FF;\">in</span> <span style=\"color: #804000;\">1.1930</span>
    seconds\nhbase<span style=\"color: #000000;\">&#40;</span>main<span style=\"color:
    #000000;\">&#41;</span>:002:<span style=\"color: #804000;\">0</span><span style=\"color:
    pink;\">&gt;</span> incr <span style=\"color: #800000;\">'account'</span><span
    style=\"color: pink;\">,</span> <span style=\"color: #800000;\">'2014'</span><span
    style=\"color: pink;\">,</span> <span style=\"color: #800000;\">'id:n'</span><span
    style=\"color: pink;\">,</span> <span style=\"color: #804000;\">1</span>\nCOUNTER
    VALUE <span style=\"color: pink;\">=</span> <span style=\"color: #804000;\">1</span>\nhbase<span
    style=\"color: #000000;\">&#40;</span>main<span style=\"color: #000000;\">&#41;</span>:04:<span
    style=\"color: #804000;\">0</span><span style=\"color: pink;\">&gt;</span> get_counter
    <span style=\"color: #800000;\">'account'</span><span style=\"color: pink;\">,</span>
    <span style=\"color: #800000;\">'2014'</span><span style=\"color: pink;\">,</span>
    <span style=\"color: #800000;\">'id:n'</span>\nCOUNTER VALUE <span style=\"color:
    pink;\">=</span> <span style=\"color: #804000;\">2</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">hbase(main):001:0&gt; create 'account',
    'id'\r\n0 row(s) in 1.1930 seconds\r\nhbase(main):002:0&gt; incr 'account', '2014',
    'id:n', 1\r\nCOUNTER VALUE = 1\r\nhbase(main):04:0&gt; get_counter 'account',
    '2014', 'id:n'\r\nCOUNTER VALUE = 2</p></div>\n\";i:4;s:350:\"\n<div class=\"wp_syntax\"
    style=\"position:relative;\"><table><tr><td class=\"code\"><pre class=\"powershell\"
    style=\"font-family:monospace;\">create <span style=\"color: #800000;\">'TS'</span><span
    style=\"color: pink;\">,</span><span style=\"color: #800000;\">'cf'</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">create 'TS','cf'</p></div>\n\";i:5;s:1107:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n</pre></td><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\">Scan scan
    <span style=\"color: #339933;\">=</span> <span style=\"color: #000000; font-weight:
    bold;\">new</span> Scan<span style=\"color: #009900;\">&#40;</span>Bytes.<span
    style=\"color: #006633;\">ToBytes</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;23989&quot;</span><span style=\"color: #009900;\">&#41;</span>,Bytes.<span
    style=\"color: #006633;\">toBytes</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;23989~&quot;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\nscan.<span style=\"color: #006633;\">setFilter</span><span
    style=\"color: #009900;\">&#40;</span>...<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span></pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">Scan scan = new Scan(Bytes.ToBytes(&quot;23989&quot;),Bytes.toBytes(&quot;23989~&quot;);\r\nscan.setFilter(...);</p></div>\n\";i:6;s:1791:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n3\n4\n</pre></td><td
    class=\"code\"><pre class=\"powershell\" style=\"font-family:monospace;\">import
    org.apache.hadoop.hbase.<span style=\"color: #0000FF;\">filter</span>.CompareFilter\nimport
    org.apache.hadoop.hbase.<span style=\"color: #0000FF;\">filter</span>.RowFilter\nimport
    org.apache.hadoop.hbase.<span style=\"color: #0000FF;\">filter</span>.SubstringComparator\nscan
    <span style=\"color: #800000;\">'TS'</span><span style=\"color: pink;\">,</span>
    <span style=\"color: #000000;\">&#123;</span>STARTROW<span style=\"color: pink;\">=&gt;</span><span
    style=\"color: #800000;\">'23989'</span><span style=\"color: pink;\">,</span>
    STOPROW<span style=\"color: pink;\">=&gt;</span><span style=\"color: #800000;\">'23989~'</span><span
    style=\"color: pink;\">,</span><span style=\"color: #0000FF;\">FILTER</span><span
    style=\"color: pink;\">=&gt;</span>RowFilter.new<span style=\"color: #000000;\">&#40;</span>CompareFilter::CompareOp.valueOf<span
    style=\"color: #000000;\">&#40;</span><span style=\"color: #800000;\">'EQUAL'</span><span
    style=\"color: #000000;\">&#41;</span><span style=\"color: pink;\">,</span>SubstringComparator.new<span
    style=\"color: #000000;\">&#40;</span><span style=\"color: #800000;\">'23989'</span><span
    style=\"color: #000000;\">&#41;</span><span style=\"color: #000000;\">&#41;</span><span
    style=\"color: #000000;\">&#125;</span></pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">import org.apache.hadoop.hbase.filter.CompareFilter\r\nimport
    org.apache.hadoop.hbase.filter.RowFilter\r\nimport org.apache.hadoop.hbase.filter.SubstringComparator\r\nscan
    'TS', {STARTROW=&gt;'23989', STOPROW=&gt;'23989~',FILTER=&gt;RowFilter.new(CompareFilter::CompareOp.valueOf('EQUAL'),SubstringComparator.new('23989'))}</p></div>\n\";i:7;s:602:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n</pre></td><td
    class=\"code\"><pre class=\"powershell\" style=\"font-family:monospace;\">count
    <span style=\"color: #800000;\">'TS'</span><span style=\"color: pink;\">,</span>
    \ INTERVAL <span style=\"color: pink;\">=&gt;</span> <span style=\"color: #804000;\">10000</span><span
    style=\"color: pink;\">,</span> CACHE <span style=\"color: pink;\">=&gt;</span>
    <span style=\"color: #804000;\">1000</span></pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">count 'TS',  INTERVAL =&gt; 10000, CACHE =&gt; 1000</p></div>\n\";}"
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/hbase-scan-filters-tips-tricks/"
---
 **Hbase tips and tricks**

1. irbrc file-irbrc configuration to save all command history of all hbase shell invocations.

minimal configuration of irbrc-

```
more ~/.irbrc require 'irb/ext/save-history' IRB.conf[:SAVE\_HISTORY] = 100 IRB.conf[:HISTORY\_FILE] = "#{ENV['HOME']}/.irb\_history" Kernel.at\_exit do IRB.conf[:AT\_EXIT].each do |i| i.call end end
```
2. enable debugging level

```
hbase\>debug or ./bin/hbase shell -d
```
3. counters with hbase- hbase offers counter feature, counters are very useful in statistics

```
hbase(main):001:0\> create 'account', 'id' 0 row(s) in 1.1930 seconds hbase(main):002:0\> incr 'account', '2014', 'id:n', 1 COUNTER VALUE = 1 hbase(main):04:0\> get\_counter 'account', '2014', 'id:n' COUNTER VALUE = 2
```
4. scan query optimization

Scan is used to get the data from hbase and the costliest operation.  
An optional startRow and stopRow is useful to improve the query performance.If rows are not defined(start and stop), the Scanner will iterate over all rows.  
Hbase scan queries with start and end key are much faster because, it doesn't have to scan everything to get the specified query/filter data.  
Here is tricks-

- create hbase table and populate data-

```
create 'TS','cf'
```

| <font color="#000000">row id</font> | <font color="#000000">cf:desc</font> |
| <font color="#000000">card_number_year_month_day_time_o</font> | <font color="#000000">transaction_amt</font> | <font color="#000000"> location </font> | <font color="#000000">type</font> | <font color="#000000">year </font> | <font color="#000000">month</font> |
| <font color="#000000">100_2014_06_10_10_932845_ta</font> | <font color="#000000">100</font> | <font color="#000000">bangalore</font> | <font color="#000000">credit</font> | <font color="#000000">2014</font> | <font color="#000000">6</font> |
| <font color="#000000">23989_2000_01_11_10_5468756_ta</font> | <font color="#000000">45843745</font> | <font color="#000000">bangalore india</font> | <font color="#000000">debit</font> | <font color="#000000">2000</font> | <font color="#000000">5</font> |
| <font color="#000000">487545_2000_01_11_10_5468756_ta</font> | <font color="#000000"><br></font> | <font color="#000000"><br></font> | <font color="#000000"><br></font> | <font color="#000000">2000</font> | <font color="#000000">1</font> |

- Avoid Full Table Scan-

find out all transaction done by card number x at place bangalore.  
use prefix/rowkey filter with regex/substring comparator to set the search condition and set the start row as 'X' and stop row 'X~'.  
Row keys are sorted(lexical) and data is stored in byte in hbase. The start/stop key helps to avoid the complete table scan and fetch the data from region contains the range value, as(~) is last in ascii table so hbase scan lookup the rows having prefix X~.  
Retrieving data from HBase scan with filter-

```
Scan scan = new Scan(Bytes.ToBytes("23989"),Bytes.toBytes("23989~"); scan.setFilter(...);
```
- Disable cache at client-

setCacheBlocks(false)  
and setCaching(0)

- Get all the row having account number **23989**

```
import org.apache.hadoop.hbase.filter.CompareFilter import org.apache.hadoop.hbase.filter.RowFilter import org.apache.hadoop.hbase.filter.SubstringComparator scan 'TS', {STARTROW=\>'23989', STOPROW=\>'23989~',FILTER=\>RowFilter.new(CompareFilter::CompareOp.valueOf('EQUAL'),SubstringComparator.new('23989'))}
```

Use start and stop row to optimize scan query.

- Count all row

```
count 'TS', INTERVAL =\> 10000, CACHE =\> 1000
```

decrease CACHE value if row is very large.

