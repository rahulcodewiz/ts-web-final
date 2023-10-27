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

# Exploring Hbase Column Qualifiers with Column Families Using MapReduce

  
HBase, a distributed NoSQL database, offers robust data storage capabilities. However, when it comes to retrieving all column qualifiers from a table with millions of rows, using a standalone program can be quite time-consuming. In this blog post, we will explore a MapReduce job that allows you to efficiently retrieve all columns with their respective column families in HBase.



HBase does not provide a direct client API to fetch all the column qualifiers. To address this limitation and expedite the process, we can leverage the power of MapReduce. Below, we'll dive into the code that makes this possible.


### Job Driver:

This driver code snippet initiates the MapReduce job and sets up the necessary configurations.


```java 
public static Job createSubmittableJob(Configuration conf, String[] args) throws IOException {
   String tableName = args[1];
   conf.set("hbase.table.name", args[1]); 
   System.out.println("table: " + tableName);
   deletePath(conf, args[2]);
   Job job = new Job(conf, conf.get(JOB_NAME_CONF_KEY, JOB_NAME_CONF_KEY + "_" + tableName));
   // Need to add HBase jars to job class path
   HBaseConfiguration.addHbaseResources(job.getConfiguration());
   TableMapReduceUtil.addDependencyJars(job);
   TableMapReduceUtil.addDependencyJars(job.getConfiguration(), org.apache.hadoop.hbase.client.Put.class);
   job.setJarByClass(ColumnsCounter.class);
   Scan scan = new Scan();
   scan.setCacheBlocks(false);
   // scan.addFamily(Bytes.toBytes(family));
   TableMapReduceUtil.initTableMapperJob(tableName, scan, ColumnsMapper.class, Text.class, Text.class, job);
   job.setReducerClass(ColumnsReducer.class);
   // job.setNumReduceTasks(1);
   FileOutputFormat.setOutputPath(job, new Path(args[2]));
   return job;
}
```

### Map phase

Now, let's take a look at the Mapper class responsible for emitting combinations of column family and qualifiers.

```java 
static class ColumnsMapper extends TableMapper<Text, Text> {
   @Override
   public void map(ImmutableBytesWritable row, Result values, Context context) throws IOException, InterruptedException {
      // Emit every combination of column family and qualifiers
      for (Map.Entry<byte[], NavigableMap<byte[], byte[]>> columnFamilyMap : values.getNoVersionMap().entrySet()) {
         for (Map.Entry<byte[], byte[]> entry : columnFamilyMap.getValue().entrySet()) {
            String cQualifier = Bytes.toString(entry.getKey());
            context.write(new Text(cQualifier), new Text(""));
         }
      }
   }
}
```

### Reduce

Finally, in the Reducer class, we gather and consolidate the emitted qualifiers.

```java 
static class ColumnsReducer extends Reducer<Text, Text, Text, Text> {
   public void reduce(Text key, Iterable<Text> values, Context context) throws IOException, InterruptedException {
      Iterator<Text> columns = values.iterator();
      List<String> columnsList = new ArrayList<>();
      while (columns.hasNext()) {
         columnsList.add(columns.next().toString());
      }
      context.write(key, new Text(columnsList.toString()));
   }
}
```



You can find the full source code for this example on [techsquids](https://github.com/rahul86s/techsquids/blob/master/map-reduce/src/main/java/com/ts/mapreduce/hbase/ColumnsCounter.java "git").

For more HBase-related insights, don't forget to check out our related post on launching HBase MapReduce jobs on TechSquids.