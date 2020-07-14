---
layout: post
title: HBase Manager design example
date: 2015-08-23 05:05:41.000000000 -07:00
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
- hbase
- java
meta:
  _edit_last: '1'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: HBase Manager design example
  _yoast_wpseo_title: HBase Manager design example
  _yoast_wpseo_metadesc: HBase Manager design example
  _yoast_wpseo_linkdex: '77'
  dsq_thread_id: '4057729006'
  wp-syntax-cache-content: "a:1:{i:1;s:17820:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n9\n10\n11\n12\n13\n14\n15\n16\n17\n18\n19\n20\n21\n22\n23\n24\n25\n26\n27\n28\n29\n30\n31\n32\n33\n34\n35\n36\n37\n38\n39\n40\n41\n42\n43\n44\n45\n46\n47\n48\n49\n50\n51\n52\n53\n54\n55\n56\n57\n58\n59\n60\n61\n62\n63\n64\n65\n66\n67\n68\n69\n70\n71\n72\n73\n74\n75\n76\n77\n78\n79\n80\n81\n82\n83\n84\n85\n86\n87\n88\n89\n90\n91\n92\n93\n94\n95\n96\n97\n98\n99\n100\n101\n102\n103\n104\n105\n106\n107\n108\n109\n110\n</pre></td><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\"><span style=\"color:
    #000000; font-weight: bold;\">public</span> <span style=\"color: #000000; font-weight:
    bold;\">class</span> HBaseManager\n<span style=\"color: #009900;\">&#123;</span>\n
    \ <span style=\"color: #000000; font-weight: bold;\">private</span> <span style=\"color:
    #000000; font-weight: bold;\">static</span> Logger logger <span style=\"color:
    #339933;\">=</span> Logger.<span style=\"color: #006633;\">getLogger</span><span
    style=\"color: #009900;\">&#40;</span> HBaseManager.<span style=\"color: #000000;
    font-weight: bold;\">class</span> <span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n  <span style=\"color: #000000; font-weight:
    bold;\">private</span> HBaseAdmin admin<span style=\"color: #339933;\">;</span>\n
    \ <span style=\"color: #000000; font-weight: bold;\">private</span> HTablePool
    pool<span style=\"color: #339933;\">;</span>\n  <span style=\"color: #000000;
    font-weight: bold;\">private</span> Configuration conf<span style=\"color: #339933;\">;</span>\n&nbsp;\n
    \ <span style=\"color: #000000; font-weight: bold;\">public</span> HBaseManager<span
    style=\"color: #009900;\">&#40;</span> <span style=\"color: #003399;\">String</span>
    zkQuorumHost, <span style=\"color: #003399;\">String</span> zkQuorumPort <span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n
    \   <span style=\"color: #000000; font-weight: bold;\">super</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n    logger.<span style=\"color: #006633;\">info</span><span
    style=\"color: #009900;\">&#40;</span> <span style=\"color: #0000ff;\">&quot;Hbase
    is intializing&quot;</span> <span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n    <span style=\"color: #000000; font-weight:
    bold;\">try</span> <span style=\"color: #009900;\">&#123;</span>\n      logger.<span
    style=\"color: #006633;\">info</span><span style=\"color: #009900;\">&#40;</span>
    <span style=\"color: #0000ff;\">&quot;HBase Manager Constructor begin zkQuorumHost
    = &quot;</span> <span style=\"color: #339933;\">+</span> zkQuorumHost <span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n      conf <span
    style=\"color: #339933;\">=</span> HBaseConfiguration.<span style=\"color: #006633;\">create</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n      conf.<span style=\"color: #006633;\">set</span><span
    style=\"color: #009900;\">&#40;</span> <span style=\"color: #0000ff;\">&quot;zk.quorum.host&quot;</span>,
    zkQuorumHost <span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n      conf.<span style=\"color: #006633;\">set</span><span
    style=\"color: #009900;\">&#40;</span> <span style=\"color: #0000ff;\">&quot;zk.quorum.port&quot;</span>,
    zkQuorumPort <span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n      admin <span style=\"color: #339933;\">=</span> <span
    style=\"color: #000000; font-weight: bold;\">new</span> HBaseAdmin<span style=\"color:
    #009900;\">&#40;</span> conf <span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n      pool <span style=\"color: #339933;\">=</span>
    <span style=\"color: #000000; font-weight: bold;\">new</span> HTablePool<span
    style=\"color: #009900;\">&#40;</span> conf, <span style=\"color: #cc66cc;\">30</span>
    <span style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n
    \   <span style=\"color: #009900;\">&#125;</span> <span style=\"color: #000000;
    font-weight: bold;\">catch</span><span style=\"color: #009900;\">&#40;</span>
    MasterNotRunningException e <span style=\"color: #009900;\">&#41;</span> <span
    style=\"color: #009900;\">&#123;</span>\n       logger.<span style=\"color: #006633;\">error</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #0000ff;\">&quot;Master
    is Not Running &quot;</span> ,e <span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n    <span style=\"color: #009900;\">&#125;</span>
    <span style=\"color: #000000; font-weight: bold;\">catch</span><span style=\"color:
    #009900;\">&#40;</span> ZooKeeperConnectionException e <span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#123;</span>\n      logger.<span style=\"color:
    #006633;\">error</span><span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #0000ff;\">&quot;Zookeeper connection failed&quot;</span> ,e <span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n    <span style=\"color:
    #009900;\">&#125;</span>\n  <span style=\"color: #009900;\">&#125;</span>\n&nbsp;\n
    \ <span style=\"color: #000000; font-weight: bold;\">public</span> HTablePool
    getTablePool<span style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>\n
    \ <span style=\"color: #009900;\">&#123;</span>\n    <span style=\"color: #000000;
    font-weight: bold;\">return</span> pool<span style=\"color: #339933;\">;</span>\n
    \ <span style=\"color: #009900;\">&#125;</span>\n&nbsp;\n  <span style=\"color:
    #000000; font-weight: bold;\">public</span> <span style=\"color: #000066; font-weight:
    bold;\">boolean</span> closeTablePool<span style=\"color: #009900;\">&#40;</span>
    <span style=\"color: #003399;\">String</span> tableName <span style=\"color: #009900;\">&#41;</span>\n
    \   <span style=\"color: #000000; font-weight: bold;\">throws</span> <span style=\"color:
    #003399;\">IOException</span>\n  <span style=\"color: #009900;\">&#123;</span>\n
    \   pool.<span style=\"color: #006633;\">closeTablePool</span><span style=\"color:
    #009900;\">&#40;</span> tableName <span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n    <span style=\"color: #000000; font-weight:
    bold;\">return</span> <span style=\"color: #000066; font-weight: bold;\">true</span><span
    style=\"color: #339933;\">;</span>\n  <span style=\"color: #009900;\">&#125;</span>\n&nbsp;\n
    \ <span style=\"color: #000000; font-weight: bold;\">public</span> <span style=\"color:
    #000066; font-weight: bold;\">boolean</span> createTable<span style=\"color: #009900;\">&#40;</span>
    <span style=\"color: #003399;\">String</span> tableName, <span style=\"color:
    #003399;\">String</span> ... <span style=\"color: #006633;\">columnFamilies</span>
    <span style=\"color: #009900;\">&#41;</span>\n    <span style=\"color: #000000;
    font-weight: bold;\">throws</span> <span style=\"color: #003399;\">IOException</span>\n
    \ <span style=\"color: #009900;\">&#123;</span>\n    logger.<span style=\"color:
    #006633;\">info</span><span style=\"color: #009900;\">&#40;</span> <span style=\"color:
    #0000ff;\">&quot;Createing table&quot;</span> <span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n    HTableDescriptor table <span style=\"color:
    #339933;\">=</span> <span style=\"color: #000066; font-weight: bold;\">null</span><span
    style=\"color: #339933;\">;</span>\n    HColumnDescriptor columnFamily<span style=\"color:
    #339933;\">;</span>\n    <span style=\"color: #000066; font-weight: bold;\">int</span>
    maxversion <span style=\"color: #339933;\">=</span> <span style=\"color: #cc66cc;\">1</span><span
    style=\"color: #339933;\">;</span>\n    table <span style=\"color: #339933;\">=</span>
    <span style=\"color: #000000; font-weight: bold;\">new</span> HTableDescriptor<span
    style=\"color: #009900;\">&#40;</span> tableName <span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n    <span style=\"color: #000000; font-weight:
    bold;\">for</span><span style=\"color: #009900;\">&#40;</span> <span style=\"color:
    #003399;\">String</span> cf <span style=\"color: #339933;\">:</span> columnFamilies
    <span style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n
    \     columnFamily <span style=\"color: #339933;\">=</span> <span style=\"color:
    #000000; font-weight: bold;\">new</span> HColumnDescriptor<span style=\"color:
    #009900;\">&#40;</span> cf <span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n      columnFamily.<span style=\"color: #006633;\">setMaxVersions</span><span
    style=\"color: #009900;\">&#40;</span> maxversion <span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n      table.<span style=\"color: #006633;\">addFamily</span><span
    style=\"color: #009900;\">&#40;</span> columnFamily <span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n    <span style=\"color: #009900;\">&#125;</span>\n
    \   admin.<span style=\"color: #006633;\">createTable</span><span style=\"color:
    #009900;\">&#40;</span> table <span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n    <span style=\"color: #000000; font-weight:
    bold;\">return</span> <span style=\"color: #000066; font-weight: bold;\">true</span><span
    style=\"color: #339933;\">;</span>\n  <span style=\"color: #009900;\">&#125;</span>\n
    <span style=\"color: #000000; font-weight: bold;\">public</span> <span style=\"color:
    #000000; font-weight: bold;\">static</span> <span style=\"color: #000066; font-weight:
    bold;\">boolean</span> checkIfRunning<span style=\"color: #009900;\">&#40;</span>
    Configuration conf <span style=\"color: #009900;\">&#41;</span>\n    <span style=\"color:
    #000000; font-weight: bold;\">throws</span> MasterNotRunningException, ZooKeeperConnectionException\n
    \ <span style=\"color: #009900;\">&#123;</span>\n    HBaseAdmin.<span style=\"color:
    #006633;\">checkHBaseAvailable</span><span style=\"color: #009900;\">&#40;</span>
    conf <span style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n
    \   <span style=\"color: #000000; font-weight: bold;\">return</span> <span style=\"color:
    #000066; font-weight: bold;\">true</span><span style=\"color: #339933;\">;</span>\n
    \ <span style=\"color: #009900;\">&#125;</span>\n&nbsp;\n  <span style=\"color:
    #000000; font-weight: bold;\">public</span> <span style=\"color: #000066; font-weight:
    bold;\">boolean</span> checkIfRunning<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span>\n    <span style=\"color: #000000; font-weight:
    bold;\">throws</span> MasterNotRunningException, ZooKeeperConnectionException\n
    \ <span style=\"color: #009900;\">&#123;</span>\n    HBaseAdmin.<span style=\"color:
    #006633;\">checkHBaseAvailable</span><span style=\"color: #009900;\">&#40;</span>
    conf <span style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n
    \   <span style=\"color: #000000; font-weight: bold;\">return</span> <span style=\"color:
    #000066; font-weight: bold;\">true</span><span style=\"color: #339933;\">;</span>\n
    \ <span style=\"color: #009900;\">&#125;</span>\n&nbsp;\n  <span style=\"color:
    #008000; font-style: italic; font-weight: bold;\">/**\n   * Flush a table. Asynchronous
    operation\n   * @param table\n   *          to be flushed\n   * @throws IOException\n
    \  */</span>\n  <span style=\"color: #000000; font-weight: bold;\">public</span>
    <span style=\"color: #000066; font-weight: bold;\">void</span> flush<span style=\"color:
    #009900;\">&#40;</span> <span style=\"color: #003399;\">String</span> tableName
    <span style=\"color: #009900;\">&#41;</span>\n    <span style=\"color: #000000;
    font-weight: bold;\">throws</span> <span style=\"color: #003399;\">IOException</span>,
    <span style=\"color: #003399;\">InterruptedException</span>\n  <span style=\"color:
    #009900;\">&#123;</span>\n    admin.<span style=\"color: #006633;\">flush</span><span
    style=\"color: #009900;\">&#40;</span> tableName <span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n  <span style=\"color: #009900;\">&#125;</span>\n&nbsp;\n
    \ <span style=\"color: #008000; font-style: italic; font-weight: bold;\">/**\n
    \  * @param\n   * @return &lt;tt&gt;true &lt;/tt&gt;if table exists\n   * @throws
    IOException\n   */</span>\n  <span style=\"color: #000000; font-weight: bold;\">public</span>
    <span style=\"color: #000066; font-weight: bold;\">boolean</span> isTableExists<span
    style=\"color: #009900;\">&#40;</span> <span style=\"color: #003399;\">String</span>
    tableName <span style=\"color: #009900;\">&#41;</span>\n    <span style=\"color:
    #000000; font-weight: bold;\">throws</span> <span style=\"color: #003399;\">IOException</span>\n
    \ <span style=\"color: #009900;\">&#123;</span>\n    <span style=\"color: #000000;
    font-weight: bold;\">return</span> admin.<span style=\"color: #006633;\">tableExists</span><span
    style=\"color: #009900;\">&#40;</span> tableName <span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n  <span style=\"color: #009900;\">&#125;</span>\n&nbsp;\n
    \ <span style=\"color: #008000; font-style: italic; font-weight: bold;\">/**\n
    \  * @param tablename\n   * @return true if table available\n   * @throws IOException\n
    \  */</span>\n  <span style=\"color: #000000; font-weight: bold;\">public</span>
    <span style=\"color: #000066; font-weight: bold;\">boolean</span> isTableAvailable<span
    style=\"color: #009900;\">&#40;</span> <span style=\"color: #003399;\">String</span>
    tableName <span style=\"color: #009900;\">&#41;</span>\n    <span style=\"color:
    #000000; font-weight: bold;\">throws</span> <span style=\"color: #003399;\">IOException</span>\n
    \ <span style=\"color: #009900;\">&#123;</span>\n    <span style=\"color: #000000;
    font-weight: bold;\">return</span> admin.<span style=\"color: #006633;\">isTableAvailable</span><span
    style=\"color: #009900;\">&#40;</span> tableName.<span style=\"color: #006633;\">getBytes</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n
    \ <span style=\"color: #009900;\">&#125;</span>\n&nbsp;\n  <span style=\"color:
    #008000; font-style: italic; font-weight: bold;\">/**\n   * @return array of available
    tables\n   * @throws IOException\n   */</span>\n  <span style=\"color: #000000;
    font-weight: bold;\">public</span> HTableDescriptor<span style=\"color: #009900;\">&#91;</span><span
    style=\"color: #009900;\">&#93;</span> listTables<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span>\n    <span style=\"color: #000000; font-weight:
    bold;\">throws</span> <span style=\"color: #003399;\">IOException</span>\n  <span
    style=\"color: #009900;\">&#123;</span>\n    <span style=\"color: #000000; font-weight:
    bold;\">return</span> admin.<span style=\"color: #006633;\">listTables</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n  <span style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">public class HBaseManager\r\n{\r\n  private
    static Logger logger = Logger.getLogger( HBaseManager.class );\r\n  private HBaseAdmin
    admin;\r\n  private HTablePool pool;\r\n  private Configuration conf;\r\n\r\n
    \ public HBaseManager( String zkQuorumHost, String zkQuorumPort ) {\r\n    super();\r\n
    \   logger.info( &quot;Hbase is intializing&quot; );\r\n    try {\r\n      logger.info(
    &quot;HBase Manager Constructor begin zkQuorumHost = &quot; + zkQuorumHost );\r\n
    \     conf = HBaseConfiguration.create();\r\n      conf.set( &quot;zk.quorum.host&quot;,
    zkQuorumHost );\r\n      conf.set( &quot;zk.quorum.port&quot;, zkQuorumPort );\r\n
    \     admin = new HBaseAdmin( conf );\r\n      pool = new HTablePool( conf, 30
    );\r\n    } catch( MasterNotRunningException e ) {\r\n       logger.error(&quot;Master
    is Not Running &quot; ,e );\r\n    } catch( ZooKeeperConnectionException e ) {\r\n
    \     logger.error(&quot;Zookeeper connection failed&quot; ,e );\r\n    }\r\n
    \ }\r\n\r\n  public HTablePool getTablePool()\r\n  {\r\n    return pool;\r\n  }\r\n\r\n
    \ public boolean closeTablePool( String tableName )\r\n    throws IOException\r\n
    \ {\r\n    pool.closeTablePool( tableName );\r\n    return true;\r\n  }\r\n \r\n
    \ public boolean createTable( String tableName, String ... columnFamilies )\r\n
    \   throws IOException\r\n  {\r\n    logger.info( &quot;Createing table&quot;
    );\r\n    HTableDescriptor table = null;\r\n    HColumnDescriptor columnFamily;\r\n
    \   int maxversion = 1;\r\n    table = new HTableDescriptor( tableName );\r\n
    \   for( String cf : columnFamilies ) {\r\n      columnFamily = new HColumnDescriptor(
    cf );\r\n      columnFamily.setMaxVersions( maxversion );\r\n      table.addFamily(
    columnFamily );\r\n    }\r\n    admin.createTable( table );\r\n    return true;\r\n
    \ }\r\n public static boolean checkIfRunning( Configuration conf )\r\n    throws
    MasterNotRunningException, ZooKeeperConnectionException\r\n  {\r\n    HBaseAdmin.checkHBaseAvailable(
    conf );\r\n    return true;\r\n  }\r\n\r\n  public boolean checkIfRunning()\r\n
    \   throws MasterNotRunningException, ZooKeeperConnectionException\r\n  {\r\n
    \   HBaseAdmin.checkHBaseAvailable( conf );\r\n    return true;\r\n  }\r\n\r\n
    \ /**\r\n   * Flush a table. Asynchronous operation\r\n   * @param table\r\n   *
    \         to be flushed\r\n   * @throws IOException\r\n   */\r\n  public void
    flush( String tableName )\r\n    throws IOException, InterruptedException\r\n
    \ {\r\n    admin.flush( tableName );\r\n  }\r\n\r\n  /**\r\n   * @param\r\n   *
    @return &lt;tt&gt;true &lt;/tt&gt;if table exists\r\n   * @throws IOException\r\n
    \  */\r\n  public boolean isTableExists( String tableName )\r\n    throws IOException\r\n
    \ {\r\n    return admin.tableExists( tableName );\r\n  }\r\n\r\n  /**\r\n   *
    @param tablename\r\n   * @return true if table available\r\n   * @throws IOException\r\n
    \  */\r\n  public boolean isTableAvailable( String tableName )\r\n    throws IOException\r\n
    \ {\r\n    return admin.isTableAvailable( tableName.getBytes() );\r\n\r\n  }\r\n\r\n
    \ /**\r\n   * @return array of available tables\r\n   * @throws IOException\r\n
    \  */\r\n  public HTableDescriptor[] listTables()\r\n    throws IOException\r\n
    \ {\r\n    return admin.listTables();\r\n  }</p></div>\n\";}"
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/hbase-manager-design-example/"
---
HBase Manager design example

This post help you to design your hbase manager class which can have common hbase utility methods.

```
public class HBaseManager { private static Logger logger = Logger.getLogger( HBaseManager.class ); private HBaseAdmin admin; private HTablePool pool; private Configuration conf; public HBaseManager( String zkQuorumHost, String zkQuorumPort ) { super(); logger.info( "Hbase is intializing" ); try { logger.info( "HBase Manager Constructor begin zkQuorumHost = " + zkQuorumHost ); conf = HBaseConfiguration.create(); conf.set( "zk.quorum.host", zkQuorumHost ); conf.set( "zk.quorum.port", zkQuorumPort ); admin = new HBaseAdmin( conf ); pool = new HTablePool( conf, 30 ); } catch( MasterNotRunningException e ) { logger.error("Master is Not Running " ,e ); } catch( ZooKeeperConnectionException e ) { logger.error("Zookeeper connection failed" ,e ); } } public HTablePool getTablePool() { return pool; } public boolean closeTablePool( String tableName ) throws IOException { pool.closeTablePool( tableName ); return true; } public boolean createTable( String tableName, String ... columnFamilies ) throws IOException { logger.info( "Createing table" ); HTableDescriptor table = null; HColumnDescriptor columnFamily; int maxversion = 1; table = new HTableDescriptor( tableName ); for( String cf : columnFamilies ) { columnFamily = new HColumnDescriptor( cf ); columnFamily.setMaxVersions( maxversion ); table.addFamily( columnFamily ); } admin.createTable( table ); return true; } public static boolean checkIfRunning( Configuration conf ) throws MasterNotRunningException, ZooKeeperConnectionException { HBaseAdmin.checkHBaseAvailable( conf ); return true; } public boolean checkIfRunning() throws MasterNotRunningException, ZooKeeperConnectionException { HBaseAdmin.checkHBaseAvailable( conf ); return true; } /\*\* \* Flush a table. Asynchronous operation \* @param table \* to be flushed \* @throws IOException \*/ public void flush( String tableName ) throws IOException, InterruptedException { admin.flush( tableName ); } /\*\* \* @param \* @return <tt>true </tt>if table exists \* @throws IOException \*/ public boolean isTableExists( String tableName ) throws IOException { return admin.tableExists( tableName ); } /\*\* \* @param tablename \* @return true if table available \* @throws IOException \*/ public boolean isTableAvailable( String tableName ) throws IOException { return admin.isTableAvailable( tableName.getBytes() ); } /\*\* \* @return array of available tables \* @throws IOException \*/ public HTableDescriptor[] listTables() throws IOException { return admin.listTables(); }
```
