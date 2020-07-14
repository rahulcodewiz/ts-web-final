---
layout: post
title: Matrices Sum Map Reducer
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
  wp-syntax-cache-content: "a:3:{i:1;s:6763:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n9\n10\n11\n12\n13\n14\n15\n16\n17\n18\n19\n20\n</pre></td><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\"><span style=\"color:
    #000000; font-weight: bold;\">class</span> MatrixSumMapper <span style=\"color:
    #000000; font-weight: bold;\">extends</span>\nMapper<span style=\"color: #339933;\">&amp;</span>lt<span
    style=\"color: #339933;\">;</span>LongWritable, Text, LongWritable, Text<span
    style=\"color: #339933;\">&amp;</span>gt<span style=\"color: #339933;\">;</span>
    <span style=\"color: #009900;\">&#123;</span>\n<span style=\"color: #003399;\">String</span>
    fName <span style=\"color: #339933;\">=</span> <span style=\"color: #000066; font-weight:
    bold;\">null</span><span style=\"color: #339933;\">;</span>\n<span style=\"color:
    #000066; font-weight: bold;\">char</span> keySeprator<span style=\"color: #339933;\">;</span>\n@Override\n<span
    style=\"color: #000000; font-weight: bold;\">protected</span> <span style=\"color:
    #000066; font-weight: bold;\">void</span> setup<span style=\"color: #009900;\">&#40;</span>\nMapper<span
    style=\"color: #339933;\">&amp;</span>lt<span style=\"color: #339933;\">;</span>LongWritable,
    Text, LongWritable, Text<span style=\"color: #339933;\">&amp;</span>gt<span style=\"color:
    #339933;\">;</span>.<span style=\"color: #003399;\">Context</span> context<span
    style=\"color: #009900;\">&#41;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">throws</span> <span style=\"color: #003399;\">IOException</span>, <span
    style=\"color: #003399;\">InterruptedException</span> <span style=\"color: #009900;\">&#123;</span>\nfName
    <span style=\"color: #339933;\">=</span> <span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#40;</span>FileSplit<span style=\"color: #009900;\">&#41;</span>context.<span
    style=\"color: #006633;\">getInputSplit</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">getPath</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span>.<span style=\"color: #006633;\">getName</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\nkeySeprator<span style=\"color: #339933;\">=</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #000066; font-weight:
    bold;\">char</span><span style=\"color: #009900;\">&#41;</span>context.<span style=\"color:
    #006633;\">getConfiguration</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span>.<span style=\"color: #006633;\">getInt</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #0000ff;\">&quot;matrix.key.separator&quot;</span>,0x001<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n<span
    style=\"color: #009900;\">&#125;</span>\n@Override\n<span style=\"color: #000000;
    font-weight: bold;\">protected</span> <span style=\"color: #000066; font-weight:
    bold;\">void</span> map<span style=\"color: #009900;\">&#40;</span>LongWritable
    key, Text value,\nMapper<span style=\"color: #339933;\">&amp;</span>lt<span style=\"color:
    #339933;\">;</span>LongWritable, Text, LongWritable, Text<span style=\"color:
    #339933;\">&amp;</span>gt<span style=\"color: #339933;\">;</span>.<span style=\"color:
    #003399;\">Context</span> context<span style=\"color: #009900;\">&#41;</span>\n<span
    style=\"color: #000000; font-weight: bold;\">throws</span> <span style=\"color:
    #003399;\">IOException</span>, <span style=\"color: #003399;\">InterruptedException</span>
    <span style=\"color: #009900;\">&#123;</span>\nLongWritable keyM <span style=\"color:
    #339933;\">=</span> <span style=\"color: #000000; font-weight: bold;\">new</span>
    LongWritable<span style=\"color: #009900;\">&#40;</span><span style=\"color: #003399;\">Long</span>.<span
    style=\"color: #006633;\">parseLong</span><span style=\"color: #009900;\">&#40;</span>value.<span
    style=\"color: #006633;\">toString</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span>.<span style=\"color: #006633;\">split</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #003399;\">String</span>.<span
    style=\"color: #006633;\">format</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;%c&quot;</span>,keySeprator<span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #009900;\">&#91;</span><span style=\"color: #cc66cc;\">0</span><span style=\"color:
    #009900;\">&#93;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\nText val <span
    style=\"color: #339933;\">=</span> <span style=\"color: #000000; font-weight:
    bold;\">new</span> Text<span style=\"color: #009900;\">&#40;</span>value.<span
    style=\"color: #006633;\">toString</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span>.<span style=\"color: #006633;\">split</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #003399;\">String</span>.<span
    style=\"color: #006633;\">format</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;%c&quot;</span>,keySeprator<span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #009900;\">&#91;</span><span style=\"color: #cc66cc;\">1</span><span style=\"color:
    #009900;\">&#93;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\ncontext.<span style=\"color: #006633;\">write</span><span
    style=\"color: #009900;\">&#40;</span>keyM, val<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #009900;\">&#125;</span>\n<span
    style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">class MatrixSumMapper extends\r\nMapper&amp;lt;LongWritable,
    Text, LongWritable, Text&amp;gt; {\r\nString fName = null;\r\nchar keySeprator;\r\n@Override\r\nprotected
    void setup(\r\nMapper&amp;lt;LongWritable, Text, LongWritable, Text&amp;gt;.Context
    context)\r\nthrows IOException, InterruptedException {\r\nfName = ((FileSplit)context.getInputSplit()).getPath().getName();\r\nkeySeprator=(char)context.getConfiguration().getInt(&quot;matrix.key.separator&quot;,0x001);\r\n}\r\n@Override\r\nprotected
    void map(LongWritable key, Text value,\r\nMapper&amp;lt;LongWritable, Text, LongWritable,
    Text&amp;gt;.Context context)\r\nthrows IOException, InterruptedException {\r\nLongWritable
    keyM = new LongWritable(Long.parseLong(value.toString().split(String.format(&quot;%c&quot;,keySeprator))[0]));\r\nText
    val = new Text(value.toString().split(String.format(&quot;%c&quot;,keySeprator))[1]);\r\ncontext.write(keyM,
    val);\r\n}\r\n}</p></div>\n\";i:2;s:13727:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n9\n10\n11\n12\n13\n14\n15\n16\n17\n18\n19\n20\n21\n22\n23\n24\n25\n26\n27\n28\n29\n30\n31\n32\n33\n34\n35\n36\n37\n38\n39\n40\n41\n42\n43\n44\n45\n46\n47\n48\n</pre></td><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\"><span style=\"color:
    #000000; font-weight: bold;\">class</span> MatrixSumReducer <span style=\"color:
    #000000; font-weight: bold;\">extends</span>\nReducer<span style=\"color: #339933;\">&amp;</span>lt<span
    style=\"color: #339933;\">;</span>LongWritable, Text, LongWritable, Text<span
    style=\"color: #339933;\">&amp;</span>gt<span style=\"color: #339933;\">;</span>
    <span style=\"color: #009900;\">&#123;</span>\n<span style=\"color: #003399;\">String</span>
    vseparator<span style=\"color: #339933;\">;</span>\n<span style=\"color: #003399;\">String</span>
    fseparator<span style=\"color: #339933;\">;</span>\n<span style=\"color: #000000;
    font-weight: bold;\">private</span> <span style=\"color: #000000; font-weight:
    bold;\">static</span> Logger logger <span style=\"color: #339933;\">=</span> Logger.<span
    style=\"color: #006633;\">getLogger</span><span style=\"color: #009900;\">&#40;</span>MatrixSumMapper.<span
    style=\"color: #000000; font-weight: bold;\">class</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n@Override\n<span
    style=\"color: #000000; font-weight: bold;\">protected</span> <span style=\"color:
    #000066; font-weight: bold;\">void</span> setup<span style=\"color: #009900;\">&#40;</span>\nReducer<span
    style=\"color: #339933;\">&amp;</span>lt<span style=\"color: #339933;\">;</span>LongWritable,
    Text, LongWritable, Text<span style=\"color: #339933;\">&amp;</span>gt<span style=\"color:
    #339933;\">;</span>.<span style=\"color: #003399;\">Context</span> context<span
    style=\"color: #009900;\">&#41;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">throws</span> <span style=\"color: #003399;\">IOException</span>, <span
    style=\"color: #003399;\">InterruptedException</span> <span style=\"color: #009900;\">&#123;</span>\nlogger.<span
    style=\"color: #006633;\">debug</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;reducer- setup: begin&quot;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\nvseparator <span
    style=\"color: #339933;\">=</span> context.<span style=\"color: #006633;\">getConfiguration</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">get</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;matrix.element.separator&quot;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\nlogger.<span
    style=\"color: #006633;\">debug</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;reducer- setup: end&quot;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n<span style=\"color:
    #009900;\">&#125;</span>\n@Override\n<span style=\"color: #000000; font-weight:
    bold;\">protected</span> <span style=\"color: #000066; font-weight: bold;\">void</span>
    reduce<span style=\"color: #009900;\">&#40;</span>LongWritable key, Iterable value,\nReducer<span
    style=\"color: #339933;\">&amp;</span>lt<span style=\"color: #339933;\">;</span>LongWritable,
    Text, LongWritable, Text<span style=\"color: #339933;\">&amp;</span>gt<span style=\"color:
    #339933;\">;</span>.<span style=\"color: #003399;\">Context</span> ctxt<span style=\"color:
    #009900;\">&#41;</span>\n<span style=\"color: #000000; font-weight: bold;\">throws</span>
    <span style=\"color: #003399;\">IOException</span>, <span style=\"color: #003399;\">InterruptedException</span>
    <span style=\"color: #009900;\">&#123;</span>\nList<span style=\"color: #339933;\">&amp;</span>lt<span
    style=\"color: #339933;\">;</span><span style=\"color: #003399;\">Integer</span><span
    style=\"color: #009900;\">&#91;</span><span style=\"color: #009900;\">&#93;</span><span
    style=\"color: #339933;\">&amp;</span>gt<span style=\"color: #339933;\">;</span>
    matrixValues <span style=\"color: #339933;\">=</span> <span style=\"color: #000000;
    font-weight: bold;\">new</span> ArrayList<span style=\"color: #339933;\">&amp;</span>lt<span
    style=\"color: #339933;\">;</span><span style=\"color: #003399;\">Integer</span><span
    style=\"color: #009900;\">&#91;</span><span style=\"color: #009900;\">&#93;</span><span
    style=\"color: #339933;\">&amp;</span>gt<span style=\"color: #339933;\">;</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #003399;\">List</span>
    val <span style=\"color: #339933;\">=</span> <span style=\"color: #000000; font-weight:
    bold;\">new</span> <span style=\"color: #003399;\">ArrayList</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n<span style=\"color: #000000; font-weight: bold;\">for</span>
    <span style=\"color: #009900;\">&#40;</span>Text t <span style=\"color: #339933;\">:</span>
    value<span style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\nprepareKeyValueMap<span
    style=\"color: #009900;\">&#40;</span>t, matrixValues<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #009900;\">&#125;</span>\n<span
    style=\"color: #000000; font-weight: bold;\">for</span> <span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #003399;\">Integer</span><span style=\"color: #009900;\">&#91;</span><span
    style=\"color: #009900;\">&#93;</span> i <span style=\"color: #339933;\">:</span>
    matrixValues<span style=\"color: #009900;\">&#41;</span> <span style=\"color:
    #009900;\">&#123;</span>\n<span style=\"color: #000000; font-weight: bold;\">for</span>
    <span style=\"color: #009900;\">&#40;</span><span style=\"color: #000066; font-weight:
    bold;\">int</span> j <span style=\"color: #339933;\">=</span> <span style=\"color:
    #cc66cc;\">0</span><span style=\"color: #339933;\">;</span> j <span style=\"color:
    #339933;\">&amp;</span>lt<span style=\"color: #339933;\">;</span> i.<span style=\"color:
    #006633;\">length</span><span style=\"color: #339933;\">;</span> j<span style=\"color:
    #339933;\">++</span><span style=\"color: #009900;\">&#41;</span> <span style=\"color:
    #009900;\">&#123;</span>\n<span style=\"color: #000000; font-weight: bold;\">try</span><span
    style=\"color: #009900;\">&#123;</span>\n<span style=\"color: #000066; font-weight:
    bold;\">int</span> sum <span style=\"color: #339933;\">=</span> val.<span style=\"color:
    #006633;\">remove</span><span style=\"color: #009900;\">&#40;</span>j<span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\nval.<span style=\"color:
    #006633;\">add</span><span style=\"color: #009900;\">&#40;</span>j,sum<span style=\"color:
    #339933;\">+</span>i<span style=\"color: #009900;\">&#91;</span>j<span style=\"color:
    #009900;\">&#93;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n<span style=\"color: #009900;\">&#125;</span><span style=\"color:
    #000000; font-weight: bold;\">catch</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #003399;\">Exception</span> e<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#123;</span>\n<span style=\"color: #003399;\">System</span>.<span
    style=\"color: #006633;\">out</span>.<span style=\"color: #006633;\">println</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #0000ff;\">&quot;throwing
    exception&quot;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\nval.<span style=\"color: #006633;\">add</span><span style=\"color:
    #009900;\">&#40;</span>i<span style=\"color: #009900;\">&#91;</span>j<span style=\"color:
    #009900;\">&#93;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n<span style=\"color: #009900;\">&#125;</span>\n<span style=\"color:
    #009900;\">&#125;</span>\n<span style=\"color: #009900;\">&#125;</span>\nctxt.<span
    style=\"color: #006633;\">write</span><span style=\"color: #009900;\">&#40;</span>key,
    <span style=\"color: #000000; font-weight: bold;\">new</span> Text<span style=\"color:
    #009900;\">&#40;</span>val.<span style=\"color: #006633;\">toString</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #009900;\">&#125;</span>\n<span
    style=\"color: #000000; font-weight: bold;\">private</span> <span style=\"color:
    #000066; font-weight: bold;\">void</span> prepareKeyValueMap<span style=\"color:
    #009900;\">&#40;</span>Text value, List<span style=\"color: #339933;\">&amp;</span>lt<span
    style=\"color: #339933;\">;</span><span style=\"color: #003399;\">Integer</span><span
    style=\"color: #009900;\">&#91;</span><span style=\"color: #009900;\">&#93;</span><span
    style=\"color: #339933;\">&amp;</span>gt<span style=\"color: #339933;\">;</span>
    valuesLst<span style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n<span
    style=\"color: #003399;\">String</span><span style=\"color: #009900;\">&#91;</span><span
    style=\"color: #009900;\">&#93;</span> valuesStr <span style=\"color: #339933;\">=</span>
    value.<span style=\"color: #006633;\">toString</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span>.<span style=\"color: #006633;\">split</span><span
    style=\"color: #009900;\">&#40;</span>vseparator<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #003399;\">Integer</span><span
    style=\"color: #009900;\">&#91;</span><span style=\"color: #009900;\">&#93;</span>
    valuesInt <span style=\"color: #339933;\">=</span> <span style=\"color: #000000;
    font-weight: bold;\">new</span> <span style=\"color: #003399;\">Integer</span><span
    style=\"color: #009900;\">&#91;</span>valuesStr.<span style=\"color: #006633;\">length</span><span
    style=\"color: #009900;\">&#93;</span><span style=\"color: #339933;\">;</span>\n<span
    style=\"color: #000000; font-weight: bold;\">for</span> <span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #000066; font-weight: bold;\">int</span> i <span style=\"color:
    #339933;\">=</span> <span style=\"color: #cc66cc;\">0</span><span style=\"color:
    #339933;\">;</span> i <span style=\"color: #339933;\">&amp;</span>lt<span style=\"color:
    #339933;\">;</span> valuesStr.<span style=\"color: #006633;\">length</span><span
    style=\"color: #339933;\">;</span> i<span style=\"color: #339933;\">++</span><span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n<span
    style=\"color: #000000; font-weight: bold;\">try</span> <span style=\"color: #009900;\">&#123;</span>\nvaluesInt<span
    style=\"color: #009900;\">&#91;</span>i<span style=\"color: #009900;\">&#93;</span>
    <span style=\"color: #339933;\">=</span> <span style=\"color: #003399;\">Integer</span>.<span
    style=\"color: #006633;\">parseInt</span><span style=\"color: #009900;\">&#40;</span>valuesStr<span
    style=\"color: #009900;\">&#91;</span>i<span style=\"color: #009900;\">&#93;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n<span
    style=\"color: #009900;\">&#125;</span> <span style=\"color: #000000; font-weight:
    bold;\">catch</span> <span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #003399;\">NumberFormatException</span> e<span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#123;</span>\nlogger.<span style=\"color: #006633;\">error</span><span
    style=\"color: #009900;\">&#40;</span>e.<span style=\"color: #006633;\">getMessage</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n<span
    style=\"color: #009900;\">&#125;</span>\n<span style=\"color: #009900;\">&#125;</span>\nvaluesLst.<span
    style=\"color: #006633;\">add</span><span style=\"color: #009900;\">&#40;</span>valuesInt<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n<span
    style=\"color: #009900;\">&#125;</span>\n<span style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">class MatrixSumReducer extends\r\nReducer&amp;lt;LongWritable,
    Text, LongWritable, Text&amp;gt; {\r\nString vseparator;\r\nString fseparator;\r\nprivate
    static Logger logger = Logger.getLogger(MatrixSumMapper.class);\r\n@Override\r\nprotected
    void setup(\r\nReducer&amp;lt;LongWritable, Text, LongWritable, Text&amp;gt;.Context
    context)\r\nthrows IOException, InterruptedException {\r\nlogger.debug(&quot;reducer-
    setup: begin&quot;);\r\nvseparator = context.getConfiguration().get(&quot;matrix.element.separator&quot;);\r\nlogger.debug(&quot;reducer-
    setup: end&quot;);\r\n}\r\n@Override\r\nprotected void reduce(LongWritable key,
    Iterable value,\r\nReducer&amp;lt;LongWritable, Text, LongWritable, Text&amp;gt;.Context
    ctxt)\r\nthrows IOException, InterruptedException {\r\nList&amp;lt;Integer[]&amp;gt;
    matrixValues = new ArrayList&amp;lt;Integer[]&amp;gt;();\r\nList val = new ArrayList();\r\nfor
    (Text t : value) {\r\nprepareKeyValueMap(t, matrixValues);\r\n}\r\nfor (Integer[]
    i : matrixValues) {\r\nfor (int j = 0; j &amp;lt; i.length; j++) {\r\ntry{\r\nint
    sum = val.remove(j);\r\nval.add(j,sum+i[j]);\r\n}catch(Exception e){\r\nSystem.out.println(&quot;throwing
    exception&quot;);\r\nval.add(i[j]);\r\n}\r\n}\r\n}\r\nctxt.write(key, new Text(val.toString()));\r\n}\r\nprivate
    void prepareKeyValueMap(Text value, List&amp;lt;Integer[]&amp;gt; valuesLst) {\r\nString[]
    valuesStr = value.toString().split(vseparator);\r\nInteger[] valuesInt = new Integer[valuesStr.length];\r\nfor
    (int i = 0; i &amp;lt; valuesStr.length; i++) {\r\ntry {\r\nvaluesInt[i] = Integer.parseInt(valuesStr[i]);\r\n}
    catch (NumberFormatException e) {\r\nlogger.error(e.getMessage());\r\n}\r\n}\r\nvaluesLst.add(valuesInt);\r\n}\r\n}</p></div>\n\";i:3;s:11996:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n9\n10\n11\n12\n13\n14\n15\n16\n17\n18\n19\n20\n21\n22\n23\n24\n25\n26\n27\n28\n29\n30\n31\n32\n33\n34\n35\n36\n</pre></td><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\"><span style=\"color:
    #000000; font-weight: bold;\">public</span> <span style=\"color: #000000; font-weight:
    bold;\">class</span> <span style=\"color: #003399;\">Driver</span> <span style=\"color:
    #000000; font-weight: bold;\">extends</span> Configured <span style=\"color: #000000;
    font-weight: bold;\">implements</span> Tool <span style=\"color: #009900;\">&#123;</span>\n<span
    style=\"color: #000000; font-weight: bold;\">private</span> <span style=\"color:
    #000000; font-weight: bold;\">static</span> Logger logger <span style=\"color:
    #339933;\">=</span> Logger.<span style=\"color: #006633;\">getLogger</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #003399;\">Driver</span>.<span
    style=\"color: #000000; font-weight: bold;\">class</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n<span style=\"color:
    #000000; font-weight: bold;\">private</span> <span style=\"color: #000066; font-weight:
    bold;\">boolean</span> deleteDirectory<span style=\"color: #009900;\">&#40;</span>Path
    path<span style=\"color: #009900;\">&#41;</span> <span style=\"color: #000000;
    font-weight: bold;\">throws</span> <span style=\"color: #003399;\">IOException</span>
    <span style=\"color: #009900;\">&#123;</span>\nFileSystem fs <span style=\"color:
    #339933;\">=</span> FileSystem.<span style=\"color: #006633;\">get</span><span
    style=\"color: #009900;\">&#40;</span>getConf<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">return</span> fs.<span style=\"color: #006633;\">delete</span><span style=\"color:
    #009900;\">&#40;</span>path, <span style=\"color: #000066; font-weight: bold;\">true</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n<span
    style=\"color: #009900;\">&#125;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">public</span> <span style=\"color: #000066; font-weight: bold;\">int</span>
    run<span style=\"color: #009900;\">&#40;</span><span style=\"color: #003399;\">String</span><span
    style=\"color: #009900;\">&#91;</span><span style=\"color: #009900;\">&#93;</span>
    args<span style=\"color: #009900;\">&#41;</span> <span style=\"color: #000000;
    font-weight: bold;\">throws</span> <span style=\"color: #003399;\">Exception</span>
    <span style=\"color: #009900;\">&#123;</span>\nlogger.<span style=\"color: #006633;\">info</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #0000ff;\">&quot;job
    Matrix Sum Driver Begin&quot;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\nConfiguration conf <span style=\"color: #339933;\">=</span>
    getConf<span style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\nconf.<span style=\"color: #006633;\">setInt</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #0000ff;\">&quot;matrix.key.separator&quot;</span>,
    0x001<span style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\nconf.<span
    style=\"color: #006633;\">set</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;matrix.element.separator&quot;</span>,<span style=\"color:
    #0000ff;\">&quot;,&quot;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\nJob job <span style=\"color: #339933;\">=</span>
    <span style=\"color: #000000; font-weight: bold;\">new</span> Job<span style=\"color:
    #009900;\">&#40;</span>conf, <span style=\"color: #0000ff;\">&quot;Matrix Sum&quot;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\njob.<span
    style=\"color: #006633;\">setJarByClass</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #003399;\">Driver</span>.<span style=\"color: #000000; font-weight:
    bold;\">class</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\nPath input1 <span style=\"color: #339933;\">=</span> <span
    style=\"color: #000000; font-weight: bold;\">new</span> Path<span style=\"color:
    #009900;\">&#40;</span>args<span style=\"color: #009900;\">&#91;</span><span style=\"color:
    #cc66cc;\">0</span><span style=\"color: #009900;\">&#93;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\nPath input2 <span
    style=\"color: #339933;\">=</span> <span style=\"color: #000000; font-weight:
    bold;\">new</span> Path<span style=\"color: #009900;\">&#40;</span>args<span style=\"color:
    #009900;\">&#91;</span><span style=\"color: #cc66cc;\">1</span><span style=\"color:
    #009900;\">&#93;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\nPath output <span style=\"color: #339933;\">=</span> <span
    style=\"color: #000000; font-weight: bold;\">new</span> Path<span style=\"color:
    #009900;\">&#40;</span>args<span style=\"color: #009900;\">&#91;</span><span style=\"color:
    #cc66cc;\">2</span><span style=\"color: #009900;\">&#93;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\ndeleteDirectory<span
    style=\"color: #009900;\">&#40;</span>output<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\njob.<span style=\"color: #006633;\">setMapOutputKeyClass</span><span
    style=\"color: #009900;\">&#40;</span>LongWritable.<span style=\"color: #000000;
    font-weight: bold;\">class</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\njob.<span style=\"color: #006633;\">setMapOutputValueClass</span><span
    style=\"color: #009900;\">&#40;</span>Text.<span style=\"color: #000000; font-weight:
    bold;\">class</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\njob.<span style=\"color: #006633;\">setMapperClass</span><span
    style=\"color: #009900;\">&#40;</span>MatrixSumMapper.<span style=\"color: #000000;
    font-weight: bold;\">class</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\njob.<span style=\"color: #006633;\">setReducerClass</span><span
    style=\"color: #009900;\">&#40;</span>MatrixSumReducer.<span style=\"color: #000000;
    font-weight: bold;\">class</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\njob.<span style=\"color: #006633;\">setNumReduceTasks</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #cc66cc;\">1</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\njob.<span
    style=\"color: #006633;\">setInputFormatClass</span><span style=\"color: #009900;\">&#40;</span>TextInputFormat.<span
    style=\"color: #000000; font-weight: bold;\">class</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\njob.<span style=\"color:
    #006633;\">setOutputFormatClass</span><span style=\"color: #009900;\">&#40;</span>TextOutputFormat.<span
    style=\"color: #000000; font-weight: bold;\">class</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\nlogger.<span
    style=\"color: #006633;\">info</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;deleting output directory: &quot;</span> <span
    style=\"color: #339933;\">+</span> deleteDirectory<span style=\"color: #009900;\">&#40;</span>output<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\nFileInputFormat.<span style=\"color: #006633;\">setInputPaths</span><span
    style=\"color: #009900;\">&#40;</span>job, input1, input2<span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\nFileOutputFormat.<span
    style=\"color: #006633;\">setOutputPath</span><span style=\"color: #009900;\">&#40;</span>job,
    output<span style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n<span
    style=\"color: #000000; font-weight: bold;\">return</span> job.<span style=\"color:
    #006633;\">waitForCompletion</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #000066; font-weight: bold;\">true</span><span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #339933;\">?</span> <span style=\"color: #cc66cc;\">0</span>
    <span style=\"color: #339933;\">:</span> <span style=\"color: #cc66cc;\">1</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #009900;\">&#125;</span>\n<span
    style=\"color: #000000; font-weight: bold;\">public</span> <span style=\"color:
    #000000; font-weight: bold;\">static</span> <span style=\"color: #000066; font-weight:
    bold;\">void</span> main<span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #003399;\">String</span><span style=\"color: #009900;\">&#91;</span><span style=\"color:
    #009900;\">&#93;</span> args<span style=\"color: #009900;\">&#41;</span> <span
    style=\"color: #000000; font-weight: bold;\">throws</span> <span style=\"color:
    #003399;\">Exception</span> <span style=\"color: #009900;\">&#123;</span>\n<span
    style=\"color: #000000; font-weight: bold;\">for</span> <span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #003399;\">String</span> str <span style=\"color: #339933;\">:</span>
    args<span style=\"color: #009900;\">&#41;</span>\n<span style=\"color: #003399;\">System</span>.<span
    style=\"color: #006633;\">out</span>.<span style=\"color: #006633;\">println</span><span
    style=\"color: #009900;\">&#40;</span>str<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\nConfiguration config <span style=\"color:
    #339933;\">=</span> <span style=\"color: #000000; font-weight: bold;\">new</span>
    Configuration<span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n<span style=\"color:
    #003399;\">System</span>.<span style=\"color: #006633;\">exit</span><span style=\"color:
    #009900;\">&#40;</span>ToolRunner.<span style=\"color: #006633;\">run</span><span
    style=\"color: #009900;\">&#40;</span>config, <span style=\"color: #000000; font-weight:
    bold;\">new</span> <span style=\"color: #003399;\">Driver</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>, args<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #009900;\">&#125;</span>\n<span
    style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">public class Driver extends Configured implements Tool
    {\r\nprivate static Logger logger = Logger.getLogger(Driver.class);\r\nprivate
    boolean deleteDirectory(Path path) throws IOException {\r\nFileSystem fs = FileSystem.get(getConf());\r\nreturn
    fs.delete(path, true);\r\n}\r\npublic int run(String[] args) throws Exception
    {\r\nlogger.info(&quot;job Matrix Sum Driver Begin&quot;);\r\nConfiguration conf
    = getConf();\r\nconf.setInt(&quot;matrix.key.separator&quot;, 0x001);\r\nconf.set(&quot;matrix.element.separator&quot;,&quot;,&quot;);\r\nJob
    job = new Job(conf, &quot;Matrix Sum&quot;);\r\njob.setJarByClass(Driver.class);\r\nPath
    input1 = new Path(args[0]);\r\nPath input2 = new Path(args[1]);\r\nPath output
    = new Path(args[2]);\r\ndeleteDirectory(output);\r\njob.setMapOutputKeyClass(LongWritable.class);\r\njob.setMapOutputValueClass(Text.class);\r\njob.setMapperClass(MatrixSumMapper.class);\r\njob.setReducerClass(MatrixSumReducer.class);\r\njob.setNumReduceTasks(1);\r\njob.setInputFormatClass(TextInputFormat.class);\r\njob.setOutputFormatClass(TextOutputFormat.class);\r\nlogger.info(&quot;deleting
    output directory: &quot; + deleteDirectory(output));\r\nFileInputFormat.setInputPaths(job,
    input1, input2);\r\nFileOutputFormat.setOutputPath(job, output);\r\nreturn job.waitForCompletion(true)
    ? 0 : 1;\r\n}\r\npublic static void main(String[] args) throws Exception {\r\nfor
    (String str : args)\r\nSystem.out.println(str);\r\nConfiguration config = new
    Configuration();\r\nSystem.exit(ToolRunner.run(config, new Driver(), args));\r\n}\r\n}</p></div>\n\";}"
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/matrices-sum-map-reducer/"
---
 **Matrices Sum Map Reducer**  
