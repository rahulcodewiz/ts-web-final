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
## Solr Multithreaded concurrent atomic updates problem:  

Apache Solr is a popular and powerful open-source search platform used to index and search large datasets. However, it comes with certain limitations when dealing with concurrent data ingestion and atomic updates, which can be a challenge in a multi-threaded environment. In this blog post, we'll explore the issue of concurrent atomic updates in Solr and discuss a solution involving client-side locking to overcome this problem.

The Challenge:

One of the main limitations of Solr is that it doesn't provide row-level locking for documents. This limitation becomes evident when multiple threads attempt to perform atomic updates on a multi-valued field of a document simultaneously. In such scenarios, some updates may get overridden, as the last thread's update might take some time to be indexed.

Data Ingestion Scenario:

Let's consider a common data ingestion scenario. Suppose you have data in two tables within an RDBMS and need to denormalize this data in Solr. The typical steps for atomic or partial document updates are as follows:

- Fetch the existing document.
- Update single-value fields as needed and add/set new values to multi-valued fields.
- Update the final document back to Solr.

For instance, you may have fields like 'id', 'address', 'name', and 'version' in your Solr collection.

```
collection fields-
field name="id" type="string" indexed="true" stored="true" required="true" multiValued="false" />
field name="address" type="text_general" indexed="true" stored="true" multiValued="true"/>
field name="name" type="text_general" indexed="true" stored="true" />
field name="_version_" type="long" indexed="true" stored="true"/>
```

[caption id="attachment\_445" align="aligncenter" width="300"][![img1]({{ site.baseurl }}/assets/images/img1-300x176.png)](http://www.techsquids.com/wp-content/uploads/2015/12/img1.png) img1[/caption]  
[caption id="attachment\_446" align="aligncenter" width="300"][![img2]({{ site.baseurl }}/assets/images/img2-300x101.png)](http://www.techsquids.com/wp-content/uploads/2015/12/img2.png) img2[/caption]

The Solution:

To address the challenge of concurrent atomic updates in Solr, you can implement a client-side locking mechanism. Here's a simplified overview of the steps involved in this solution:

1. Create an LRUSet to store the most recently updated documents.
2. Set a maximum limit for the number of elements in the LRUSet to manage memory efficiently.
3. Before making an atomic update, check if the document is already present in the LRUSet.
4. If the document is in the LRUSet and has been successfully indexed in Solr, proceed with the atomic update.
5. If the document is not yet indexed, wait for the current thread until the document is successfully indexed.
6. After the update is complete, add or replace the entry in the LRUSet.

If you have any questions or need further clarification on this solution, please feel free to leave a comment. I hope this post helps you address the issue of concurrent atomic updates in Solr and improve your data management in this powerful search platform.

