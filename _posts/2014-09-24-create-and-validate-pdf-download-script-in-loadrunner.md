---
layout: post
title: How to create and validate a pdf download script in LoadRunner
date: 2014-09-24 12:17:09.000000000 -07:00
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
  _yoast_wpseo_focuskw: pdf download script in loadrunner
  _yoast_wpseo_title: How to create and validate a pdf download script in loadrunner
  _yoast_wpseo_linkdex: '61'
  _yoast_wpseo_metadesc: Saving a file to the local machine during recording a pdf
    download script in LoadRunner VUgen, by clicking on"save as" button, is a client
    side activity and does not get recorded. But
  dsq_thread_id: '3068861924'
  _wp_old_slug: how-to-create-and-validate-pdf-file-download-script-in-loadrunner
author:
  login: ceekay
  email: ceekay.chandrakant88@gmail.com
  name: Chandrakant
  display_name: Chandrakant Singh
  first_name: Chandrakant
  last_name: Singh
permalink: "/pt/create-and-validate-pdf-download-script-in-loadrunner/"
---
Saving a file to the local machine during recording of a pdf download script in loadrunner&nbsp;VUgen, by clicking on"save as" button, is a client side activity and does not get recorded. But the action on web page which results the file download box gets recorded in VUgen and actually downloads the file (pdf file/Zip file).

The downloaded file can be found in the data folder of recorded script by checking the size/type of contents.

To verify if the script is downloading file during run-time, check the iteration# folders (inside result1 folder) for the file.

If you know the size of file (in Kbs) which you are downloading, you can also use below code to check if the file has got downloaded successfully or not.

web\_url (Request for file download)

DownloadSize = web\_get\_int\_property( HTTP\_INFO\_DOWNLOAD\_SIZE ); //define DownloadSize &nbsp;as an integer variable at the beginning of action code

lr\_output\_message("Downloaded File size is %d" , DownloadSize);

if (DownloadSize \< 1000) { &nbsp;//The file to be downloaded has size of 1000 kbs

lr\_error\_message("File download has failed and downloaded content size in KBs is %d", DownloadSize);

}

