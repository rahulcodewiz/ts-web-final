---
layout: post
title: Indexing Using Map Reduce
date: 2014-09-25 19:49:46.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Big Data
tags:
- hadoop
- map-reduce
meta:
  _edit_last: '1'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: Indexing Using Map Reduce
  _yoast_wpseo_title: Indexing Using Map Reduce
  _yoast_wpseo_metadesc: generate indexing using mapreduce. create index operations
    with map reducer
  _yoast_wpseo_linkdex: '73'
  dsq_thread_id: '3091825106'
  wp-syntax-cache-content: "a:4:{i:1;s:2354:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n</pre></td><td class=\"code\"><pre
    class=\"java\" style=\"font-family:monospace;\"><span style=\"color: #000000;
    font-weight: bold;\">class</span> IndexMapper <span style=\"color: #000000; font-weight:
    bold;\">extends</span> Mapper<span style=\"color: #339933;\">&lt;</span><span
    style=\"color: #003399;\">Object</span> , Text, LongWritable, Text<span style=\"color:
    #339933;\">&gt;</span><span style=\"color: #009900;\">&#123;</span>\n@Override\n<span
    style=\"color: #000000; font-weight: bold;\">protected</span> <span style=\"color:
    #000066; font-weight: bold;\">void</span> map<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #003399;\">Object</span> key, Text value, Mapper<span style=\"color:
    #339933;\">&lt;</span><span style=\"color: #003399;\">Object</span>, Text, LongWritable,
    Text<span style=\"color: #339933;\">&gt;</span>.<span style=\"color: #003399;\">Context</span>
    context<span style=\"color: #009900;\">&#41;</span>\n<span style=\"color: #000000;
    font-weight: bold;\">throws</span> <span style=\"color: #003399;\">IOException</span>,
    <span style=\"color: #003399;\">InterruptedException</span> <span style=\"color:
    #009900;\">&#123;</span>\ncontext.<span style=\"color: #006633;\">write</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #000000; font-weight:
    bold;\">new</span> LongWritable<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #003399;\">Long</span>.<span style=\"color: #006633;\">parseLong</span><span
    style=\"color: #009900;\">&#40;</span>key.<span style=\"color: #006633;\">toString</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span>,
    value<span style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n<span
    style=\"color: #009900;\">&#125;</span>\n<span style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">class IndexMapper extends Mapper&lt;Object
    , Text, LongWritable, Text&gt;{\r\n@Override\r\nprotected void map(Object key,
    Text value, Mapper&lt;Object, Text, LongWritable, Text&gt;.Context context)\r\nthrows
    IOException, InterruptedException {\r\ncontext.write(new LongWritable(Long.parseLong(key.toString())),
    value);\r\n}\r\n}</p></div>\n\";i:2;s:2088:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"line_numbers\"><pre>1\n2\n3\n4\n</pre></td><td class=\"code\"><pre class=\"java\"
    style=\"font-family:monospace;\"><span style=\"color: #000000; font-weight: bold;\">static</span>
    <span style=\"color: #000000; font-weight: bold;\">enum</span> Counter<span style=\"color:
    #009900;\">&#123;</span>COUNT<span style=\"color: #009900;\">&#125;</span> <span
    style=\"color: #000000; font-weight: bold;\">protected</span> <span style=\"color:
    #000066; font-weight: bold;\">void</span> setup<span style=\"color: #009900;\">&#40;</span>
    Reducer<span style=\"color: #339933;\">&amp;</span>lt<span style=\"color: #339933;\">;</span>LongWritable,
    Text, NullWritable, Text<span style=\"color: #339933;\">&amp;</span>gt<span style=\"color:
    #339933;\">;</span>.<span style=\"color: #003399;\">Context</span> context<span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #000000; font-weight:
    bold;\">throws</span> <span style=\"color: #003399;\">IOException</span>, <span
    style=\"color: #003399;\">InterruptedException</span> <span style=\"color: #009900;\">&#123;</span>\ncontext.<span
    style=\"color: #006633;\">getCounter</span><span style=\"color: #009900;\">&#40;</span>Counter.<span
    style=\"color: #006633;\">COUNT</span><span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">setValue</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #cc66cc;\">1</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">super</span>.<span style=\"color: #006633;\">setup</span><span style=\"color:
    #009900;\">&#40;</span>context<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">static enum Counter{COUNT} protected
    void setup( Reducer&amp;lt;LongWritable, Text, NullWritable, Text&amp;gt;.Context
    context) throws IOException, InterruptedException {\r\ncontext.getCounter(Counter.COUNT).setValue(1);\r\nsuper.setup(context);\r\n}</p></div>\n\";i:3;s:5841:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n9\n10\n11\n12\n13\n14\n15\n16\n17\n18\n</pre></td><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\"><span style=\"color:
    #000000; font-weight: bold;\">class</span> IndexReucer <span style=\"color: #000000;
    font-weight: bold;\">extends</span> Reducer<span style=\"color: #339933;\">&lt;</span>LongWritable,
    Text, NullWritable, Text<span style=\"color: #339933;\">&gt;</span><span style=\"color:
    #009900;\">&#123;</span>\n<span style=\"color: #000000; font-weight: bold;\">static</span>
    <span style=\"color: #000000; font-weight: bold;\">enum</span> Counter<span style=\"color:
    #009900;\">&#123;</span>COUNT<span style=\"color: #009900;\">&#125;</span>\n<span
    style=\"color: #000000; font-weight: bold;\">static</span> <span style=\"color:
    #000000; font-weight: bold;\">final</span> <span style=\"color: #000066; font-weight:
    bold;\">char</span> SEPARATOR<span style=\"color: #339933;\">=</span>0x001<span
    style=\"color: #339933;\">;</span>\n@Override\n<span style=\"color: #000000; font-weight:
    bold;\">protected</span> <span style=\"color: #000066; font-weight: bold;\">void</span>
    setup<span style=\"color: #009900;\">&#40;</span>\nReducer<span style=\"color:
    #339933;\">&lt;</span>LongWritable, Text, NullWritable, Text<span style=\"color:
    #339933;\">&gt;</span>.<span style=\"color: #003399;\">Context</span> context<span
    style=\"color: #009900;\">&#41;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">throws</span> <span style=\"color: #003399;\">IOException</span>, <span
    style=\"color: #003399;\">InterruptedException</span> <span style=\"color: #009900;\">&#123;</span>\ncontext.<span
    style=\"color: #006633;\">getCounter</span><span style=\"color: #009900;\">&#40;</span>Counter.<span
    style=\"color: #006633;\">COUNT</span><span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">setValue</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #cc66cc;\">1</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">super</span>.<span style=\"color: #006633;\">setup</span><span style=\"color:
    #009900;\">&#40;</span>context<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #009900;\">&#125;</span>\n@Override\n<span
    style=\"color: #000000; font-weight: bold;\">protected</span> <span style=\"color:
    #000066; font-weight: bold;\">void</span> reduce<span style=\"color: #009900;\">&#40;</span>LongWritable
    key, Iterable<span style=\"color: #339933;\">&lt;</span>Text<span style=\"color:
    #339933;\">&gt;</span> value,Reducer<span style=\"color: #339933;\">&lt;</span>LongWritable,
    Text, NullWritable, Text<span style=\"color: #339933;\">&gt;</span>.<span style=\"color:
    #003399;\">Context</span> context<span style=\"color: #009900;\">&#41;</span>\n<span
    style=\"color: #000000; font-weight: bold;\">throws</span> <span style=\"color:
    #003399;\">IOException</span>, <span style=\"color: #003399;\">InterruptedException</span>
    <span style=\"color: #009900;\">&#123;</span>\n<span style=\"color: #003399;\">Long</span>
    counter <span style=\"color: #339933;\">=</span> context.<span style=\"color:
    #006633;\">getCounter</span><span style=\"color: #009900;\">&#40;</span>Counter.<span
    style=\"color: #006633;\">COUNT</span><span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">getValue</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\ncontext.<span
    style=\"color: #006633;\">write</span><span style=\"color: #009900;\">&#40;</span>NullWritable.<span
    style=\"color: #006633;\">get</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span>, <span style=\"color: #000000; font-weight:
    bold;\">new</span> Text<span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #003399;\">String</span>.<span style=\"color: #006633;\">format</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #0000ff;\">&quot;%d%c%s&quot;</span>,
    counter,SEPARATOR,value.<span style=\"color: #006633;\">iterator</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>.<span style=\"color:
    #006633;\">next</span><span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\ncontext.<span style=\"color: #006633;\">getCounter</span><span
    style=\"color: #009900;\">&#40;</span>Counter.<span style=\"color: #006633;\">COUNT</span><span
    style=\"color: #009900;\">&#41;</span>.<span style=\"color: #006633;\">increment</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #cc66cc;\">1</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;;</span>\n<span
    style=\"color: #009900;\">&#125;</span>\n<span style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">class IndexReucer extends Reducer&lt;LongWritable,
    Text, NullWritable, Text&gt;{\r\nstatic enum Counter{COUNT}\r\nstatic final char
    SEPARATOR=0x001;\r\n@Override\r\nprotected void setup(\r\nReducer&lt;LongWritable,
    Text, NullWritable, Text&gt;.Context context)\r\nthrows IOException, InterruptedException
    {\r\ncontext.getCounter(Counter.COUNT).setValue(1);\r\nsuper.setup(context);\r\n}\r\n@Override\r\nprotected
    void reduce(LongWritable key, Iterable&lt;Text&gt; value,Reducer&lt;LongWritable,
    Text, NullWritable, Text&gt;.Context context)\r\nthrows IOException, InterruptedException
    {\r\nLong counter = context.getCounter(Counter.COUNT).getValue();\r\ncontext.write(NullWritable.get(),
    new Text(String.format(&quot;%d%c%s&quot;, counter,SEPARATOR,value.iterator().next())));\r\ncontext.getCounter(Counter.COUNT).increment(1);;\r\n}\r\n}</p></div>\n\";i:4;s:5814:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n9\n10\n11\n12\n13\n14\n15\n16\n17\n18\n19\n20\n21\n22\n23\n24\n25\n26\n27\n28\n29\n30\n31\n32\n33\n</pre></td><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\"><span style=\"color:
    #000000; font-weight: bold;\">public</span> <span style=\"color: #000066; font-weight:
    bold;\">int</span> run<span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #003399;\">String</span><span style=\"color: #009900;\">&#91;</span><span style=\"color:
    #009900;\">&#93;</span> args<span style=\"color: #009900;\">&#41;</span> <span
    style=\"color: #000000; font-weight: bold;\">throws</span> <span style=\"color:
    #003399;\">Exception</span> <span style=\"color: #009900;\">&#123;</span>\n&nbsp;\nConfiguration
    conf <span style=\"color: #339933;\">=</span>getConf<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\nJob
    job <span style=\"color: #339933;\">=</span> <span style=\"color: #000000; font-weight:
    bold;\">new</span> Job<span style=\"color: #009900;\">&#40;</span>conf, <span
    style=\"color: #0000ff;\">&quot;Indexing Job&quot;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\njob.<span
    style=\"color: #006633;\">setMapOutputKeyClass</span><span style=\"color: #009900;\">&#40;</span>LongWritable.<span
    style=\"color: #000000; font-weight: bold;\">class</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\njob.<span
    style=\"color: #006633;\">setMapOutputValueClass</span><span style=\"color: #009900;\">&#40;</span>Text.<span
    style=\"color: #000000; font-weight: bold;\">class</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\njob.<span
    style=\"color: #006633;\">setMapperClass</span><span style=\"color: #009900;\">&#40;</span>IndexMapper.<span
    style=\"color: #000000; font-weight: bold;\">class</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\njob.<span
    style=\"color: #006633;\">setReducerClass</span><span style=\"color: #009900;\">&#40;</span>IndexReucer.<span
    style=\"color: #000000; font-weight: bold;\">class</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\njob.<span
    style=\"color: #006633;\">setNumReduceTasks</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #cc66cc;\">1</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\njob.<span style=\"color: #006633;\">setInputFormatClass</span><span
    style=\"color: #009900;\">&#40;</span>TextInputFormat.<span style=\"color: #000000;
    font-weight: bold;\">class</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\njob.<span style=\"color: #006633;\">setOutputFormatClass</span><span
    style=\"color: #009900;\">&#40;</span>TextOutputFormat.<span style=\"color: #000000;
    font-weight: bold;\">class</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\nPath output <span style=\"color: #339933;\">=</span>
    <span style=\"color: #000000; font-weight: bold;\">new</span> Path<span style=\"color:
    #009900;\">&#40;</span>args<span style=\"color: #009900;\">&#91;</span><span style=\"color:
    #cc66cc;\">1</span><span style=\"color: #009900;\">&#93;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\ndeleteDirectory<span
    style=\"color: #009900;\">&#40;</span>output<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\nFileInputFormat.<span style=\"color:
    #006633;\">addInputPath</span><span style=\"color: #009900;\">&#40;</span>job,
    <span style=\"color: #000000; font-weight: bold;\">new</span> Path<span style=\"color:
    #009900;\">&#40;</span>args<span style=\"color: #009900;\">&#91;</span><span style=\"color:
    #cc66cc;\">0</span><span style=\"color: #009900;\">&#93;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n&nbsp;\nFileOutputFormat.<span style=\"color: #006633;\">setOutputPath</span><span
    style=\"color: #009900;\">&#40;</span>job, output<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\njob.<span style=\"color: #006633;\">setJarByClass</span><span
    style=\"color: #009900;\">&#40;</span>IndexDriver.<span style=\"color: #000000;
    font-weight: bold;\">class</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\n<span style=\"color: #000000; font-weight:
    bold;\">return</span> job.<span style=\"color: #006633;\">waitForCompletion</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #000066; font-weight:
    bold;\">true</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">?</span><span style=\"color: #cc66cc;\">0</span><span style=\"color:
    #339933;\">:</span><span style=\"color: #cc66cc;\">1</span><span style=\"color:
    #339933;\">;</span>\n&nbsp;\n<span style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">public int run(String[] args) throws
    Exception {\r\n\r\nConfiguration conf =getConf();\r\n\r\nJob job = new Job(conf,
    &quot;Indexing Job&quot;);\r\n\r\njob.setMapOutputKeyClass(LongWritable.class);\r\n\r\njob.setMapOutputValueClass(Text.class);\r\n\r\njob.setMapperClass(IndexMapper.class);\r\n\r\njob.setReducerClass(IndexReucer.class);\r\n\r\njob.setNumReduceTasks(1);\r\n\r\njob.setInputFormatClass(TextInputFormat.class);\r\n\r\njob.setOutputFormatClass(TextOutputFormat.class);\r\n\r\nPath
    output = new Path(args[1]);\r\n\r\ndeleteDirectory(output);\r\n\r\nFileInputFormat.addInputPath(job,
    new Path(args[0]));\r\n\r\nFileOutputFormat.setOutputPath(job, output);\r\n\r\njob.setJarByClass(IndexDriver.class);\r\n\r\nreturn
    job.waitForCompletion(true)?0:1;\r\n\r\n}</p></div>\n\";}"
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/indexing-using-map-reduce/"
---
Generate indexing using map reduce can't be done in distributed mode of&nbsp; mapreduce as each line number is sequential and unique. To achieve this I tried to generate index using single reducer job.

