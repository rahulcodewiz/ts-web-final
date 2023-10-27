---
layout: post
title: strtok - Capture a sub string or data from a string based on delimiters in
  Loadrunner
date: 2014-09-24 12:15:28.000000000 -07:00
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
  dsq_thread_id: '3074905618'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: strtok
  _wp_old_slug: how-to-capture-a-sub-string-or-data-from-a-string-based-on-delimiters-in-loadrunner
  _yoast_wpseo_linkdex: '73'
  _yoast_wpseo_title: strtok - Capture a sub string or string data based on delimiters
  _yoast_wpseo_metadesc: strtok is a function in loadrunner that can be used to capture
    data from string by specifying delimiters. strtok function can be used to do the
    trick
author:
  login: ceekay
  email: ceekay.chandrakant88@gmail.com
  name: Chandrakant
  display_name: Chandrakant Singh
  first_name: Chandrakant
  last_name: Singh
permalink: "/pt/strtok-loadrunner/"
---
There is an inbuilt function in loadrunner that can be used to capture data from string by specifying delimiters. strtok function can be used to do the trick -

In below example it is shown that how all words can be captured from string "http://localhost/app/myapp:8080" by using 2 delimeters / and :

&nbsp;extern char \* strtok(char \* string, const char \* delimiters ); // Explicit declaration

&nbsp; _&nbsp; char String\_org[] = "http://localhost/app/myapp:8080"; // original string&nbsp;_

_&nbsp; &nbsp; char delimiter[] = "/:";_

_&nbsp; &nbsp; char \* token;_

_&nbsp; &nbsp; token = (char \*)strtok(String\_org, delimiter); // capture 1st sub string based on defined delimiter_

_&nbsp; &nbsp; if (!token) {_

_&nbsp; &nbsp; &nbsp; &nbsp; lr\_output\_message ("No tokens found in string!");_

_&nbsp; &nbsp; &nbsp; &nbsp; return( -1 );_

_&nbsp; &nbsp; }_

_&nbsp; &nbsp; while (token != NULL ) { // While valid tokens are returned_

_&nbsp; &nbsp; &nbsp; &nbsp; lr\_output\_message ("%s", token );_

_&nbsp; &nbsp; &nbsp; &nbsp; token = (char \*)strtok(NULL, delimiter); // Get the next token_

_&nbsp; &nbsp; }&nbsp;_

&nbsp;Output:

Starting iteration 1.

Starting action Action.

Action.c(15): http

Action.c(15): localhost

Action.c(15): app

Action.c(15): myapp

Action.c(15): 8080

Ending action Action.

