---
layout: post
title: why there is difference between values of average response time in Summary
  Report and Average transaction response time graph
date: 2014-11-24 12:59:28.000000000 -08:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Performance Testing
tags:
- LoadRunner
- LoadRunner Analysis
meta:
  _edit_last: '2'
  interface_sidebarlayout: default
  dsq_thread_id: '3286332476'
  _yoast_wpseo_focuskw: difference between values of average response time in Summary
    Report and Average transaction response time graph
  _yoast_wpseo_title: difference between values of average response time in Summary
    Report and Average transaction response time graph
  _yoast_wpseo_metadesc: difference between values of average response time in Summary
    Report and Average transaction response time graph
  _yoast_wpseo_linkdex: '63'
author:
  login: ceekay
  email: ceekay.chandrakant88@gmail.com
  name: Chandrakant
  display_name: Chandrakant Singh
  first_name: Chandrakant
  last_name: Singh
permalink: "/pt/ifference-between-values-of-average-response-time-in-summary-report-and-graph/"
---
Sometimes it is confusing, when we observe the difference in Avg, max and min values of response time in "Summary report" and values in "Average transaction response time" graph.

To understand this we will have to understand how these values are calculated.

The Avg, max and min values of response time in "Summary report" is calculated using the complete data of transactions that executed during the test duration and is most precise.

The "Average transaction response time" graph does not use all the data points captured during execution. The values in the Graph are averaged out based on the granularity to make it more readable. So, the the Avg, max and min values of response time in "Average transaction response time" graph is calculated based on the averaged values (calculated based on granularity) used as data points to plot this graph. These values will change if there is change in the granularity.

You may also find that the Avg, max and min values of response time shown during execution in controller is different from the above two. It could be because there is some think time coded with in the transaction scope and it is added to the response time value, shown in controller. This think time is excluded by default in the LoadRunner analysis.

So, if you are confused, always use the data that is there in the Summary Report!

