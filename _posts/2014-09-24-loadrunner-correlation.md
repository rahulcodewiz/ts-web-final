---
layout: post
title: LoadRunner Correlation
date: 2014-09-24 12:12:40.000000000 -07:00
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
meta:
  _edit_last: '2'
  _layout: inherit
  dsq_thread_id: '3069363555'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: loadrunner correlation
  _yoast_wpseo_title: loadrunner correlation for dynamic values - TechSquids
  _yoast_wpseo_metadesc: LoadRunner Correlation is one of the most important concept
    in loadrunner, especially when you are working on web protocols in loadrunner
    like web(http/html), sap web
  _wp_old_slug: how-to-identify-the-dynamic-values-in-loadrunner-script-and-do-correlation-in-loadrunner-for-the-dynamic-values
  _yoast_wpseo_linkdex: '80'
author:
  login: ceekay
  email: ceekay.chandrakant88@gmail.com
  name: Chandrakant
  display_name: Chandrakant Singh
  first_name: Chandrakant
  last_name: Singh
permalink: "/pt/loadrunner-correlation/"
---
LoadRunner Correlation is one of the most important concept in loadrunner, especially when you are working on web protocols in loadrunner like web(http/html), sap web or Oracle web applications etc.

&nbsp;LoadRunner Correlation is used to deal with the dynamic values in script that changes with each script execution. The inbuilt function web\_reg\_save\_param in loadrunner can be used to implement loadrunner correlation.

Below are the step by step instructions to do the loadrunner &nbsp;correlation:-

Note:- It is advised to have 2 recordings of same business flow to compare and identify the dynamic values.

Step 1 : Identify the dynamic value :-

- &nbsp;Replay the recorded script and see if the script fails somewhere

Note:- &nbsp;If script does not fail and the intended job is verified using the check points - there may not be any dynamic values or there is no correlation required

- Go to the failed request in script and compare it with the same request in second recording
- Identify the dynamic values present in the request

Step 2 : Find the left boundary, right boundary and correct place in the script to put the web\_reg\_save\_param function

- Find the first occurrence of dynamic value in generation log (in output window of loadrunner) - It should be present in the response header/response body to do the correlation. (Note:- If the dynamic value is present in the request header / body then the value might have generated from client side and cannot be correlated)
- Copy the left and right boundary to capture the dynamic value (eg:- consider the dynamic value DATA is present in response in the format - abcDATAxyz. Here abc is the LB and xyz is the RB to capture DATA). we should always try choosing the unique combination of LB and RB to avoid finding out the ordinance.
- Note down the **id no.** from&nbsp;\*\*\*\*\*\* Response Header/Body For Transaction With Id # \*\*\*\*\*\* (search **upward** for ' **transacion with id**' text)
- Find the event generated for the previous response\*\*\*\*\*\* Add Event For Transaction With Id # \*\*\*\*\*\*&nbsp;(search&nbsp; **downward&nbsp;** for ' **Add event**' text)
- Note down the snapshot no. for reference (snapshot=##.inf)
- Search for the snapshot no. ##.inf in the script

Step 3 : Put the web\_reg\_save\_param function in script

- You need to put the web\_reg\_save\_param function in script before the request identified in previous step (identify through the inf file number)
- Use LB and RB capture in previous step - **web\_reg\_save\_param("Correlation\_parameter", "LB=**abc **", "RB=** xyz**",LAST);**

The dynamic value should get captured in the correlation\_parameter and can be seen in replay log during replay by enabling extended log in run-time settings\>log - enable logging (checked), always send messages (checked), extended log (checked), parameter substitution (checked).

Important Notes about web\_reg\_save\_param:-

1. If the ordinance attribute is not specified in the function, it will take 1 as the default ordinance)
2. if the search attribute is not specified in the function, it will take **search=body** as default argument. Specify **search=header** if the dynamic value has to be captured from response header
3. If the length of the captured string in correlation\_parameter is greater than 256 bytes, specify&nbsp; **web\_set\_max\_html\_param\_len** ("9999"); at the beginning of action.
4. 

If you are not able to find an add event (corresponding request) for a particular response, where the dynamic value is present. Try using "relframid=all" argument in the web\_reg\_save\_param (put web\_reg\_save\_param before the &nbsp;request which ever is available first after the response).

How to deal with dynamic left and right boundaries in loadrunner correlation will be covered in separate&nbsp;post...

