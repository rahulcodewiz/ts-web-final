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
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/hbase-scan-filters-tips-tricks/"
---
# Hbase tips and tricks: Maximizing Performance and Efficiency

When it comes to handling big data, HBase stands out as a powerful NoSQL database for handling vast amounts of information. As you delve deeper into the world of HBase, there are numerous tips and tricks that can enhance your experience, save time, and optimize performance. In this post, I will share some of the useful HBase tips and tricks to help you make the most out of this robust database.

1. History Preservation with irbrc

If you frequently use the HBase shell, it can be helpful to maintain a record of your command history. The irbrc file configuration allows you to save all command history for HBase shell invocations, ensuring that you can review and reuse your previous commands easily.

Here's a minimal configuration for your irbrc file:

```ruby
require 'irb/ext/save-history'
IRB.conf[:SAVE_HISTORY] = 100
IRB.conf[:HISTORY_FILE] = "#{ENV['HOME']}/.irb_history"
Kernel.at_exit do
  IRB.conf[:AT_EXIT].each do |i|
    i.call
  end
end
```

2. Enable Debugging for Insight

For debugging purposes, you can enable the debugging level in the HBase shell. This feature can help you trace and identify issues with command.

```
hbase\>debug 

or 

./bin/hbase shell -d
```


3. Leveraging Counters for Statistics

HBase offers a counter feature, it allow you to keep track of various metrics, and you can increment or retrieve counter values with ease. Here's a quick example:

```bash
hbase(main):001:0\> create 'account', 'id' 
0 row(s) in 1.1930 seconds 
hbase(main):002:0\> incr 'account', '2014', 'id:n', 1 COUNTER VALUE = 1 
hbase(main):04:0\> get_counter 'account', '2014', 'id:n' COUNTER VALUE = 2
```

4. Scan Query Optimization

Scans are often used to retrieve data from HBase. However, performing a scan without proper optimization can be resource-intensive. To enhance the performance of scan queries, consider the following tricks:

- create hbase table and populate data-

```bash
create 'TS','cf'
```

| row id| cf:desc|
--- | --- |
| card_number_year_month_day_time_o| transaction_amt|  location | type| year | month|
| 100_2014_06_10_10_932845_ta| 100| bangalore| credit| 2014| 6|
| 23989_2000_01_11_10_5468756_ta| 45843745| bangalore india| debit| 2000| 5|
| 487545_2000_01_11_10_5468756_ta| | | >| 2000| 1|


- Avoid Full Table Scan-

find out all transaction done by card number x at place bangalore.  
use prefix/rowkey filter with regex/substring comparator to set the search condition and set the start row as 'X' and stop row 'X~'.  
Row keys are sorted(lexical) and data is stored in byte in hbase. The start/stop key helps to avoid the complete table scan and fetch the data from region contains the range value, as(~) is last in ascii table so hbase scan lookup the rows having prefix X~.  
Retrieving data from HBase scan with filter-

```bash
Scan scan = new Scan(Bytes.ToBytes("23989"),Bytes.toBytes("23989~"); scan.setFilter(...);
```
- Disable cache at client-

setCacheBlocks(false)  
and setCaching(0)

- Get all the row having account number **23989**

```bash
import org.apache.hadoop.hbase.filter.CompareFilter 
import org.apache.hadoop.hbase.filter.RowFilter 
import org.apache.hadoop.hbase.filter.SubstringComparator scan 'TS', {STARTROW=\>'23989', STOPROW=\>'23989~',FILTER=\>RowFilter.new(CompareFilter::CompareOp.valueOf('EQUAL'),SubstringComparator.new('23989'))}
```

Use start and stop row to optimize scan query.

5. Count all row

```
count 'TS', INTERVAL =\> 10000, CACHE =\> 1000
```

Decrease the CACHE value if row is very large.


These strategies will help you make the most of this powerful NoSQL database, whether you're working with large-scale data analysis, statistics, or any other use case. I hope this was helpful.