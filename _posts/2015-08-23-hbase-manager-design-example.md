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

author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/hbase-manager-design-example/"
---
## HBase Manager design example

This post help you to design your hbase manager class which can have common hbase utility methods.

```java 
public class HBaseManager { private static Logger logger = Logger.getLogger( HBaseManager.class );
 private HBaseAdmin admin;
 private HTablePool pool;
 private Configuration conf;
 public HBaseManager( String zkQuorumHost, String zkQuorumPort ) { super();
 logger.info( "Hbase is intializing" );
 try { logger.info( "HBase Manager Constructor begin zkQuorumHost = " + zkQuorumHost );
 conf = HBaseConfiguration.create();
 conf.set( "zk.quorum.host", zkQuorumHost );
 conf.set( "zk.quorum.port", zkQuorumPort );
 admin = new HBaseAdmin( conf );
 pool = new HTablePool( conf, 30 );
 } catch( MasterNotRunningException e ) { logger.error("Master is Not Running " ,e );
 } catch( ZooKeeperConnectionException e ) { logger.error("Zookeeper connection failed" ,e );
 } } public HTablePool getTablePool() { return pool;
 } public boolean closeTablePool( String tableName ) throws IOException { pool.closeTablePool( tableName );
 return true;
 } public boolean createTable( String tableName, String ... columnFamilies ) throws IOException { logger.info( "Createing table" );
 HTableDescriptor table = null;
 HColumnDescriptor columnFamily;
 int maxversion = 1;
 table = new HTableDescriptor( tableName );
 for( String cf : columnFamilies ) { columnFamily = new HColumnDescriptor( cf );
 columnFamily.setMaxVersions( maxversion );
 table.addFamily( columnFamily );
 } admin.createTable( table );
 return true;
 } public static boolean checkIfRunning( Configuration conf ) throws MasterNotRunningException, ZooKeeperConnectionException { HBaseAdmin.checkHBaseAvailable( conf );
 return true;
 } public boolean checkIfRunning() throws MasterNotRunningException, ZooKeeperConnectionException { HBaseAdmin.checkHBaseAvailable( conf );
 return true;
 } /\*\* \* Flush a table. Asynchronous operation \* @param table \* to be flushed \* @throws IOException \*/ public void flush( String tableName ) throws IOException, InterruptedException { admin.flush( tableName );
 } /\*\* \* @param \* @return <tt>true </tt>if table exists \* @throws IOException \*/ public boolean isTableExists( String tableName ) throws IOException { return admin.tableExists( tableName );
 } /\*\* \* @param tablename \* @return true if table available \* @throws IOException \*/ public boolean isTableAvailable( String tableName ) throws IOException { return admin.isTableAvailable( tableName.getBytes() );
 } /\*\* \* @return array of available tables \* @throws IOException \*/ public HTableDescriptor[] listTables() throws IOException { return admin.listTables();
 }
```
