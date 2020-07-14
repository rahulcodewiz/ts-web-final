---
layout: post
title: Pagination with Hbase
date: 2014-10-08 20:29:25.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Big Data
- java
tags:
- bigdata
- hbase
- java
meta:
  _edit_last: '1'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: Pagination with Hbase
  _yoast_wpseo_title: Pagination with Hbase
  _yoast_wpseo_metadesc: Pagination with Hbase. Backward/forward pagination. previous/next
    pagination hbase with java client. Reverse pagination with HBase
  _yoast_wpseo_linkdex: '79'
  dsq_thread_id: '3097187018'
  wp-syntax-cache-content: "a:5:{i:1;s:523:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\">Filter filter
    <span style=\"color: #339933;\">=</span> <span style=\"color: #000000; font-weight:
    bold;\">new</span> PageFilter<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #cc66cc;\">15</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span></pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">Filter filter = new PageFilter(15);</p></div>\n\";i:2;s:512:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"code\"><pre
    class=\"powershell\" style=\"font-family:monospace;\">create <span style=\"color:
    #800000;\">'PAGINATION'</span><span style=\"color: pink;\">,</span> <span style=\"color:
    #000000;\">&#123;</span>NAME <span style=\"color: pink;\">=&gt;</span> <span style=\"color:
    #800000;\">'CF'</span><span style=\"color: #000000;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">create 'PAGINATION', {NAME =&gt; 'CF'}</p></div>\n\";i:3;s:1334:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n</pre></td><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\"><span style=\"color:
    #000000; font-weight: bold;\">public</span> <span style=\"color: #000000; font-weight:
    bold;\">class</span> Pagination <span style=\"color: #009900;\">&#123;</span>\n
    \   <span style=\"color: #000000; font-weight: bold;\">protected</span> <span
    style=\"color: #000066; font-weight: bold;\">int</span> numberOfRecords<span style=\"color:
    #339933;\">;</span>\n    <span style=\"color: #000000; font-weight: bold;\">protected</span>
    <span style=\"color: #003399;\">String</span> startKey<span style=\"color: #339933;\">;</span>\n
    \   <span style=\"color: #000000; font-weight: bold;\">protected</span> <span
    style=\"color: #000066; font-weight: bold;\">int</span> pageNumber<span style=\"color:
    #339933;\">;</span>\n    <span style=\"color: #000000; font-weight: bold;\">protected</span>
    <span style=\"color: #003399;\">String</span> scrollingType<span style=\"color:
    #339933;\">;</span>\n<span style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">public class Pagination {\r\n    protected
    int numberOfRecords;\r\n    protected String startKey;\r\n    protected int pageNumber;\r\n
    \   protected String scrollingType;\r\n}</p></div>\n\";i:4;s:7366:\"\n<div class=\"wp_syntax\"
    style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n9\n10\n11\n12\n13\n14\n15\n16\n17\n18\n19\n20\n</pre></td><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\"> <span style=\"color:
    #000000; font-weight: bold;\">public</span> <span style=\"color: #000066; font-weight:
    bold;\">void</span> put<span style=\"color: #009900;\">&#40;</span> <span style=\"color:
    #003399;\">String</span> key, Pagination pagination <span style=\"color: #009900;\">&#41;</span>\n
    \     <span style=\"color: #000000; font-weight: bold;\">throws</span> DAOException\n
    \   <span style=\"color: #009900;\">&#123;</span>\n      HTableInterface table
    <span style=\"color: #339933;\">=</span> <span style=\"color: #000066; font-weight:
    bold;\">null</span><span style=\"color: #339933;\">;</span>\n      <span style=\"color:
    #000000; font-weight: bold;\">try</span> <span style=\"color: #009900;\">&#123;</span>\n
    \       table <span style=\"color: #339933;\">=</span> getTable<span style=\"color:
    #009900;\">&#40;</span>  <span style=\"color: #0000ff;\">&quot;PAGINATION&quot;</span>
    \ <span style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n
    \       Put put <span style=\"color: #339933;\">=</span> <span style=\"color:
    #000000; font-weight: bold;\">new</span> Put<span style=\"color: #009900;\">&#40;</span>
    Bytes.<span style=\"color: #006633;\">toBytes</span><span style=\"color: #009900;\">&#40;</span>
    key <span style=\"color: #339933;\">+</span> <span style=\"color: #0000ff;\">&quot;_&quot;</span>
    <span style=\"color: #339933;\">+</span> pagination.<span style=\"color: #006633;\">getNumberOfRecords</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n        put.<span style=\"color: #006633;\">add</span><span
    style=\"color: #009900;\">&#40;</span> Bytes.<span style=\"color: #006633;\">toBytes</span><span
    style=\"color: #009900;\">&#40;</span> <span style=\"color: #0000ff;\">&quot;CF&quot;</span><span
    style=\"color: #009900;\">&#41;</span>, Bytes.<span style=\"color: #006633;\">toBytes</span><span
    style=\"color: #009900;\">&#40;</span> pagination.<span style=\"color: #006633;\">getPrevPageNumber</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#41;</span>, Bytes.<span style=\"color: #006633;\">toBytes</span><span
    style=\"color: #009900;\">&#40;</span> pagination.<span style=\"color: #006633;\">getStartKey</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n        put.<span style=\"color: #006633;\">add</span><span
    style=\"color: #009900;\">&#40;</span> Bytes.<span style=\"color: #006633;\">toBytes</span><span
    style=\"color: #009900;\">&#40;</span> <span style=\"color: #0000ff;\">&quot;CF&quot;</span><span
    style=\"color: #009900;\">&#41;</span>, Bytes.<span style=\"color: #006633;\">toBytes</span><span
    style=\"color: #009900;\">&#40;</span> <span style=\"color: #0000ff;\">&quot;LAST_ACCESSED&quot;</span>
    <span style=\"color: #009900;\">&#41;</span>, Bytes.<span style=\"color: #006633;\">toBytes</span><span
    style=\"color: #009900;\">&#40;</span> <span style=\"color: #003399;\">System</span>.<span
    style=\"color: #006633;\">currentTimeMillis</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n
    \       table.<span style=\"color: #006633;\">put</span><span style=\"color: #009900;\">&#40;</span>
    put <span style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n
    \     <span style=\"color: #009900;\">&#125;</span> <span style=\"color: #000000;
    font-weight: bold;\">catch</span><span style=\"color: #009900;\">&#40;</span>
    <span style=\"color: #003399;\">IOException</span> e <span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#123;</span>\n        <span style=\"color: #003399;\">StringWriter</span>
    sw <span style=\"color: #339933;\">=</span> <span style=\"color: #000000; font-weight:
    bold;\">new</span> <span style=\"color: #003399;\">StringWriter</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n        e.<span style=\"color: #006633;\">printStackTrace</span><span
    style=\"color: #009900;\">&#40;</span> <span style=\"color: #000000; font-weight:
    bold;\">new</span> <span style=\"color: #003399;\">PrintWriter</span><span style=\"color:
    #009900;\">&#40;</span> sw <span style=\"color: #009900;\">&#41;</span> <span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n
    \       logger.<span style=\"color: #006633;\">error</span><span style=\"color:
    #009900;\">&#40;</span> sw.<span style=\"color: #006633;\">toString</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n
    \       <span style=\"color: #000000; font-weight: bold;\">throw</span> <span
    style=\"color: #000000; font-weight: bold;\">new</span> DAOException<span style=\"color:
    #009900;\">&#40;</span> <span style=\"color: #0000ff;\">&quot;Failed to update:
    &quot;</span> <span style=\"color: #339933;\">+</span> e.<span style=\"color:
    #006633;\">getMessage</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n      <span style=\"color: #009900;\">&#125;</span>
    <span style=\"color: #000000; font-weight: bold;\">finally</span> <span style=\"color:
    #009900;\">&#123;</span>\n        closeResources<span style=\"color: #009900;\">&#40;</span>
    table <span style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n
    \     <span style=\"color: #009900;\">&#125;</span>\n      logger.<span style=\"color:
    #006633;\">info</span><span style=\"color: #009900;\">&#40;</span> <span style=\"color:
    #0000ff;\">&quot;WSPagination.put: end&quot;</span> <span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n    <span style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\"> public void put( String key, Pagination
    pagination )\r\n      throws DAOException\r\n    {\r\n      HTableInterface table
    = null;\r\n      try {\r\n        table = getTable(  &quot;PAGINATION&quot;  );\r\n
    \       Put put = new Put( Bytes.toBytes( key + &quot;_&quot; + pagination.getNumberOfRecords()
    ) );\r\n        put.add( Bytes.toBytes( &quot;CF&quot;), Bytes.toBytes( pagination.getPrevPageNumber()
    ), Bytes.toBytes( pagination.getStartKey() ) );\r\n        put.add( Bytes.toBytes(
    &quot;CF&quot;), Bytes.toBytes( &quot;LAST_ACCESSED&quot; ), Bytes.toBytes( System.currentTimeMillis()
    ) );\r\n        table.put( put );\r\n      } catch( IOException e ) {\r\n        StringWriter
    sw = new StringWriter();\r\n        e.printStackTrace( new PrintWriter( sw ) );\r\n
    \       logger.error( sw.toString() );\r\n        throw new DAOException( &quot;Failed
    to update: &quot; + e.getMessage() );\r\n      } finally {\r\n        closeResources(
    table );\r\n      }\r\n      logger.info( &quot;WSPagination.put: end&quot; );\r\n
    \   }</p></div>\n\";i:5;s:8789:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n9\n10\n11\n12\n13\n14\n15\n16\n17\n18\n19\n20\n21\n22\n23\n</pre></td><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\"> <span style=\"color:
    #000000; font-weight: bold;\">public</span> <span style=\"color: #003399;\">String</span>
    get<span style=\"color: #009900;\">&#40;</span> <span style=\"color: #003399;\">String</span>
    key, Pagination pagination <span style=\"color: #009900;\">&#41;</span>\n      <span
    style=\"color: #000000; font-weight: bold;\">throws</span> DAOException\n    <span
    style=\"color: #009900;\">&#123;</span>\n      HTableInterface table <span style=\"color:
    #339933;\">=</span> <span style=\"color: #000066; font-weight: bold;\">null</span><span
    style=\"color: #339933;\">;</span>\n      <span style=\"color: #003399;\">String</span>
    resultStr <span style=\"color: #339933;\">=</span> <span style=\"color: #000066;
    font-weight: bold;\">null</span><span style=\"color: #339933;\">;</span>\n      <span
    style=\"color: #000000; font-weight: bold;\">try</span> <span style=\"color: #009900;\">&#123;</span>\n
    \       table <span style=\"color: #339933;\">=</span> getTable<span style=\"color:
    #009900;\">&#40;</span>  <span style=\"color: #0000ff;\">&quot;PAGINATION&quot;</span>
    \ <span style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n
    \       logger.<span style=\"color: #006633;\">debug</span><span style=\"color:
    #009900;\">&#40;</span> <span style=\"color: #0000ff;\">&quot;get key:&quot;</span>
    <span style=\"color: #339933;\">+</span> key <span style=\"color: #339933;\">+</span>
    DatabaseConstants.<span style=\"color: #006633;\">FIELD_DELIMITER_TRANS</span>
    <span style=\"color: #339933;\">+</span> pagination.<span style=\"color: #006633;\">getNumberOfRecords</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #339933;\">+</span> <span style=\"color: #0000ff;\">&quot;page:
    &quot;</span>\n          <span style=\"color: #339933;\">+</span> <span style=\"color:
    #009900;\">&#40;</span> pagination.<span style=\"color: #006633;\">getPrevPageNumber</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n        Get get <span style=\"color: #339933;\">=</span>
    <span style=\"color: #000000; font-weight: bold;\">new</span> Get<span style=\"color:
    #009900;\">&#40;</span> Bytes.<span style=\"color: #006633;\">toBytes</span><span
    style=\"color: #009900;\">&#40;</span> key <span style=\"color: #339933;\">+</span>
    <span style=\"color: #0000ff;\">&quot;_&quot;</span><span style=\"color: #339933;\">+</span>
    pagination.<span style=\"color: #006633;\">getNumberOfRecords</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span> <span style=\"color:
    #009900;\">&#41;</span> <span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n        get.<span style=\"color: #006633;\">addColumn</span><span
    style=\"color: #009900;\">&#40;</span> Bytes.<span style=\"color: #006633;\">toBytes</span><span
    style=\"color: #009900;\">&#40;</span> <span style=\"color: #0000ff;\">&quot;CF&quot;</span><span
    style=\"color: #009900;\">&#41;</span>, Bytes.<span style=\"color: #006633;\">toBytes</span><span
    style=\"color: #009900;\">&#40;</span> pagination.<span style=\"color: #006633;\">getPrevPageNumber</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n        Result result <span style=\"color:
    #339933;\">=</span> table.<span style=\"color: #006633;\">get</span><span style=\"color:
    #009900;\">&#40;</span> get <span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n        resultStr <span style=\"color: #339933;\">=</span>
    <span style=\"color: #009900;\">&#40;</span> result <span style=\"color: #339933;\">==</span>
    <span style=\"color: #000066; font-weight: bold;\">null</span> <span style=\"color:
    #339933;\">||</span> result.<span style=\"color: #006633;\">isEmpty</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#41;</span> <span style=\"color: #339933;\">?</span>
    <span style=\"color: #000066; font-weight: bold;\">null</span> <span style=\"color:
    #339933;\">:</span> Bytes.<span style=\"color: #006633;\">toString</span><span
    style=\"color: #009900;\">&#40;</span> result.<span style=\"color: #006633;\">getValue</span><span
    style=\"color: #009900;\">&#40;</span>\n          Bytes.<span style=\"color: #006633;\">toBytes</span><span
    style=\"color: #009900;\">&#40;</span> WS_PAGINATION.<span style=\"color: #006633;\">FAMILY</span>
    <span style=\"color: #009900;\">&#41;</span>, Bytes.<span style=\"color: #006633;\">toBytes</span><span
    style=\"color: #009900;\">&#40;</span> pagination.<span style=\"color: #006633;\">getPrevPageNumber</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n
    \     <span style=\"color: #009900;\">&#125;</span> <span style=\"color: #000000;
    font-weight: bold;\">catch</span><span style=\"color: #009900;\">&#40;</span>
    <span style=\"color: #003399;\">Exception</span> e <span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#123;</span>\n        <span style=\"color: #003399;\">StringWriter</span>
    sw <span style=\"color: #339933;\">=</span> <span style=\"color: #000000; font-weight:
    bold;\">new</span> <span style=\"color: #003399;\">StringWriter</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n        e.<span style=\"color: #006633;\">printStackTrace</span><span
    style=\"color: #009900;\">&#40;</span> <span style=\"color: #000000; font-weight:
    bold;\">new</span> <span style=\"color: #003399;\">PrintWriter</span><span style=\"color:
    #009900;\">&#40;</span> sw <span style=\"color: #009900;\">&#41;</span> <span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n
    \       <span style=\"color: #000000; font-weight: bold;\">throw</span> <span
    style=\"color: #000000; font-weight: bold;\">new</span> DAOException<span style=\"color:
    #009900;\">&#40;</span> <span style=\"color: #0000ff;\">&quot;Failed to get Number:
    &quot;</span> <span style=\"color: #339933;\">+</span> resultStr <span style=\"color:
    #339933;\">+</span> <span style=\"color: #0000ff;\">&quot;<span style=\"color:
    #000099; font-weight: bold;\">\\t</span> error: &quot;</span> <span style=\"color:
    #339933;\">+</span> e.<span style=\"color: #006633;\">getMessage</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span> <span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n      <span style=\"color:
    #009900;\">&#125;</span> <span style=\"color: #000000; font-weight: bold;\">finally</span>
    <span style=\"color: #009900;\">&#123;</span>\n        closeResources<span style=\"color:
    #009900;\">&#40;</span> table <span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n      <span style=\"color: #009900;\">&#125;</span>\n
    \     <span style=\"color: #000000; font-weight: bold;\">return</span> resultStr<span
    style=\"color: #339933;\">;</span>\n    <span style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\"> public String get( String key, Pagination
    pagination )\r\n      throws DAOException\r\n    {\r\n      HTableInterface table
    = null;\r\n      String resultStr = null;\r\n      try {\r\n        table = getTable(
    \ &quot;PAGINATION&quot;  );\r\n        logger.debug( &quot;get key:&quot; + key
    + DatabaseConstants.FIELD_DELIMITER_TRANS + pagination.getNumberOfRecords() +
    &quot;page: &quot;\r\n          + ( pagination.getPrevPageNumber() ) );\r\n        Get
    get = new Get( Bytes.toBytes( key + &quot;_&quot;+ pagination.getNumberOfRecords()
    ) );\r\n        get.addColumn( Bytes.toBytes( &quot;CF&quot;), Bytes.toBytes(
    pagination.getPrevPageNumber() ) );\r\n        Result result = table.get( get
    );\r\n        resultStr = ( result == null || result.isEmpty() ) ? null : Bytes.toString(
    result.getValue(\r\n          Bytes.toBytes( WS_PAGINATION.FAMILY ), Bytes.toBytes(
    pagination.getPrevPageNumber() ) ) );\r\n      } catch( Exception e ) {\r\n        StringWriter
    sw = new StringWriter();\r\n        e.printStackTrace( new PrintWriter( sw ) );\r\n
    \       throw new DAOException( &quot;Failed to get Number: &quot; + resultStr
    + &quot;\\t error: &quot; + e.getMessage() );\r\n      } finally {\r\n        closeResources(
    table );\r\n      }\r\n      return resultStr;\r\n    }</p></div>\n\";}"
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/pagination-with-hbase/"
---
 **Pagination with Hbase**

