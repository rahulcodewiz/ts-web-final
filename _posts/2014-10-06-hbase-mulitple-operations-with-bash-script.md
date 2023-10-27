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
 ## Automating HBase Operations with Bash Scripts

HBase is a popular NoSQL database that provides a distributed, scalable, and high-performance solution for handling large datasets. While HBase provides a shell with built-in commands for managing tables and data, it can be challenging to automate complex operations or perform bulk tasks using the standard shell. In this blog, we'll explore how you can perform multiple HBase operations using a Bash script, enabling you to streamline tasks and manage your HBase database more efficiently.

*The Limitations of HBase Shell*: HBase's shell commands offer a jruby-style object-oriented approach to managing tables and data. You can use these commands directly in the Ruby shell. However, when it comes to running these commands from a Bash script, things get a bit tricky. While you can use Bash to pipe a single operation like 'put,' 'get,' or 'scan' to the HBase shell, running multiple operations in a script can be cumbersome.

Furthermore, you cannot create variable references to HBase tables using Bash scripting. This limitation makes it challenging to build reusable scripts for complex HBase tasks.


To overcome the limitations of the HBase shell and automate multiple HBase operations, we'll create a Bash script that runs various HBase commands. Here's a step-by-step guide:

First, gather all the HBase commands you want to execute. For instance, you may want to create tables, put data, scan tables, or perform administrative tasks like disabling or dropping tables. Write all these commands in a text file, let's call it 'hbase.script.'

```shell
e.g. "create 'SAMPLE', {NAME ='UP' , VERSIONS =5}'" | hbase shell
```

```
create 'TEST', {NAME => 'SE'}
create 'SAMPLE', {NAME => 'SA'}
create 'SAMPLE1', {NAME => 'FM'}
disable 'TEST'
```

Now, create a Bash script that reads each line from the 'hbase.script' file and pipes these commands to the HBase shell. Here's an example script, which we'll name 'ddl.sh':


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

You can run the 'ddl.sh' script with the following command:

```bash
./ddl.sh hbase.script /path/to/your/table
```
Make sure to replace /path/to/your/table with the actual table location in HBase.


In summary, this approach allows you to perform operations with ease. So, whether you need to create, modify, or administratively manage HBase tables, using a Bash script is a powerful way to simplify the process.