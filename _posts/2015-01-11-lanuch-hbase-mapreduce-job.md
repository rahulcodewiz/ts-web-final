---
layout: post
title: Lanuch Hbase Mapreduce Job
date: 2015-01-11 03:09:37.000000000 -08:00
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
permalink: "/bd/lanuch-hbase-mapreduce-job/"
---

# Launching an HBase MapReduce Job with Custom JARs

In the world of big data processing, Hadoop and HBase are powerful tools that are commonly used to store and process large volumes of data. MapReduce jobs in Hadoop are a key component for distributed data processing. However, sometimes you may need to launch an HBase MapReduce job with additional libraries or custom JARs. In this blog post, I will walk you through the process of launching an HBase MapReduce job with custom JARs.


- Collect the Required JARs
Before launching an HBase MapReduce job, you need to collect all the required JAR files and store them in a variable. These JARs will be used by your MapReduce job for proper execution. You can set the JAR variable like this:

```
jar=/home/hadoop/Desktop/techsquids/repos/techsquids/map-reduce/target/map-reduce-1.0-SNAPSHOT.jar
classpath=$jar

# Loop through HBase library JARs and add them to the classpath
for f in $HBASE_HOME/lib/*.jar; do
    classpath="${classpath},$f"
done
```

- Prepare the Hadoop Classpath

Next prepare the Hadoop classpath from previously formed jar files and jars separated by colon(:).

```
path=`echo $classpath | sed 's/,/:/g'`
```

- Export LIBJARS and HADOOP_CLASSPATH
To make the JARs available to your Hadoop job, you need to export two important environment variables, LIBJARS and HADOOP_CLASSPATH. These variables ensure that Hadoop can access the JARs you've collected:

```
export LIBJARS=`hadoop classpath`:$classpath
export HADOOP_CLASSPATH=$path
```

- Run the Hadoop Job
Now that everything is set up, you can run your HBase MapReduce job with the custom JARs and libraries. Use the following command to execute your job:

```
hadoop jar $jar com.ts.mapreduce.hbase.ColumnsCounter -libjars ${classpath} "$@"
```

- Handle ClassNotFoundException

If you encounter a ClassNotFountException during your Java job execution, you may need to register additional JARs with HBase. This can be done with the following code:

```
HBaseConfiguration.addHbaseResources(job.getConfiguration());
TableMapReduceUtil.addDependencyJars(job);
TableMapReduceUtil.addDependencyJars(job.getConfiguration(), org.apache.hadoop.hbase.client.Put.class);
job.setJarByClass(ColumnsCounter.class);
```
For a complete source example, you can check out the script on GitHub at ([techsquids](https://github.com/rahul86s/techsquids/blob/master/hbase/runjob.sh "runjob.sh")).

