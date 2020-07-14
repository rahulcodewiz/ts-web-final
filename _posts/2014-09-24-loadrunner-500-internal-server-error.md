---
layout: post
title: How to resolve LoadRunner 500 internal server error while testing an upload
  file scenario
date: 2014-09-24 11:36:21.000000000 -07:00
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
  _layout: inherit
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: loadrunner 500 internal server error
  _yoast_wpseo_title: Resolve LoadRunner 500 internal server error - TechSquids
  _yoast_wpseo_metadesc: Below are few tips on resolving the loadrunner 500 internal
    server error in HTTP/HTML protocol script created for upload functionality. Check,
    if you hav
  _yoast_wpseo_linkdex: '79'
  dsq_thread_id: '3098346311'
  _wp_old_slug: how-to-resolve-500-internal-server-error-in-loadrunner-while-testing-an-upload-file-scenario
author:
  login: ceekay
  email: ceekay.chandrakant88@gmail.com
  name: Chandrakant
  display_name: Chandrakant Singh
  first_name: Chandrakant
  last_name: Singh
permalink: "/pt/loadrunner-500-internal-server-error/"
---
Scripting a file Upload scenario is usually pretty straightforward, just do few correlations and the script runs without any errors.

But, sometime it becomes complicated when script keeps failing even after correlating all the dynamic values. The most common error encountered while executing the upload script is LoadRunner 500 internal server error&nbsp;.

It may look easier to switch from HTTP/HTML protocol to AJAX truclient in order to resolve the issues but that may lead to different complications, considering –

1. AJAX &nbsp;truclient &nbsp;is a GUI based protocol. So, the script during execution consumes more memory on your load generator machine. Therefor the number of users which can be simulated from a load generator is comparatively less
2. The script created has to be more dynamic to run without any issues that arise, when application starts performing slow under load.

**Below are few tips on resolving the loadrunner 500 internal server error in HTTP/HTML script created for upload functionality.**

- Record a new script and compare the requests to identify if any dynamic value has been missed out
- Check, if you have missed to convert the captured values to some special format (PLAIN to URL OR PLAIN to HTML etc.)
- Enable parameter substitution and &nbsp;cross-check the values that are getting substituted are in the same format as the Original recorded format
- The last and most important point is to go to the tree view (toggle to HTML view) of failing request and compare the items in header section for recorded and replay snapshot. You may find some important header missing during replay like a secure token value or something. Add corresponding web\_add\_header(); before the failing request in the script and re execute.

_I hope, by now you would have successfully resolved the issues related to your script_&nbsp;:)

