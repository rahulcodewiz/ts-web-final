---
layout: post
title: Hive Query Over Hbase
date: 2014-09-25 19:51:32.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Big Data
tags:
- hbase
- hive
meta:
  _edit_last: '1'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: Hive Query Over Hbase
  _yoast_wpseo_title: Hive Query Over Hbase
  _yoast_wpseo_metadesc: Hive Query Over Hbase .run hive query over hbase table.
  _yoast_wpseo_linkdex: '63'
  dsq_thread_id: '3068408754'
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/hive-query-over-hbase/"
---
Hive Query Over Hbase-

1- Launch the hbase shell-

hbase shell

2- Create employee table with column family 'cf'-

create 'employees', 'cf'

3- Load the sample data in employees table-

put 'employees','1001','cf:name','mike'

put 'employees','1001','cf:country','USA'

put 'employees','1002','cf:name','sky'

put 'employees','1002','cf:country','Canada'

put 'employees','1003','cf:name','sara'

put 'employees','1003','cf:country','aus'

4- Launch the hive cli & run below query-

CREATE EXTERNAL TABLE hbase\_employee(key STRING, name STRING,country STRING)

STORED BY 'org.apache.hadoop.hive.hbase.HBaseStorageHandler'

WITH SERDEPROPERTIES ("hbase.columns.mapping" = ":key,cf:name,cf:country")

TBLPROPERTIES ("hbase.table.name" = "employees");

5- Test query on Hive-

select country,count(\*) from hbase\_employee group by country;

In case you get Hbase classes Not found exception then add hbase jar to hiv aux path-

hive --auxpath ${HBASE\_HOME}/hbase-0.94.13.jar

