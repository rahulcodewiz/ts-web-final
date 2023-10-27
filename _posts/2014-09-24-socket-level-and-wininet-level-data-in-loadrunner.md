---
layout: post
title: Difference between Socket level and Wininet level data in Loadrunner
date: 2014-09-24 12:19:10.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Performance Testing
tags:
- LoadRunner
- LoadRunner Scripting Tricks
meta:
  _edit_last: '2'
  _layout: inherit
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: socket level and wininet level data in loadrunner
  _yoast_wpseo_title: socket level and wininet level data in loadrunner
  _yoast_wpseo_metadesc: There are 2 types of capture levels - socket level and wininet
    level data in loadrunner. These 2 capture levels are available in recording options.
  _yoast_wpseo_linkdex: '77'
  dsq_thread_id: '3075566327'
  _wp_old_slug: difference-between-socket-level-and-wininet-level-data-in-loadrunner-recording-options
author:
  login: ceekay
  email: ceekay.chandrakant88@gmail.com
  name: Chandrakant
  display_name: Chandrakant Singh
  first_name: Chandrakant
  last_name: Singh
permalink: "/pt/socket-level-and-wininet-level-data-in-loadrunner/"
---

## Difference between Socket level and Wininet level data in Loadrunner

There are 2 types of capture levels - socket level and wininet level data in loadrunner. These 2 capture levels are available in recording options. They specify the tool, where to hook and capture the communication packets from.

Most of the application though communicate at the socket level and the events get recorded by loadrunner using socket level data capture. But, sometimes the applications are designed to interact using wininet API and in such cases we should use wininet level capture in loadrunner, to capture the events successfully. So, the use of socket level/wininet level capture depends on how the application communicates.

Note: The requests might get duplicated if you are using socket level and wininet level data capture and you can comment the duplicated requests in the script.

[caption id="" align="aligncenter" width="320"][![socket level and wininet level data in loadrunner]({{ site.baseurl }}/assets/images/proxy?url=http%3A%2F%2F3.bp.blogspot.com%2F-09JKD9Ng8SY%2FU7FIqPPADbI%2FAAAAAAAAAEA%2FmSvPfvIfzho%2Fs1600%2F1.gif&container=blogger&gadget=a&rewriteMime=image%2F*)](http://3.bp.blogspot.com/-09JKD9Ng8SY/U7FIqPPADbI/AAAAAAAAAEA/mSvPfvIfzho/s1600/1.gif) LoadRunner Recording Options[/caption]

