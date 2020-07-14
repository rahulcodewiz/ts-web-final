---
layout: post
title: Get Hbase Columns with Column Families
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
meta:
  _edit_last: '1'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: Get Hbase Columns with Column Families
  _yoast_wpseo_title: Get Hbase Columns with Column Families
  _yoast_wpseo_metadesc: Get Hbase Columns with Column Families
  _yoast_wpseo_linkdex: '76'
  dsq_thread_id: '4165269295'
  wp-syntax-cache-content: "a:3:{i:1;s:7407:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n9\n10\n11\n12\n13\n14\n15\n16\n17\n18\n19\n20\n21\n22\n23\n24\n25\n26\n27\n28\n29\n30\n31\n32\n33\n34\n35\n36\n37\n38\n39\n</pre></td><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\">\t<span style=\"color:
    #000000; font-weight: bold;\">public</span> <span style=\"color: #000000; font-weight:
    bold;\">static</span> Job createSubmittableJob<span style=\"color: #009900;\">&#40;</span>Configuration
    conf, <span style=\"color: #003399;\">String</span><span style=\"color: #009900;\">&#91;</span><span
    style=\"color: #009900;\">&#93;</span> args<span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #000000; font-weight: bold;\">throws</span> <span style=\"color:
    #003399;\">IOException</span> <span style=\"color: #009900;\">&#123;</span>\n&nbsp;\n\t\t<span
    style=\"color: #003399;\">String</span> tableName <span style=\"color: #339933;\">=</span>args<span
    style=\"color: #009900;\">&#91;</span><span style=\"color: #cc66cc;\">1</span><span
    style=\"color: #009900;\">&#93;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n\t\tconf.<span
    style=\"color: #006633;\">set</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;habse.table.name&quot;</span>, args<span style=\"color:
    #009900;\">&#91;</span><span style=\"color: #cc66cc;\">1</span><span style=\"color:
    #009900;\">&#93;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n&nbsp;\n\t\t<span style=\"color: #003399;\">System</span>.<span
    style=\"color: #006633;\">out</span>.<span style=\"color: #006633;\">println</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #0000ff;\">&quot;table:
    &quot;</span> <span style=\"color: #339933;\">+</span> tableName<span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n\t\tdeletePath<span
    style=\"color: #009900;\">&#40;</span>conf, args<span style=\"color: #009900;\">&#91;</span><span
    style=\"color: #cc66cc;\">2</span><span style=\"color: #009900;\">&#93;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n\t\tJob
    job <span style=\"color: #339933;\">=</span> <span style=\"color: #000000; font-weight:
    bold;\">new</span> Job<span style=\"color: #009900;\">&#40;</span>conf, conf.<span
    style=\"color: #006633;\">get</span><span style=\"color: #009900;\">&#40;</span>JOB_NAME_CONF_KEY,
    JOB_NAME_CONF_KEY <span style=\"color: #339933;\">+</span> <span style=\"color:
    #0000ff;\">&quot;_&quot;</span> <span style=\"color: #339933;\">+</span> tableName<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\n\t\t<span style=\"color: #666666;
    font-style: italic;\">// Need to add Hbase jars to job class path</span>\n&nbsp;\n\t\tHBaseConfiguration.<span
    style=\"color: #006633;\">addHbaseResources</span><span style=\"color: #009900;\">&#40;</span>job.<span
    style=\"color: #006633;\">getConfiguration</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\n\t\tTableMapReduceUtil.<span style=\"color:
    #006633;\">addDependencyJars</span><span style=\"color: #009900;\">&#40;</span>job<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n\t\tTableMapReduceUtil.<span
    style=\"color: #006633;\">addDependencyJars</span><span style=\"color: #009900;\">&#40;</span>job.<span
    style=\"color: #006633;\">getConfiguration</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span>, org.<span style=\"color: #006633;\">apache</span>.<span
    style=\"color: #006633;\">hadoop</span>.<span style=\"color: #006633;\">hbase</span>.<span
    style=\"color: #006633;\">client</span>.<span style=\"color: #006633;\">Put</span>.<span
    style=\"color: #000000; font-weight: bold;\">class</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n\t\tjob.<span
    style=\"color: #006633;\">setJarByClass</span><span style=\"color: #009900;\">&#40;</span>ColumnsCounter.<span
    style=\"color: #000000; font-weight: bold;\">class</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n\t\tScan
    scan <span style=\"color: #339933;\">=</span> <span style=\"color: #000000; font-weight:
    bold;\">new</span> Scan<span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n\t\tscan.<span
    style=\"color: #006633;\">setCacheBlocks</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #000066; font-weight: bold;\">false</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n\t\t<span
    style=\"color: #666666; font-style: italic;\">// scan.addFamily(Bytes.toBytes(family));</span>\n&nbsp;\n\t\tTableMapReduceUtil.<span
    style=\"color: #006633;\">initTableMapperJob</span><span style=\"color: #009900;\">&#40;</span>\n\t\t\t\ttableName,
    scan, ColumnsMapper.<span style=\"color: #000000; font-weight: bold;\">class</span>,\n\t\t\t\tText.<span
    style=\"color: #000000; font-weight: bold;\">class</span>,\n\t\t\t\tText.<span
    style=\"color: #000000; font-weight: bold;\">class</span>, job<span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n\t\tjob.<span
    style=\"color: #006633;\">setReducerClass</span><span style=\"color: #009900;\">&#40;</span>ColumnsReducer.<span
    style=\"color: #000000; font-weight: bold;\">class</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n\t\t<span
    style=\"color: #666666; font-style: italic;\">//job.setNumReduceTasks(1);</span>\n&nbsp;\n\t\tFileOutputFormat.<span
    style=\"color: #006633;\">setOutputPath</span><span style=\"color: #009900;\">&#40;</span>job,
    <span style=\"color: #000000; font-weight: bold;\">new</span> Path<span style=\"color:
    #009900;\">&#40;</span>args<span style=\"color: #009900;\">&#91;</span><span style=\"color:
    #cc66cc;\">2</span><span style=\"color: #009900;\">&#93;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n&nbsp;\n\t\t<span style=\"color: #000000; font-weight: bold;\">return</span>
    job<span style=\"color: #339933;\">;</span>\n&nbsp;\n\t<span style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">\tpublic static Job createSubmittableJob(Configuration
    conf, String[] args) throws IOException {\r\n\r\n\t\tString tableName =args[1];\r\n\r\n\t\tconf.set(&quot;habse.table.name&quot;,
    args[1]);\r\n\r\n\t\tSystem.out.println(&quot;table: &quot; + tableName);\r\n\t\tdeletePath(conf,
    args[2]);\r\n\t\tJob job = new Job(conf, conf.get(JOB_NAME_CONF_KEY, JOB_NAME_CONF_KEY
    + &quot;_&quot; + tableName));\r\n\r\n\t\t// Need to add Hbase jars to job class
    path\r\n\r\n\t\tHBaseConfiguration.addHbaseResources(job.getConfiguration());\r\n\r\n\t\tTableMapReduceUtil.addDependencyJars(job);\r\n\r\n\t\tTableMapReduceUtil.addDependencyJars(job.getConfiguration(),
    org.apache.hadoop.hbase.client.Put.class);\r\n\r\n\t\tjob.setJarByClass(ColumnsCounter.class);\r\n\r\n\t\tScan
    scan = new Scan();\r\n\r\n\t\tscan.setCacheBlocks(false);\r\n\r\n\t\t// scan.addFamily(Bytes.toBytes(family));\r\n\r\n\t\tTableMapReduceUtil.initTableMapperJob(\r\n\t\t\t\ttableName,
    scan, ColumnsMapper.class,\r\n\t\t\t\tText.class,\r\n\t\t\t\tText.class, job);\r\n\t\tjob.setReducerClass(ColumnsReducer.class);\r\n\t\t\r\n\t\t//job.setNumReduceTasks(1);\r\n\r\n\t\tFileOutputFormat.setOutputPath(job,
    new Path(args[2]));\r\n\r\n\t\treturn job;\r\n\r\n\t}</p></div>\n\";i:2;s:5064:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n9\n10\n11\n12\n13\n14\n15\n16\n17\n18\n19\n20\n</pre></td><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\">\t<span style=\"color:
    #000000; font-weight: bold;\">static</span> <span style=\"color: #000000; font-weight:
    bold;\">class</span> ColumnsMapper <span style=\"color: #000000; font-weight:
    bold;\">extends</span> TableMapper<span style=\"color: #339933;\">&lt;</span>Text,
    NullWritable<span style=\"color: #339933;\">&gt;</span> <span style=\"color: #009900;\">&#123;</span>\n&nbsp;\n\t\t@Override\n\t\t<span
    style=\"color: #000000; font-weight: bold;\">public</span> <span style=\"color:
    #000066; font-weight: bold;\">void</span> map<span style=\"color: #009900;\">&#40;</span>ImmutableBytesWritable
    row, Result values, <span style=\"color: #003399;\">Context</span> context<span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #000000; font-weight:
    bold;\">throws</span> <span style=\"color: #003399;\">IOException</span>,\n\t\t\t\t<span
    style=\"color: #003399;\">InterruptedException</span> <span style=\"color: #009900;\">&#123;</span>\n&nbsp;\n\t\t\t<span
    style=\"color: #666666; font-style: italic;\">// emit every combination of column
    family and qualifiers</span>\n\t\t\t<span style=\"color: #000000; font-weight:
    bold;\">for</span> <span style=\"color: #009900;\">&#40;</span>Entry<span style=\"color:
    #339933;\">&lt;</span><span style=\"color: #000066; font-weight: bold;\">byte</span><span
    style=\"color: #009900;\">&#91;</span><span style=\"color: #009900;\">&#93;</span>,
    NavigableMap<span style=\"color: #339933;\">&lt;</span><span style=\"color: #000066;
    font-weight: bold;\">byte</span><span style=\"color: #009900;\">&#91;</span><span
    style=\"color: #009900;\">&#93;</span>, <span style=\"color: #000066; font-weight:
    bold;\">byte</span><span style=\"color: #009900;\">&#91;</span><span style=\"color:
    #009900;\">&#93;</span><span style=\"color: #339933;\">&gt;&gt;</span> columnFamilyMap
    <span style=\"color: #339933;\">:</span> values.<span style=\"color: #006633;\">getNoVersionMap</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">entrySet</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#123;</span>\n\t\t\t\t<span style=\"color: #000000;
    font-weight: bold;\">for</span> <span style=\"color: #009900;\">&#40;</span>Entry<span
    style=\"color: #339933;\">&lt;</span><span style=\"color: #000066; font-weight:
    bold;\">byte</span><span style=\"color: #009900;\">&#91;</span><span style=\"color:
    #009900;\">&#93;</span>, <span style=\"color: #000066; font-weight: bold;\">byte</span><span
    style=\"color: #009900;\">&#91;</span><span style=\"color: #009900;\">&#93;</span><span
    style=\"color: #339933;\">&gt;</span> entry <span style=\"color: #339933;\">:</span>
    columnFamilyMap.<span style=\"color: #006633;\">getValue</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>.<span style=\"color:
    #006633;\">entrySet</span><span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span> <span style=\"color:
    #009900;\">&#123;</span>\n&nbsp;\n\t\t\t\t\t<span style=\"color: #003399;\">String</span>
    cQualifier <span style=\"color: #339933;\">=</span> Bytes.<span style=\"color:
    #006633;\">toString</span><span style=\"color: #009900;\">&#40;</span>entry.<span
    style=\"color: #006633;\">getKey</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\n\t\t\t\t\tcontext.<span style=\"color:
    #006633;\">write</span><span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #000000; font-weight: bold;\">new</span> Text<span style=\"color: #009900;\">&#40;</span>cQualifier<span
    style=\"color: #009900;\">&#41;</span>, NullWritable.<span style=\"color: #006633;\">get</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n\t\t\t\t<span
    style=\"color: #009900;\">&#125;</span>\n&nbsp;\n\t\t\t<span style=\"color: #009900;\">&#125;</span>\n&nbsp;\n\t\t<span
    style=\"color: #009900;\">&#125;</span>\n\t<span style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">\tstatic class ColumnsMapper extends
    TableMapper&lt;Text, NullWritable&gt; {\r\n\r\n\t\t@Override\r\n\t\tpublic void
    map(ImmutableBytesWritable row, Result values, Context context) throws IOException,\r\n\t\t\t\tInterruptedException
    {\r\n\r\n\t\t\t// emit every combination of column family and qualifiers\r\n\t\t\tfor
    (Entry&lt;byte[], NavigableMap&lt;byte[], byte[]&gt;&gt; columnFamilyMap : values.getNoVersionMap().entrySet())
    {\r\n\t\t\t\tfor (Entry&lt;byte[], byte[]&gt; entry : columnFamilyMap.getValue().entrySet())
    {\r\n\r\n\t\t\t\t\tString cQualifier = Bytes.toString(entry.getKey());\r\n\r\n\t\t\t\t\tcontext.write(new
    Text(cQualifier), NullWritable.get());\r\n\r\n\t\t\t\t}\r\n\r\n\t\t\t}\r\n\r\n\t\t}\r\n\t}</p></div>\n\";i:3;s:3753:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n9\n10\n11\n12\n13\n</pre></td><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\"><span style=\"color:
    #000000; font-weight: bold;\">static</span> <span style=\"color: #000000; font-weight:
    bold;\">class</span> ColumnsReducer <span style=\"color: #000000; font-weight:
    bold;\">extends</span> Reducer<span style=\"color: #339933;\">&lt;</span>Text,
    Text, Text, Text<span style=\"color: #339933;\">&gt;</span> <span style=\"color:
    #009900;\">&#123;</span>\n&nbsp;\n\t\t<span style=\"color: #000000; font-weight:
    bold;\">public</span> <span style=\"color: #000066; font-weight: bold;\">void</span>
    reduce<span style=\"color: #009900;\">&#40;</span>Text key, Iterable<span style=\"color:
    #339933;\">&lt;</span>Text<span style=\"color: #339933;\">&gt;</span> values,
    <span style=\"color: #003399;\">Context</span> context<span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #000000; font-weight: bold;\">throws</span> <span style=\"color:
    #003399;\">IOException</span>,\n\t\t\t\t<span style=\"color: #003399;\">InterruptedException</span>
    <span style=\"color: #009900;\">&#123;</span>\n\t\tIterator<span style=\"color:
    #339933;\">&lt;</span>Text<span style=\"color: #339933;\">&gt;</span> columns<span
    style=\"color: #339933;\">=</span>\tvalues.<span style=\"color: #006633;\">iterator</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n\t\tList<span style=\"color: #339933;\">&lt;</span>String<span
    style=\"color: #339933;\">&gt;</span> columnsList<span style=\"color: #339933;\">=</span><span
    style=\"color: #000000; font-weight: bold;\">new</span> ArrayList<span style=\"color:
    #339933;\">&lt;</span>String<span style=\"color: #339933;\">&gt;</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n\t\t<span style=\"color: #000000; font-weight: bold;\">while</span><span
    style=\"color: #009900;\">&#40;</span>columns.<span style=\"color: #006633;\">hasNext</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span>\n\t\t\tcolumnsList.<span style=\"color:
    #006633;\">add</span><span style=\"color: #009900;\">&#40;</span>columns.<span
    style=\"color: #006633;\">next</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span>.<span style=\"color: #006633;\">toString</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\t\n\t\t\tcontext.<span
    style=\"color: #006633;\">write</span><span style=\"color: #009900;\">&#40;</span>key,
    <span style=\"color: #000000; font-weight: bold;\">new</span> Text<span style=\"color:
    #009900;\">&#40;</span>columnsList.<span style=\"color: #006633;\">toString</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\n\t\t<span style=\"color: #009900;\">&#125;</span>\n&nbsp;\n\t<span
    style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">static class ColumnsReducer extends Reducer&lt;Text, Text,
    Text, Text&gt; {\r\n\r\n\t\tpublic void reduce(Text key, Iterable&lt;Text&gt;
    values, Context context) throws IOException,\r\n\t\t\t\tInterruptedException {\r\n\t\tIterator&lt;Text&gt;
    columns=\tvalues.iterator();\r\n\t\tList&lt;String&gt; columnsList=new ArrayList&lt;String&gt;();\r\n\t\twhile(columns.hasNext())\r\n\t\t\tcolumnsList.add(columns.next().toString());\t\r\n\t\t\tcontext.write(key,
    new Text(columnsList.toString()));\r\n\r\n\t\t}\r\n\r\n\t}</p></div>\n\";}"
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/get-hbase-columns-column-families/"
---
Get Hbase Columns with Column Families  
Hbase doesn't provide any client API to get all the column qualifiers. If your table has millions of rows and you need to get all the qualifiers then it takes very long time to get all columns by standalone program. Here is, map reduce job that will help you to get all columns with family.  
Prepare the Job Driver:

