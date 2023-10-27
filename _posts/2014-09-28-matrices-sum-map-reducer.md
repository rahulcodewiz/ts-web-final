---
layout: post
title: Matrix operations in Mapreduce
date: 2014-09-28 04:37:42.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Big Data
tags:
- hadoop
- java
meta:
  _edit_last: '1'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: Matrices Sum Map Reducer
  _yoast_wpseo_title: Matrices Sum Map Reducer
  _yoast_wpseo_metadesc: Matrices Sum Map Reducer, multiple mapper and single reducer
    program to add the matrices
  _yoast_wpseo_linkdex: '82'
  dsq_thread_id: '3064153150'
  
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/matrices-sum-map-reducer/"
---

## Matrix operations in Mapreduce

 **Matrices Sum Map Reducer**  
Matrix sum is the operation of adding matrices by adding corresponding entries together.  
**Entrywise sum**  

The sum of two m × n (pronounced "m by n") matrices A and B, denoted by A + B, is again an m × n matrix computed by adding corresponding elements  
[![matraix sum]({{ site.baseurl }}/assets/images/matraix-sum-300x137.png)](http://www.techsquids.com/wp-content/uploads/2014/09/matraix-sum.png)

Entrywise sum implementation using Map-reduce-

I have two matrices in separate files ( check blog [indexing](http://www.techsquids.com/bd/indexing-using-map-reduce/ "indexing")for generating index), each file contains same size (m\*n) matrix. matrix row index(m) and values separated by ^A [0x001] and values(n) are separated by (,).

1. Mapper emits the row index as key and entire row as a value. If you have different types of matrices then create separate mappers to process/ filters the matrix.

```java
class MatrixSumMapper extends Mapper\<LongWritable, Text, LongWritable, Text\> { 
  String fName = null;
  char keySeprator;
  @Override protected void setup( Mapper\<LongWritable, Text, LongWritable, Text\>.Context context) throws IOException, InterruptedException { fName = ((FileSplit)context.getInputSplit()).getPath().getName();
  keySeprator=(char)context.getConfiguration().getInt("matrix.key.separator",0x001);
  } @Override protected void map(LongWritable key, Text value, Mapper\<LongWritable, Text, LongWritable, Text\>.Context context) throws IOException, InterruptedException { LongWritable keyM = new LongWritable(Long.parseLong(value.toString().split(String.format("%c",keySeprator))[0]));
  Text val = new Text(value.toString().split(String.format("%c",keySeprator))[1]);
  context.write(keyM, val);
} }
```
2. Reducer gets the row key as (m). Next split each value to generate (n) then add the values index and position wise.

```java
 
```
3. Driver code:
```java
public class Driver extends Configured implements Tool { private static Logger logger = Logger.getLogger(Driver.class);
private boolean deleteDirectory(Path path) throws IOException { FileSystem fs = FileSystem.get(getConf());
return fs.delete(path, true);
} public int run(String[] args) throws Exception { logger.info("job Matrix Sum Driver Begin");
Configuration conf = getConf();
conf.setInt("matrix.key.separator", 0x001);
conf.set("matrix.element.separator",",");
Job job = new Job(conf, "Matrix Sum");
job.setJarByClass(Driver.class);
Path input1 = new Path(args[0]);
Path input2 = new Path(args[1]);
Path output = new Path(args[2]);
deleteDirectory(output);
job.setMapOutputKeyClass(LongWritable.class);
job.setMapOutputValueClass(Text.class);
job.setMapperClass(MatrixSumMapper.class);
job.setReducerClass(MatrixSumReducer.class);
job.setNumReduceTasks(1);
job.setInputFormatClass(TextInputFormat.class);
job.setOutputFormatClass(TextOutputFormat.class);
logger.info("deleting output directory: " + deleteDirectory(output));
FileInputFormat.setInputPaths(job, input1, input2);
FileOutputFormat.setOutputPath(job, output);
return job.waitForCompletion(true) ? 0 : 1;
} public static void main(String[] args) throws Exception { for (String str : args) System.out.println(str);
Configuration config = new Configuration();
System.exit(ToolRunner.run(config, new Driver(), args));
} }
```

check out the complete source code from [techsquids](https://github.com/rahul86s/techsquids.git "techsquids")

