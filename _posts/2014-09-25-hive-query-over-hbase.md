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
# Hive Query Over Hbase

Hive and HBase are two powerful technologies that, when combined, can provide a comprehensive solution for big data storage and analysis. In this blog post, we'll walk you through the process of executing Hive queries over HBase. This integration enables you to leverage Hive's SQL-like querying capabilities on top of HBase's NoSQL database. Let's get started with the step-by-step guide.

1. Launch the hbase shell-

```bash
hbase shell
```

2. Create employee table with column family 'cf'-

create 'employees', 'cf'

3. Let's populate the "employees" table with some sample data. Use the following commands to add employee details:

```bash
put 'employees','1001','cf:name','mike'

put 'employees','1001','cf:country','USA'

put 'employees','1002','cf:name','sky'

put 'employees','1002','cf:country','Canada'

put 'employees','1003','cf:name','sara'

put 'employees','1003','cf:country','aus'

```

4. Launch the Hive CLI and Define an External Table
Now switch to the Hive environment. Launch the Hive CLI using the hive command. Once you're in the Hive CLI, you can define an external table that references the HBase table. Enter the following HiveQL query:

```bash
CREATE EXTERNAL TABLE hbase_employee(key STRING, name STRING, country STRING)
STORED BY 'org.apache.hadoop.hive.hbase.HBaseStorageHandler'
WITH SERDEPROPERTIES ("hbase.columns.mapping" = ":key,cf:name,cf:country")
TBLPROPERTIES ("hbase.table.name" = "employees");
```

This HiveQL query defines an external table named "hbase_employee" that points to the "employees" HBase table. It specifies the column mapping and other properties required for integrating Hive with HBase.

5.  Test Your Hive Query

With the external table defined, you can now run Hive queries on HBase data. For example, you can run a simple query to count employees by country:

```bash
select country,count(\*) from hbase\_employee group by country;
```

Tip: Handling HBase Classes Not Found Exception
If you encounter an HBase classes not found exception while running Hive queries, it may be due to missing HBase JAR files. To resolve this issue, you can add the HBase JAR to Hive's auxiliary path. Here's the command to do so:

    hive --auxpath ${HBASE_HOME}/hbase-0.94.13.jar

By following the steps outlined, you can seamlessly execute Hive queries over HBase, enabling you to work with both structured and unstructured data within your big data ecosystem. Cheers!