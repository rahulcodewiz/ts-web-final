---
layout: post
title: Error during code generation and The Vuser script was not generated in Loadrunner
date: 2014-09-24 12:18:36.000000000 -07:00
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
  dsq_thread_id: '3074895826'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: Error during code generation
  _yoast_wpseo_title: Error during code generation in Loadrunner script
  _yoast_wpseo_metadesc: Sometime, LoadRunner captures all events during recording
    but throws - "Error during code generation. The Vuser script was not generated."
  _wp_old_slug: loadrunner-captured-all-events-during-recording-but-thrown-an-error-during-script-generation-error-during-code-generation-the-vuser-script-was-not-generated
  _yoast_wpseo_linkdex: '68'
author:
  login: ceekay
  email: ceekay.chandrakant88@gmail.com
  name: Chandrakant
  display_name: Chandrakant Singh
  first_name: Chandrakant
  last_name: Singh
permalink: "/pt/loadrunner-error-during-code-generation/"
---

## Error during code generation and The Vuser script was not generated in Loadrunner
Sometime, LoadRunner captures all events during recording but throws an&nbsp;Error during script generation - "Error during code generation. The Vuser script was not generated."

Sometimes the character sets used are not supported by LoadRunner (by default) and creates issue at the time of script generation. Try regenerating the script after enabling UTF-8 type supported charset in recording options as shown below :

&nbsp;

[caption id="" align="aligncenter" width="320"][![Error during code generation loadrunner]({{ site.baseurl }}/assets/images/proxy?url=http%3A%2F%2F3.bp.blogspot.com%2F-XzFQetzweqk%2FU7Eywth4NvI%2FAAAAAAAAADg%2F6l1DDVvyOmY%2Fs1600%2FRecording-options.jpg&container=blogger&gadget=a&rewriteMime=image%2F*)](http://3.bp.blogspot.com/-XzFQetzweqk/U7Eywth4NvI/AAAAAAAAADg/6l1DDVvyOmY/s1600/Recording-options.jpg) LoadRunner Recording Options[/caption]

&nbsp;