```
public static Job createSubmittableJob(Configuration conf, String[] args) throws IOException { String tableName =args[1]; conf.set("habse.table.name", args[1]); System.out.println("table: " + tableName); deletePath(conf, args[2]); Job job = new Job(conf, conf.get(JOB\_NAME\_CONF\_KEY, JOB\_NAME\_CONF\_KEY + "\_" + tableName)); // Need to add Hbase jars to job class path HBaseConfiguration.addHbaseResources(job.getConfiguration()); TableMapReduceUtil.addDependencyJars(job); TableMapReduceUtil.addDependencyJars(job.getConfiguration(), org.apache.hadoop.hbase.client.Put.class); job.setJarByClass(ColumnsCounter.class); Scan scan = new Scan(); scan.setCacheBlocks(false); // scan.addFamily(Bytes.toBytes(family)); TableMapReduceUtil.initTableMapperJob( tableName, scan, ColumnsMapper.class, Text.class, Text.class, job); job.setReducerClass(ColumnsReducer.class); //job.setNumReduceTasks(1); FileOutputFormat.setOutputPath(job, new Path(args[2])); return job; }
```

Mapper that emits the column family as key and value as qualifier:

```
static class ColumnsMapper extends TableMapper { @Override public void map(ImmutableBytesWritable row, Result values, Context context) throws IOException, InterruptedException { // emit every combination of column family and qualifiers for (Entry\> columnFamilyMap : values.getNoVersionMap().entrySet()) { for (Entry entry : columnFamilyMap.getValue().entrySet()) { String cQualifier = Bytes.toString(entry.getKey()); context.write(new Text(cQualifier), NullWritable.get()); } } } }
```

Reducer that returns the column family with all qualifier

```
static class ColumnsReducer extends Reducer { public void reduce(Text key, Iterable values, Context context) throws IOException, InterruptedException { Iterator columns= values.iterator(); List columnsList=new ArrayList(); while(columns.hasNext()) columnsList.add(columns.next().toString()); context.write(key, new Text(columnsList.toString())); } }
```

Full program at git([techsquids](https://github.com/rahul86s/techsquids/blob/master/map-reduce/src/main/java/com/ts/mapreduce/hbase/ColumnsCounter.java "git"))  
Related post: launch hbase mapreduce job [runjob](http://www.techsquids.com/?p=367 "mapr")

