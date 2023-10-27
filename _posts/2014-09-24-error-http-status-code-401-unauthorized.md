---
layout: post
title: Error HTTP Status Code 401 Unauthorized during script replay
date: 2014-09-24 12:17:44.000000000 -07:00
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
  dsq_thread_id: '3071184574'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: error http status code 401 unauthorized
  _yoast_wpseo_title: error http status code 401 unauthorized in LoadRunner
  _yoast_wpseo_metadesc: Encountering error HTTP Status Code 401 Unauthorized, during
    HTTP/HTML script replay then try options - Add web_set_user
  _wp_old_slug: http-status-code401-unauthorized-error-during-script-replay-httphtml-protocol-in-loadrunner
  _yoast_wpseo_linkdex: '66'
author:
  login: ceekay
  email: ceekay.chandrakant88@gmail.com
  name: Chandrakant
  display_name: Chandrakant Singh
  first_name: Chandrakant
  last_name: Singh
permalink: "/pt/error-http-status-code-401-unauthorized/"
---
There are lot of common errors that we keep encountering while using Loadrunner, like HTTP status code 401, 500, 403 etc.

If you encounter error HTTP Status Code 401 Unauthorized, during HTTP/HTML script replay then try below options:

- Option 1: Add web\_set\_user(username,password,host:port );

- Option 2: Record the script after changing the capture level to Wininet level data in Recording option\> Network \> Port mapping \> capture level

- Option 3:&nbsp;Run the script after enabling Wininet replay instead of sockets option in Run time settings \> Internet Protocol \> Preferences\> Advanced

- Option 4 : If none of the above option works, record the business flow with fiddler and compare the requests in LoadRunner and fiddler. Identify if any request/header/cookie is missing in the load runner script and causing&nbsp;the issue.
