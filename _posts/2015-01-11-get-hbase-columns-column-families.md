---
layout: post
title: Java Example for Hbase Columns witandh Column Families Operations
date: 2015-01-11 02:54:48.000000000 -08:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Big Data
- hbase
- java
tags:
- hadoop
- hbase
- java
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/get-hbase-columns-column-families/"
---

## Java Example for Hbase Columns witandh Column Families Operations
  
Hbase doesn't provide any client API to get all the column qualifiers. If your table has millions of rows and you need to get all the qualifiers then it takes very long time to get all columns by standalone program. This post shares the map reduce job that will help you to get all columns with family.  


### Job Driver:

```java 
public static Job createSubmittableJob(Configuration conf, String[] args) throws IOException {
   String tableName =args[1];
   conf.set("habse.table.name", args[1]); 
   System.out.println("table: " + tableName);
    deletePath(conf, args[2]);
    Job job = new Job(conf, conf.get(JOB\_NAME\_CONF\_KEY, JOB\_NAME\_CONF\_KEY + "\_" + tableName));
    // Need to add Hbase jars to job class path HBaseConfiguration.addHbaseResources(job.getConfiguration());
    TableMapReduceUtil.addDependencyJars(job);
    TableMapReduceUtil.addDependencyJars(job.getConfiguration(), org.apache.hadoop.hbase.client.Put.class);
    job.setJarByClass(ColumnsCounter.class);
    Scan scan = new Scan();
    scan.setCacheBlocks(false);
    // scan.addFamily(Bytes.toBytes(family));
    TableMapReduceUtil.initTableMapperJob( tableName, scan, ColumnsMapper.class, Text.class, Text.class, job);
    job.setReducerClass(ColumnsReducer.class);
    //job.setNumReduceTasks(1);
    FileOutputFormat.setOutputPath(job, new Path(args[2]));
    return job;
}
```

### Map phase

```java 
static class ColumnsMapper extends TableMapper { @Override public void map(ImmutableBytesWritable row, Result values, Context context) throws IOException, InterruptedException { // emit every combination of column family and qualifiers for (Entry\> columnFamilyMap : values.getNoVersionMap().entrySet()) { for (Entry entry : columnFamilyMap.getValue().entrySet()) { String cQualifier = Bytes.toString(entry.getKey());
context.write(new Text(cQualifier), NullWritable.get());
} } } }
```

### Reduce
```
static class ColumnsReducer extends Reducer { public void reduce(Text key, Iterable values, Context context) throws IOException, InterruptedException { Iterator columns= values.iterator();
List columnsList=new ArrayList();
while(columns.hasNext()) columnsList.add(columns.next().toString());
context.write(key, new Text(columnsList.toString()));
} }
```

Full program at git([techsquids](https://github.com/rahul86s/techsquids/blob/master/map-reduce/src/main/java/com/ts/mapreduce/hbase/ColumnsCounter.java "git"))  
Related post: launch hbase mapreduce job [runjob](http://www.techsquids.com/?p=367 "mapr")