Pagefilter is use for pagination and it controls how many row per page should be returned.

```
Filter filter = new PageFilter(15);
```

Hbase pagination always work in forward direction, there are no way to go reverse or in backward direction.

suppose you need to implement functionality at UI pagination table and it should have next/forward and back/backward feature.

Forward option easily implemented using PageFilter but for backward, no solution. e.g. you need to get the rows(20) from end key to most recent and going backward. eg. backward get all records 1000 - 980.  
Unless your rows are predictable (you know how many rows between row key 0 and row key 2^32) reverse scanning won't even matter but If the rows are unpredictable, you would always have to scan the entire set to find out how many pages there and get the particular range start and stop row key.

I worked on similar use case, alternate solutions can be if your dataset is very huge-

1. Secondary index table-

each insert into main table, create a entry into secondary table that's sorted in reverse order. whenever request comes for scan in backward, scan the reverse/ index table for number of rows then use the returned start and stop row key to query on actual table.

2. Pagination table-

create a new hbase table with one cf family.

```
create 'PAGINATION', {NAME =\> 'CF'}
```

Create java bean-

```
public class Pagination { protected int numberOfRecords; protected String startKey; protected int pageNumber; protected String scrollingType; }
```

scrolling type is forward/backward.

for each forward search, create an entry into pagination table with row key 'search criteria'+numberOfRecords from pagination bean, column qualifier 'CF:pageNumber' and value is start key of set.

