---
layout: post
title: Solrcloud 4 inconsistent results count-commitwithinms issue
date: 2015-12-14 22:25:39.000000000 -08:00
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
  _yoast_wpseo_focuskw: Solrcloud 4 inconsistent results count-commitwithinms issue
  _yoast_wpseo_title: Solrcloud 4 inconsistent results count
  _yoast_wpseo_metadesc: Solrcloud 4 inconsistent results count-commitwithinms issue.
  _yoast_wpseo_linkdex: '56'
  dsq_thread_id: '4403431178'

author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/solrcloud-4-inconsistent-results-count-commitwithinms-issue/"
---
## Solrcloud 4 inconsistent results count-commitwithinms issue:

SolrCloud, a distributed search platform, is known for its scalability and real-time indexing capabilities. However, when dealing with high data loads and high query frequencies, it can sometimes returns inconsistent results in terms of document counts, especially during peak data ingestion periods. In this blog post, we'll explore an issue with SolrCloud 4.10 and discuss a solution that might help you achieve consistent results.

The Challenge:

This scenario I faced with a SolrCloud v4.10, with a collection containing four shards, two replicas, and five ZooKeeper nodes. The collection is responsible for providing real-time data ingestion and search capabilities, running both processes simultaneously. On a daily basis, the system handles around 2-3 million insert and update operations, resulting in a total document count exceeding 80 million.

This load cause inconsistency in document counts returned by Solr during peak data ingestion times. A simple query to retrieve the document count using the 'numFound' variable often shows significantly fewer documents than are actually present in the Solr index. This inconsistency can have business impact, especially when the system relies on accurate data retrieval.


Sample query:

```
for i in `seq 1 50`; do curl 'http://localhost:8888/solr/OPTUM/select?q=\*:\*&wt=json&indent=true'|grep numFound|rev|cut -d'{' -f1 |rev done
```

The response `numfound` variable shows sometime very less documents count then actually present in solr.

The Solution:

While the root cause of this issue might be challenging to pinpoint precisely, a temporary workaround has proven effective in mitigating the problem. The workaround involves making adjustments at the Solr configuration level rather than the client-side. More specifically, modifying the commit strategy settings within Solr's configuration.

```
<autocommit>
            <maxtime>15000</maxtime>
            <opensearcher>false</opensearcher>
        </autocommit><autosoftcommit>
            <maxtime>2000</maxtime>
        </autosoftcommit>
```

In conclusion, this solution helped with achieving consistent results, especially during peak data ingestion times, is crucial. While the exact cause of inconsistent document counts may remain elusive, adopting the workaround mentioned above can provide a viable solution.

