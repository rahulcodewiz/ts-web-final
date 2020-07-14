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
  wp-syntax-cache-content: "a:2:{i:1;s:581:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"line_numbers\"><pre>1\n2\n3\n4\n</pre></td><td class=\"code\"><pre class=\"unix\"
    style=\"font-family:monospace;\">for i in `seq 1 50`;\r\ndo\r\n       curl 'http://localhost:8888/solr/OPTUM/select?q=*:*&amp;amp;wt=json&amp;amp;indent=true'|grep
    numFound|rev|cut -d'{' -f1 |rev\r\ndone</pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">for i in `seq 1 50`;\r\ndo\r\n       curl 'http://localhost:8888/solr/OPTUM/select?q=*:*&amp;amp;wt=json&amp;amp;indent=true'|grep
    numFound|rev|cut -d'{' -f1 |rev\r\ndone</p></div>\n\";i:2;s:793:\"\n<div class=\"wp_syntax\"
    style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n</pre></td><td
    class=\"code\"><pre class=\"html\" style=\"font-family:monospace;\">    &lt;autoCommit&gt;\r\n
    \           &lt;maxTime&gt;15000&lt;/maxTime&gt;\r\n            &lt;openSearcher&gt;false&lt;/openSearcher&gt;\r\n
    \       &lt;/autoCommit&gt;\r\n&lt;autoSoftCommit&gt;\r\n            &lt;maxTime&gt;2000&lt;/maxTime&gt;\r\n
    \       &lt;/autoSoftCommit&gt;</pre></td></tr></table><p class=\"theCode\" style=\"display:none;\">
    \   &lt;autoCommit&gt;\r\n            &lt;maxTime&gt;15000&lt;/maxTime&gt;\r\n
    \           &lt;openSearcher&gt;false&lt;/openSearcher&gt;\r\n        &lt;/autoCommit&gt;\r\n&lt;autoSoftCommit&gt;\r\n
    \           &lt;maxTime&gt;2000&lt;/maxTime&gt;\r\n        &lt;/autoSoftCommit&gt;</p></div>\n\";}"
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/solrcloud-4-inconsistent-results-count-commitwithinms-issue/"
---
Solrcloud 4 inconsistent results count-commitwithinms issue:

Issue description:

I have&nbsp;four nodes solrcloud setup version 4.10 and my collection has 4 shards, 2 replicas and 5 zookeeper nodes. My application provide the search ability with realtime data ingestion, both data ingestion and search processes runs in parallel.

Every day the data load is around 2~3MM records(insert/update operations) and total documents count is 80MM+.

The problem I was&nbsp;facing is that the solr returns very inconsistent records count during peak time of data ingestion.

Sample query:

```
for i in `seq 1 50`; do curl 'http://localhost:8888/solr/OPTUM/select?q=\*:\*&wt=json&indent=true'|grep numFound|rev|cut -d'{' -f1 |rev done
```

The response&nbsp;`numfound`&nbsp;variable shows sometime very less documents count then actually present in solr.

Solution:  
I could not find exact root cause of this problem but temporarily I did a work around to resolve this error.  
I had been using solrj4.x softcommit method(UpdateRequest.setCommitWithin( commitWithinMs )) which I commented and used all commit strategy at solr end.

```
<autocommit>
            <maxtime>15000</maxtime>
            <opensearcher>false</opensearcher>
        </autocommit><autosoftcommit>
            <maxtime>2000</maxtime>
        </autosoftcommit>
```

I am getting consistent result from solr but still I am not sure why solrj client side commit isn't working.