Matrix sum is the operation of adding matrices by adding corresponding entries together.  
**Entrywise sum**  
The sum of two m × n (pronounced "m by n") matrices A and B, denoted by A + B, is again an m × n matrix computed by adding corresponding elements  
[![matraix sum]({{ site.baseurl }}/assets/images/matraix-sum-300x137.png)](http://www.techsquids.com/wp-content/uploads/2014/09/matraix-sum.png)

Entrywise sum implementation using Map-reduce-

I have two matrices in separate files ( check blog [indexing](http://www.techsquids.com/bd/indexing-using-map-reduce/ "indexing")for generating index), each file contains same size (m\*n) matrix. matrix row index(m) and values separated by ^A [0x001] and values(n) are separated by (,).

1. Mapper emits the row index as key and entire row as a value. If you have different types of matrices then create separate mappers to process/ filters the matrix.
```
class MatrixSumMapper extends Mapper\<LongWritable, Text, LongWritable, Text\> { String fName = null; char keySeprator; @Override protected void setup( Mapper\<LongWritable, Text, LongWritable, Text\>.Context context) throws IOException, InterruptedException { fName = ((FileSplit)context.getInputSplit()).getPath().getName(); keySeprator=(char)context.getConfiguration().getInt("matrix.key.separator",0x001); } @Override protected void map(LongWritable key, Text value, Mapper\<LongWritable, Text, LongWritable, Text\>.Context context) throws IOException, InterruptedException { LongWritable keyM = new LongWritable(Long.parseLong(value.toString().split(String.format("%c",keySeprator))[0])); Text val = new Text(value.toString().split(String.format("%c",keySeprator))[1]); context.write(keyM, val); } }
```
2. Reducer gets the row key as (m). Next split each value to generate (n) then add the values index and position wise.
```
class MatrixSumReducer extends Reducer\<LongWritable, Text, LongWritable, Text\> { String vseparator; String fseparator; private static Logger logger = Logger.getLogger(MatrixSumMapper.class); @Override protected void setup( Reducer\<LongWritable, Text, LongWritable, Text\>.Context context) throws IOException, InterruptedException { logger.debug("reducer- setup: begin"); vseparator = context.getConfiguration().get("matrix.element.separator"); logger.debug("reducer- setup: end"); } @Override protected void reduce(LongWritable key, Iterable value, Reducer\<LongWritable, Text, LongWritable, Text\>.Context ctxt) throws IOException, InterruptedException { List\<Integer[]\> matrixValues = new ArrayList\<Integer[]\>(); List val = new ArrayList(); for (Text t : value) { prepareKeyValueMap(t, matrixValues); } for (Integer[] i : matrixValues) { for (int j = 0; j \< i.length; j++) { try{ int sum = val.remove(j); val.add(j,sum+i[j]); }catch(Exception e){ System.out.println("throwing exception"); val.add(i[j]); } } } ctxt.write(key, new Text(val.toString())); } private void prepareKeyValueMap(Text value, List\<Integer[]\> valuesLst) { String[] valuesStr = value.toString().split(vseparator); Integer[] valuesInt = new Integer[valuesStr.length]; for (int i = 0; i \< valuesStr.length; i++) { try { valuesInt[i] = Integer.parseInt(valuesStr[i]); } catch (NumberFormatException e) { logger.error(e.getMessage()); } } valuesLst.add(valuesInt); } }
```
3. Driver code:
```
public class Driver extends Configured implements Tool { private static Logger logger = Logger.getLogger(Driver.class); private boolean deleteDirectory(Path path) throws IOException { FileSystem fs = FileSystem.get(getConf()); return fs.delete(path, true); } public int run(String[] args) throws Exception { logger.info("job Matrix Sum Driver Begin"); Configuration conf = getConf(); conf.setInt("matrix.key.separator", 0x001); conf.set("matrix.element.separator",","); Job job = new Job(conf, "Matrix Sum"); job.setJarByClass(Driver.class); Path input1 = new Path(args[0]); Path input2 = new Path(args[1]); Path output = new Path(args[2]); deleteDirectory(output); job.setMapOutputKeyClass(LongWritable.class); job.setMapOutputValueClass(Text.class); job.setMapperClass(MatrixSumMapper.class); job.setReducerClass(MatrixSumReducer.class); job.setNumReduceTasks(1); job.setInputFormatClass(TextInputFormat.class); job.setOutputFormatClass(TextOutputFormat.class); logger.info("deleting output directory: " + deleteDirectory(output)); FileInputFormat.setInputPaths(job, input1, input2); FileOutputFormat.setOutputPath(job, output); return job.waitForCompletion(true) ? 0 : 1; } public static void main(String[] args) throws Exception { for (String str : args) System.out.println(str); Configuration config = new Configuration(); System.exit(ToolRunner.run(config, new Driver(), args)); } }
```

check out the complete source code from [techsquids](https://github.com/rahul86s/techsquids.git "techsquids")

