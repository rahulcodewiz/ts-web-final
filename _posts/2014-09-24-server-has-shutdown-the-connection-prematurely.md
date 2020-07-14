---
layout: post
title: LoadRunner Controller Error :- Server has shutdown the connection prematurely
date: 2014-09-24 12:08:05.000000000 -07:00
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
  dsq_thread_id: '3067509689'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: server has shutdown the connection prematurely
  _wp_old_slug: lserver-has-shutdown-the-connection-prematurely
  _yoast_wpseo_linkdex: '82'
  _yoast_wpseo_title: server has shutdown the connection prematurely - TechSquids
  _yoast_wpseo_metadesc: The Error "Server has shutdown the connection prematurely"
    is often seen during performance test execution in controller. 1. Is this a performance
    issue
author:
  login: ceekay
  email: ceekay.chandrakant88@gmail.com
  name: Chandrakant
  display_name: Chandrakant Singh
  first_name: Chandrakant
  last_name: Singh
permalink: "/pt/server-has-shutdown-the-connection-prematurely/"
---
The Error **"Server has shutdown the connection prematurely"** is often seen during performance test execution in controller.

1. Is this a performance issue with the web/app server?

No, it is not.

2. Is this related to Loadrunner?

Yes, it is.

3. Can we resolve it by simply setting&nbsp;web\_set\_sockets\_option

("IGNORE\_PREMATURE\_SHUTDOWN", "1"); to the scripts?

No, we cannot. Adding the function - &nbsp;web\_set\_sockets\_option ("IGNORE\_PREMATURE\_SHUTDOWN", "1"); will just help in ignoring the error on controller and the issue may still persist.

4. What is the root cause of this error?

Case 1 :-The error - "server has shutdown the connection prematurely" is because the server closed a live connection, created by your loadrunner script. The server can do so because of multiple reasons and the most common one is that the client is not able to read data from the server's socket in the specified time out limit.

If you have access to the server logs, scan the logs and you might be able to identify the root cause of this. Below is the captured log from an ORACLE web logic server.

\<BEA-000449\> \<Closing the socket, as no data read from it on ##.###.#.###:##,### during the configured idle timeout of 5 seconds.\>

So, it clearly states that the client (you load generator machine) is not able to read the data from the socket in the specified time limit and then the server closed the connection. This resulted an error on the controller.

5. &nbsp;How to resolve the "Server xxx has shut down the connection prematurely" error:-

As stated above, the error is because of slow client (LG) which was not able to read the data from server's socket. This could be because you have over loaded your load generator machine then it's capacity or the shared bandwidth is too less for the Vusers.

**Try distributing the load to multiple load generator machines to resolve the issue.**

&nbsp;

Note:- You may also come across this&nbsp;situation, if the number of concurrent connections made to the database server exceeds the maximum defined limit.

