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
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/pagination-with-hbase/"
---
# HBase Pagination for Both Forward and Backward Navigation

HBase is a powerful, distributed, and scalable NoSQL database system, known for its ability to handle massive amounts of data efficiently. When working with HBase, it's common to use the PageFilter for pagination, allowing you to control the number of rows returned for a given request. However, one limitation with the PageFilter is that it only supports forward pagination, and there's no built-in solution for backward navigation. This can be quite challenging when you want to implement a UI table with both forward and backward navigation features. In this blog post, we'll explore a workaround for this limitation.


Hbase uses the Pagefilter for the pagination and it controls how many row to return for a request. The pagination always work in forward direction what that means the reverse or backward direction option isn't possible. Suppose that you need to implement functionality at UI pagination table which allows users to have forward and backward features.

Forward option easily implemented using the PageFilter but for backward, no solution. e.g. you need to get the rows(20) from end key to most recent and going backward. eg. backward get all records 1000 - 980.  
Unless your rows are predictable (you know how many rows between row key 0 and row key 2^32) reverse scanning won't even matter but If the rows are unpredictable, you would always have to scan the entire set to find out how many pages there and get the particular range start and stop row key.

Simple Page filter declaration:

```
Filter filter = new PageFilter(15);
```

I solution this problem by creating parallel table and downside of this approach is that duplicate copies for dataset and edit might increase further complexcities-

1. Secondary index table-

So, each insert into main table, create a entry into secondary table that's sorted in reverse order. whenever request comes for scan in backward, scan the reverse/ index table for number of rows then use the returned start and stop row key to query on actual table.

2. Pagination table-

create a new hbase table with one cf family.

```bash
create 'PAGINATION', {NAME =\> 'CF'}
```

Java bean declaration for Pagination-

```java
public class Pagination {
   protected int numberOfRecords; 
   protected String startKey; 
   protected int pageNumber; 
   protected String scrollingType; }
```

Now, you can have scrolling type as forward and backward.

For each forward search, create an entry into pagination table with row key `search criteria` and numberOfRecords from pagination bean, column qualifier 'CF:pageNumber' and value is start key of set.

Java implementation: 

```java
public void put( String key, Pagination pagination ) throws DAOException { 
  HTableInterface table = null; 
  try { 
      table = getTable( "PAGINATION" ); 
      Put put = new Put( Bytes.toBytes( key + "\_" + pagination.getNumberOfRecords() ) );
      put.add( Bytes.toBytes( "CF"), Bytes.toBytes( pagination.getPrevPageNumber() ), Bytes.toBytes( pagination.getStartKey() ) ); 
      put.add( Bytes.toBytes( "CF"), Bytes.toBytes( "LAST\_ACCESSED" ), Bytes.toBytes( System.currentTimeMillis() ) ); table.put( put ); 
    } catch( IOException e ) { 
      StringWriter sw = new StringWriter(); 
      e.printStackTrace( new PrintWriter( sw ) ); 
      logger.error( sw.toString() ); 
      throw new DAOException( "Failed to update: " + e.getMessage() ); 
    } finally { 
      closeResources( table ); 
    } 
    
    logger.info( "WSPagination.put: end" ); 
    
    }
```


Your secondary index table will grow with number of requests which can be purged automatically after certain duration as user sessions duration is finite using  Hbase cell expiry feature or cleanup using external job. For each forward request you make an entry in table and for backward scan, get the start key from pagination table using `search criteria`, numberOfRecords and pageNumber, then run search on actual table. On UI table just make sure to capyure the entire pagination bean.

Code snippet:

```java
public String get( String key, Pagination pagination ) throws DAOException { 
  HTableInterface table = null; 
  String resultStr = null; 
  try { 
    table = getTable( "PAGINATION" ); 
    logger.debug( "get key:" + key + DatabaseConstants.FIELD\_DELIMITER\_TRANS + pagination.getNumberOfRecords() + "page: " + ( pagination.getPrevPageNumber() ) ); 
    Get get = new Get( Bytes.toBytes( key + "\_"+ pagination.getNumberOfRecords() ) ); 
    get.addColumn( Bytes.toBytes( "CF"), Bytes.toBytes( pagination.getPrevPageNumber() ) ); 
    Result result = table.get( get ); 
    resultStr = ( result == null || result.isEmpty() ) ? null : Bytes.toString( result.getValue( Bytes.toBytes( WS\_PAGINATION.FAMILY ), Bytes.toBytes( pagination.getPrevPageNumber() ) ) );
     } catch( Exception e ) { 
        StringWriter sw = new StringWriter(); e.printStackTrace( new PrintWriter( sw ) ); 
        throw new DAOException( "Failed to get Number: " + resultStr + "\t error: " + e.getMessage() ); 
      } 
        finally { 
          closeResources( table ); } 
          return resultStr; 
        }
```

Managing the Secondary Index Table

In summary, by creating a secondary index table and a dedicated pagination table, you can implement both forward and backward navigation in HBase, enhancing your application's user experience. While this approach involves some complexity due to maintaining duplicate datasets, it's a valuable workaround for a common HBase limitation.