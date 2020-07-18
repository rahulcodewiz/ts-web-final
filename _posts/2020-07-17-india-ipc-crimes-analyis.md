---
layout: page
title: India IPC crimes Analysis
date: 2020-07-17 12:09:32.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- data-visualization
tags:
- data-visualization
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharmaß
permalink: "/dv/india-ipc-crimes-analysis/"
---

## Objective: Identify the regions in India where crime rate is emerging?


{%  include  ind-ipc.html %}

<br><br>

----

### Approximately 42 million crimes were reported in India during 2001 through 2018. 
Following facts infographics depicts- 
* Crime steadily increased in the North and center regions. 
* Crime rates are highest in the states- Madhya Pradesh, Utter Pradesh, Rajasthan and Maharashtra. 
* Theft is most dominant crime along with murder and rapes. Worst neighborhoods are Delhi, Mumbai, Bangalore etc. 
* Highest percentage crime change reported in 2014.

###How do these charts indicate the answer?
Answer: Dashboard covers four major dimensions:
* Geographic Map: go over the map and regions to analyze crimes distribution among 19 states and each state is color ranked with crime intensity. It shows north region has highest number of crimes and further we can analyze crime by category on the mouse over event.   
* Pie chart: next, this chart shows crime type comparison and Theft is the most dominant crime type. It's also integrated with the global Year filter to perform yearly comparison. Select Map location for region wise comparison.    
* Bar Chart: further, find worst neighborhood/district in nation. It's integrated with the global Year filter. Also, this graph provides filter to choose top N neighborhoods and additional stats are shown over the mouse over event. Select Map location to find the region wise worst neighborhood.
* Line Chart: Analyze Percentage crime change year by year.

[Use global year filter to narrow search across the graphs (excluded line chart as X axis is year). Use Map selection feature to see state wise stats on Pie and Bar charts. Mouse hover on map region for detailed information. These filters can be used in combination]


**References**
- [India Open Data](https://data.gov.in/)
- [Dataset](https://github.com/reethified/India-IPC-Crimes-Datasets)