Here are the steps you can follow to create the job-

create a mapper that emits the line offset as key and row as value.

```
class IndexMapper extends Mapper<object text longwritable>{
@Override
protected void map(Object key, Text value, Mapper<object text longwritable>.Context context)
throws IOException, InterruptedException {
context.write(new LongWritable(Long.parseLong(key.toString())), value);
}
}
</object></object>
```

At reducer side setup a counter for line number in setup method.

```
static enum Counter{COUNT} protected void setup( Reducer\<LongWritable, Text, NullWritable, Text\>.Context context) throws IOException, InterruptedException { context.getCounter(Counter.COUNT).setValue(1); super.setup(context); }
```

In reduce method for each line increment the counter, write the current counter value as key and intetarator's rows as value. Or club the counter with iterator rows and emit as value.

```
class IndexReucer extends Reducer<longwritable text nullwritable>{
static enum Counter{COUNT}
static final char SEPARATOR=0x001;
@Override
protected void setup(
Reducer<longwritable text nullwritable>.Context context)
throws IOException, InterruptedException {
context.getCounter(Counter.COUNT).setValue(1);
super.setup(context);
}
@Override
protected void reduce(LongWritable key, Iterable<text> value,Reducer<longwritable text nullwritable>.Context context)
throws IOException, InterruptedException {
Long counter = context.getCounter(Counter.COUNT).getValue();
context.write(NullWritable.get(), new Text(String.format("%d%c%s", counter,SEPARATOR,value.iterator().next())));
context.getCounter(Counter.COUNT).increment(1);;
}
}
</longwritable></text></longwritable></longwritable>
```

finally setup your driver

```
public int run(String[] args) throws Exception { Configuration conf =getConf(); Job job = new Job(conf, "Indexing Job"); job.setMapOutputKeyClass(LongWritable.class); job.setMapOutputValueClass(Text.class); job.setMapperClass(IndexMapper.class); job.setReducerClass(IndexReucer.class); job.setNumReduceTasks(1); job.setInputFormatClass(TextInputFormat.class); job.setOutputFormatClass(TextOutputFormat.class); Path output = new Path(args[1]); deleteDirectory(output); FileInputFormat.addInputPath(job, new Path(args[0])); FileOutputFormat.setOutputPath(job, output); job.setJarByClass(IndexDriver.class); return job.waitForCompletion(true)?0:1; }
```

You can download the entire project from github https://github.com/rahul86s/techsquids.git

