---
layout: post
title: Solr Multithreaded concurrent atomic updates problem.
date: 2015-12-14 13:02:54.000000000 -08:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Big Data
- java
- solr
tags:
- bigdata
- java
- solr
meta:
  _edit_last: '1'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: Solr Multithreaded concurrent atomic updates
  _yoast_wpseo_title: Solr Multithreaded concurrent atomic updates
  _yoast_wpseo_metadesc: Solr Multithreaded concurrent atomic updates
  _yoast_wpseo_linkdex: '81'
  dsq_thread_id: '4402147611'
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/solr-multithreaded-concurrent-atomic-updates-problem/"
---
Solr Multithreaded concurrent atomic updates problem:  
Solr has few limitations for the data ingestion, as it doesn't provide row level lock over document.  
 I face this problem while uploading data in bulk to solr5 in multithread environment and I solved it by solrj client side lock.  
When concurrent threads try to make atomic update on a multivalued field of a document at the same time, few threads changes get overridden and it happens because last thread update take sometime to get indexed.

Data ingestion scenario:  
There are two tables in RDBMS and I need to denormalize in solr, Steps I was following for atomic/partial document update-  
1- Fetch the existing document.  
2- Update the single value fields if required and add/set the new values to multivlaued fields.  
3- Update the final document back to solr.

e.g.  
<!--more-->`
collection fields-
field name="id" type="string" indexed="true" stored="true" required="true" multiValued="false" />
field name="address" type="text_general" indexed="true" stored="true" multiValued="true"/>
field name="name" type="text_general" indexed="true" stored="true" />
field name="_version_" type="long" indexed="true" stored="true"/>
`  
[caption id="attachment\_445" align="aligncenter" width="300"][![img1]({{ site.baseurl }}/assets/images/img1-300x176.png)](http://www.techsquids.com/wp-content/uploads/2015/12/img1.png) img1[/caption]  
[caption id="attachment\_446" align="aligncenter" width="300"][![img2]({{ site.baseurl }}/assets/images/img2-300x101.png)](http://www.techsquids.com/wp-content/uploads/2015/12/img2.png) img2[/caption]

I followed below steps to create client side lock to resolve this problem:

- Store last recently updates in last recently used set LRUSet.
- Set maximum number of elements limit in LRUSet 
- if new update present in LRUSet then check whether that document is indexed succesfully or not.
- if document is indexed then make atomic update set/add to solr else wait current thread until document is indexed in solr successfuly 
- Add or replace new entry in LRUSet.

Please post your comment if you have any queries.

