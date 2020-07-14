---
layout: post
title: 'Loadrunner : Error -26601: Decompression function wgzMemDecompressBuffer failed,
  return code=-5 (Z_BUF_ERROR), inSize=0, inUse=0, outUse=0'
date: 2014-09-24 12:11:06.000000000 -07:00
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
  _yoast_wpseo_focuskw: Decompression function wgzMemDecompressBuffer failed
  _yoast_wpseo_title: 'LoadRunner: Decompression function Loadrunner : Error -26601:
    Decompression function wgzMemDecompressBuffer failed failed-TechSquids'
  _yoast_wpseo_metadesc: The "error -26601 Decompression function wgzMemDecompressBuffer
    failed" in loadrunner occurs because of insufficient buffer size set in the runtime
    settings
  _yoast_wpseo_linkdex: '63'
  dsq_thread_id: '3094674663'
  _wp_old_slug: loadrunner-error-26601-decompression-function-wgzmemdecompressbuffer-failed-return-code-5-z_buf_error-insize0-inuse0-outuse0
author:
  login: ceekay
  email: ceekay.chandrakant88@gmail.com
  name: Chandrakant
  display_name: Chandrakant Singh
  first_name: Chandrakant
  last_name: Singh
permalink: "/pt/decompression-function-wgzmemdecompressbuffer-failed/"
---
The "error -26601: Decompression function wgzMemDecompressBuffer failed, return code=-5 (Z\_BUF\_ERROR), inSize=0, inUse=0, outUse=0" in loadrunner occurs because of insufficient buffer size set in the runtime settings. The Network buffer size is set to 12288 bytes, by default.

In a scenario where user requires to use more than the specified buffer, we encounter the " Decompression function wgzMemDecompressBuffer failed " error.

Solution:- Increasing the network buffer size in Runtime settings\> Preferences\> Option\>General\>Netwok Buffer Size

&nbsp;

[caption id="" align="aligncenter" width="388"][![Error -26601: Decompression function wgzMemDecompressBuffer failed]({{ site.baseurl }}/assets/images/proxy?url=http%3A%2F%2F2.bp.blogspot.com%2F-MkAwQPSQ2Fo%2FU7UdFLxwpZI%2FAAAAAAAAAEU%2FdznNWVaziYg%2Fs1600%2FNetworkbuffersize.PNG&container=blogger&gadget=a&rewriteMime=image%2F*)](http://2.bp.blogspot.com/-MkAwQPSQ2Fo/U7UdFLxwpZI/AAAAAAAAAEU/dznNWVaziYg/s1600/Networkbuffersize.PNG) LoadRunner Runtime Settings[/caption]

&nbsp;

