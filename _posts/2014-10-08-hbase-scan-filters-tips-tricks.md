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
## Hbase tips and tricks

 This post shares the useful tips and tricks for the Hbase-

1. irbrc file-irbrc configuration to save all command history of all hbase shell invocations.

Minimal configuration of irbrc-

```
more ~/.irbrc require 'irb/ext/save-history' IRB.conf[:SAVE\_HISTORY] = 100 IRB.conf[:HISTORY\_FILE] = "#{ENV['HOME']}/.irb\_history" Kernel.at\_exit do IRB.conf[:AT\_EXIT].each do |i| i.call end end
```
2. Enable debugging level

```
hbase\>debug or ./bin/hbase shell -d
```
3. counters with hbase- hbase offers counter feature, counters are very useful in statistics

```bash
hbase(main):001:0\> create 'account', 'id' 
0 row(s) in 1.1930 seconds 
hbase(main):002:0\> incr 'account', '2014', 'id:n', 1 COUNTER VALUE = 1 
hbase(main):04:0\> get_counter 'account', '2014', 'id:n' COUNTER VALUE = 2
```
4. How to optimize Scan query optimization

Scan is used to get the data from hbase and the costliest operation.  An optional startRow and stopRow is useful to improve the query performance. If rows are not defined(start and stop), the Scanner will iterate over all rows.  
Hbase scan queries with start and end key are much faster because, it doesn't have to scan everything to get the specified query/filter data.  

Here is tricks-

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