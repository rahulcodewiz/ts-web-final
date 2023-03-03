---
layout: post
title: Loadrunner Correlation of dynamic boundary
date: 2014-09-24 12:19:47.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Performance Testing
tags:
- LoadRunner
- Loadrunner Correlation
- LoadRunner Scripting Tricks
meta:
  _edit_last: '2'
  _layout: inherit
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: correlation
  _yoast_wpseo_title: Correlation of dynamic boundary by using regex in LoadRunner
  _yoast_wpseo_metadesc: loadrunner correlation dynamic boundary. Use of Regular expression
    attributes in loadrunner script to deal with dynamic left or right boundaries
  _wp_old_slug: loadrunner-correlation-dynamic-left-boundary-and-right-boundary-in-web_reg_save_param-2
  _yoast_wpseo_linkdex: '84'
  dsq_thread_id: '3065020303'
author:
  login: ceekay
  email: ceekay.chandrakant88@gmail.com
  name: Chandrakant
  display_name: Chandrakant Singh
  first_name: Chandrakant
  last_name: Singh
permalink: "/pt/loadrunner-correlation-dynamic-boundary/"
---

##  Loadrunner Correlation of dynamic boundary

LoadRunner [Correlation](http://www.techsquids.com/pt/loadrunner-correlation/ "Correlation")is one of the most important concept in loadrunner, especially when you are working on web protocols in loadrunner like web(http/html), sap web or Oracle web applications. When dealing with complex scripts, we encounter scenarios where the usual web\_reg\_save\_param function is not able to solve the purpose.

You can use following regular expression attributes &nbsp;in your script to deal with correlation of dynamic boundary :-

1. **LB/DIG -** This attribute interprets the **#** sign as a wildcard for single digit. eg:- &nbsp;"Error5##" matches for "Error500", "Error501" till "Error599".
2. **LB/ALNUM -** This attribute interprets the **^** sign as a wildcard for single US-ASCII alphanumeric character.
3. L **B/ALNUMIC -** &nbsp;This attribute interprets the&nbsp; **^** &nbsp;sign as a wildcard for single US-ASCII alphanumeric character, this regular expression is case insensitive. eg:- "Er^^r" matches for "Error", "ErRor", "ErrOr", "ErROr", "Er12r", Err1r" etc.
4. **LB/ALNUMLC -** &nbsp;This attribute interprets the&nbsp; **^** &nbsp;sign as a wildcard for single US-ASCII alphanumeric character and lower case. &nbsp;In this case&nbsp;"Er^^r" will not match for "ErROr", "ErRor", "ErR1r" and others with an uppercase alphabet present.
5. **LB/ALNUMUC -** &nbsp;This attribute interprets the&nbsp; **^** &nbsp;sign as a wildcard for single US-ASCII alphanumeric character and upper case.

Read for basic correlation tips :-  
[LoadRunner Correlation](http://www.techsquids.com/pt/how-to-identify-the-dynamic-values-in-loadrunner-script-and-do-correlation-in-loadrunner-for-the-dynamic-values/ "LoadRunner Correlation")

