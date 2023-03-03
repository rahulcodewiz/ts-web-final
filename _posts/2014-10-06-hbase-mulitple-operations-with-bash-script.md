---
layout: post
title: Hbase mulitple operations with bash script
date: 2014-10-06 16:05:27.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Big Data
- hbase
tags:
- hadoop
- hbase
- UNIX
meta:
  _edit_last: '1'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: Hbase mulitple operations with bash script
  _yoast_wpseo_title: Hbase mulitple operations with bash script
  _yoast_wpseo_metadesc: Hbase mulitple operations with bash script. hadoop and hbase,
    bulk of hbase commands into bash script.
  _yoast_wpseo_linkdex: '83'
  dsq_thread_id: '3088941754'
  _wp_old_slug: hbase-commands-bulk-operations-with-bash-script
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/hbase-mulitple-operations-with-bash-script/"
---
 ## Hbase mulitple operations with bash script or run the bulk of command from bash script


HBase's latest version shell commands that provide a jruby-style object-oriented references for tables and reference variable can be used to perform the hbase operation directly in ruby shell, but there are no way to run the same into bash script.  
Using bash pipe a table operation(put,get, scan...) can be spawn to hbase shell, single operation will be performed at a time and variable table referencing can't be implemented with bash scripting.  
Here we will run the table operations such as puts, scans, and admin functionality such as disabling, dropping, describing tables using bash script.  
A single hbase operation can be launched from bash like this-

```shell
e.g. "create 'SAMPLE', {NAME ='UP' , VERSIONS =5}'" | hbase shell
```

here is example to run the bunch of commands from shell script-

- Write all hbase commands into a file-

```
create 'TEST', {NAME =\> 'SE'} create 'SAMPLE', {NAME =\> 'SA'} , {NAME =\> 'AD' , VERSIONS =\> 5} create 'SAMPLE1', {NAME =\> 'FM'} disable 'TEST'
```

- Save all commands into a file 'hbase.script'

- Create a bash script to read the each line of hbase script and pipe the commands to hbase shell-

```bash
#!/bin/bash 

######################################### 
# Name of the Script : ddl.sh # No. of Input Parameters : 2 # Input Parameter accepted : <command filepath> <table location in hbase> | e.g. createtables.sh /home/hadoop/ /home/hadoop/hbasem7/path/
# Comment : This shell script run all the commands present in command file param $1.
###########################################

usage() {
        echo "`date +%Y%m%d%H%M%S`: Usage: $0 <hbase command file> <table location>" 1&gt;&amp;2;
        exit 1;
}
if [$# -ne 2]
then
        usage;
fi;
STATUS=0
file_path=$1
ip=$(echo ${2}| sed 's/\//\\\//g')
while read line;do
        command=$(echo ${line} | sed -e "s/#table_path#/${ip}/g")
        echo "executing command on hbase; ${command}"
        echo ${command}| hbase shell
        if ["$?" != "0"]; then
        echo "Error while creating tables" 1&gt;&amp;2
        STATUS=1;
fi
done </table>
```