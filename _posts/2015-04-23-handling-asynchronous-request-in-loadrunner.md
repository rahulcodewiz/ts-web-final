---
layout: post
title: Handling Asynchronous request in LoadRunner
date: 2015-04-23 13:29:31.000000000 -07:00
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
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: asynchronous request in loadrunner
  _yoast_wpseo_metadesc: Handling asynchronous request in loadrunner. There are 3
    types of Asynchronous requests, primarily - Polling, Long polling and Push. These
    Asynchronous requests can be handled in loadrunner by enabling "Async Scan" and
    by using web_reg_async_attributes and web_sync functions defined in LoadRunner.
  _yoast_wpseo_linkdex: '76'
  dsq_thread_id: '4074811375'
author:
  login: ceekay
  email: ceekay.chandrakant88@gmail.com
  name: Chandrakant
  display_name: Chandrakant Singh
  first_name: Chandrakant
  last_name: Singh
permalink: "/pt/handling-asynchronous-request-in-loadrunner/"
---
It is now easy to handle&nbsp;asynchronous request in loadrunner. I am not going to start with differentiating synchronous and asynchronous request here, as I suppose if you are here you already know the difference.

&nbsp;

There are 3 types of Asynchronous requests, primarily -

&nbsp;

1. **Polling** -&nbsp; Client sends HTTP requests to the server at regular intervals. The server responds with updates and this as a result updates the application interface inside the browser.

2. **Long polling** - Client sends an HTTP request to the server. Whenever there is an update available on the server, it responds with an HTTP response.&nbsp;As soon as client receives the response, it issues another request to the server.

3. **Push** - Client sends an HTTP request to the server. Server responds with a response that appears to never end, so that the connection is not closed by client.&nbsp;Whenever there is an update on the server, it sends that to the client over this open connection and if there is no real update available on the server, it sends PING messages to the client&nbsp;to prevent the connection from closing or getting timeout.

We will see the implementation to handle asynchronous poll call by using the web\_reg\_async function available in LR11.5 and above versions.

1. Enable Async Scan in Recording Options **-&nbsp;** Navaigate to Recording Options\>General\>Code Generation\> check "Async Scan" checkbox

Optional :- You can modify the default configuration used to recognise patterns of Async conversations during the scan by clicking the “Async Options” button.

1. Record the application with Async call, as usual.

1. After recording, the code will be generated and the Async Scan performed automatically.

1. The results of the scan are then displayed in the Async tab of the Design Studio dialog, which is automatically presented at the end of script generation
2. VuGen inserts a web\_reg\_async\_attributes step before the start of the asynchronous conversation and comments out the repetitive calls in the script
3. web\_reg\_async\_attributes function has follwing attributes (callback functions are added to the AsyncCallbacks.c extra file):-

&nbsp;

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ID - Id used for asynchronous communication

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;URL - To&nbsp;start the ASYNC communication (will be checked in subsequent web\_custom or web\_submit requests)

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Pattern - Type of Asynchronous request - push, poll, or long-poll

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;RequestCB - called before a request is sent

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;ResponseCB - callback is called after every response is received in the conversation.

&nbsp;

1. VuGen adds a web\_stop\_async step at the end of the asynchronous conversation, this marks the end of ASYNC conversation

1. If the asynchronous request is of type poll adding web\_sync function after the polling request and before web\_stop\_async will work like a do-while loop with&nbsp;exit criteria defined&nbsp;in AsyncCallbacks.c under Poll\_1\_ResponseCB function as shown below-

> &nbsp;
> 
> **&nbsp; &nbsp; From Action.c**
> 
> //Register a polling pattern
> 
> web\_reg\_async\_attributes("ID=Poll\_1",
> 
> "Pattern=Poll",
> 
> "URL= **http://TestURL.com**",
> 
> "PollIntervalMs=15200",
> 
> "RequestCB=Push\_0\_RequestCB",
> 
> "ResponseCB=Push\_0\_ResponseCB",
> 
> LAST);
> 
> //Start the polling pattern
> 
> web\_custom\_request("Test request",
> 
> "URL= **http://TestURL.com**",
> 
> "Method=POST",
> 
> "TargetFrame=",
> 
> "Resource=0",
> 
> "RecContentType=text/xml",
> 
> "Referer=",
> 
> "Snapshot=t49.inf",
> 
> "Mode=HTML",
> 
> "EncType=text/xml; charset=utf-8",
> 
> "Body=Testmsdfmsdsadas;.dsad",
> 
> LAST);
> 
> //Wait for parameter to be created (see below in AsyncCallbacks.c)
> 
> web\_sync("ParamCreated=ready","RetryIntervalMs=18000","RetryTimeoutMs=3600000",LAST);
> 
> web\_stop\_async("ID=Push\_0",
> 
> LAST);
> 
> **From AsyncCallbacks.c**
> 
> //The response call-back is called after each polling response is received.
> 
> int Poll\_1\_ResponseCB(
> 
> const char \*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; aResponseHeadersStr,
> 
> int&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; aResponseHeadersLen,
> 
> const char \*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; aResponseBodyStr,
> 
> int&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; aResponseBodyLen,
> 
> int&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; aHttpStatusCode)
> 
> {
> 
> //enter your implementation for ResponseCB() here
> 
> //Increment long-polling response counter
> 
> counter++;
> 
> //Set parameter value to indicate that 10 long-polling responses were received.
> 
> if (counter\>10 || (strcmp(aResponseBodyStr,"6000")==0))
> 
> lr\_save\_string("OK","ready");
> 
> return WEB\_ASYNC\_CB\_RC\_OK;
> 
> }
> 
> &nbsp;

During the replay

The matching request will be handled according to the Pattern attribute:

For a Poll pattern, the request will be sent repeatedly. That is, after a response for a polling request is received, replay will wait for an interval matching the polling interval

specified in the web\_reg\_async\_attributes. After this interval has passed, another request will be sent, and so on.

For a Long Poll pattern, the request will be sent repeatedly. Another request will be sent as soon as a response for a polling request is received.

For a Push pattern, the response is expected to continue indefinitely (until it is terminated by either the server or the client).

&nbsp;

Post your queries in the comment.....

&nbsp;

