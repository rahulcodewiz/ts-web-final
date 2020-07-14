---
layout: post
title: SSL protocol error when attempting to read with host
date: 2014-11-24 11:16:35.000000000 -08:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Performance Testing
tags:
- LoadRunner
- Loadrunner Errors
meta:
  _edit_last: '2'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: SSL protocol error when attempting to read with host
  _yoast_wpseo_title: SSL protocol error when attempting to read with host
  _yoast_wpseo_metadesc: SSL protocol error when attempting to read with host
  _yoast_wpseo_linkdex: '56'
  dsq_thread_id: '3267141396'
author:
  login: ceekay
  email: ceekay.chandrakant88@gmail.com
  name: Chandrakant
  display_name: Chandrakant Singh
  first_name: Chandrakant
  last_name: Singh
permalink: "/pt/ssl-protocol-error-when-attempting-to-read-with-host/"
---
If you are experiencing the usual SSL protocol error during the replay of script in VUgen. Try the below function with SSL version as "TLS" to resolve the "SSL protocol error when attempting to read with host"

**web\_set\_sockets\_option("SSL\_VERSION", "TLS");&nbsp;**