```
public void put( String key, Pagination pagination ) throws DAOException { HTableInterface table = null; try { table = getTable( "PAGINATION" ); Put put = new Put( Bytes.toBytes( key + "\_" + pagination.getNumberOfRecords() ) ); put.add( Bytes.toBytes( "CF"), Bytes.toBytes( pagination.getPrevPageNumber() ), Bytes.toBytes( pagination.getStartKey() ) ); put.add( Bytes.toBytes( "CF"), Bytes.toBytes( "LAST\_ACCESSED" ), Bytes.toBytes( System.currentTimeMillis() ) ); table.put( put ); } catch( IOException e ) { StringWriter sw = new StringWriter(); e.printStackTrace( new PrintWriter( sw ) ); logger.error( sw.toString() ); throw new DAOException( "Failed to update: " + e.getMessage() ); } finally { closeResources( table ); } logger.info( "WSPagination.put: end" ); }
```

if required, maintain the last accessed extra column for clean up job that clean up the table periodically.  
whenever request comes for scan in backward, get the start key from pagination table using 'search criteria'+numberOfRecords and pageNumber, then search on actual table. each requests should contains pagination bean.

```
public String get( String key, Pagination pagination ) throws DAOException { HTableInterface table = null; String resultStr = null; try { table = getTable( "PAGINATION" ); logger.debug( "get key:" + key + DatabaseConstants.FIELD\_DELIMITER\_TRANS + pagination.getNumberOfRecords() + "page: " + ( pagination.getPrevPageNumber() ) ); Get get = new Get( Bytes.toBytes( key + "\_"+ pagination.getNumberOfRecords() ) ); get.addColumn( Bytes.toBytes( "CF"), Bytes.toBytes( pagination.getPrevPageNumber() ) ); Result result = table.get( get ); resultStr = ( result == null || result.isEmpty() ) ? null : Bytes.toString( result.getValue( Bytes.toBytes( WS\_PAGINATION.FAMILY ), Bytes.toBytes( pagination.getPrevPageNumber() ) ) ); } catch( Exception e ) { StringWriter sw = new StringWriter(); e.printStackTrace( new PrintWriter( sw ) ); throw new DAOException( "Failed to get Number: " + resultStr + "\t error: " + e.getMessage() ); } finally { closeResources( table ); } return resultStr; }
```
