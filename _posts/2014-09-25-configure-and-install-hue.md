---
layout: post
title: Configure and install Hue
date: 2014-09-25 19:54:00.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Big Data
tags:
- bigdata
meta:
  _edit_last: '1'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: Configure and install Hue
  _yoast_wpseo_title: Configure and install Hue
  _yoast_wpseo_metadesc: Configure and install Hue
  _yoast_wpseo_meta-robots-noindex: '2'
  _yoast_wpseo_linkdex: '79'
  dsq_thread_id: '3064154658'

author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/configure-and-install-hue/"
---
## Configure and install Hue-  

1- Hue Native lib dependencies-  

Hue has many modules which are dependent on native library.

```
Commands to install the required libraries- sudo apt-get install ant sudo apt-get install gcc sudo apt-get install g++ sudo apt-get install libkrb5-dev sudo apt-get install libmysqlclient-dev sudo apt-get install libssl-dev sudo apt-get install libsasl2-dev sudo apt-get install libsasl2-modules-gssapi-mit sudo apt-get install libsqlite3-dev sudo apt-get install libtidy-0.99-0 sudo apt-get install libxml2-dev sudo apt-get install libxslt-dev sudo apt-get install mvn sudo apt-get install openldap-dev sudo apt-get installpython-dev sudo apt-get install python-simplejson sudo apt-get install python-setuptools
```

2- Download hue from Github-[https://codeload.github.com/cloudera/hue/zip/master](https://codeload.github.com/cloudera/hue/zip/master)

3- Extract and build Hue-

```
unzip hue-master.zip -d hue cd hue/hue-master make apps
```

add the HUE\_HOME into .bashrc file.

```
vi ~/.bashrc export HUE\_HOME e.g. export HUE\_HOME=/home/ubuntu/software/hue/hue-master source ~/.bashrc
```

4- start the Hue server-  
build/env/bin/hue runserver

5- Hadoop Configuration-  
add below properties to hdfs-site.xml-

```
vi $HADOOP\_HOME/conf/hdfs-site.xml <property>
<name>dfs.webhdfs.enabled</name>
<value>true<value>
</value></value></property>
```

add below properties to core-site.xml-

```
vi $HADOOP\_HOME/conf/core-site.html. <property>
<name>hadoop.proxyuser.hue.hosts</name>
<value>*</value>
<property>
<property>
<name>hadoop.proxyuser.hue.groups</name>
<value>*</value>
<property><code class="literal"></code>
</property></property></property></property>
```

6- Restart the hadoop services-

```
sh $HADOOP\_HOME/bin/stop-all.sh sh $HADOOP\_HOME/bin/start-all.sh
```

7- Hadoop MapReduce cofiguration-

```
copy hue jar files to hadoop lib cp $HUE\_HOME/desktop/libs/hadoop/java-lib/hue-plugins-\*.jar $HADOOP\_HOME/lib/. add the below properties to mapred-site.xml then restart the job-tracker vi $HADOOP\_HOME/conf/mapred-site.html <property>
<name>jobtracker.thrift.address</name>
<value>0.0.0.0:9290</value>
<property>
<property>
<name>mapred.jobtracker.plugins</name>
<value>org.apache.hadoop.thriftfs.ThriftJobTrackerPlugin</value>
<description>Comma-separated list of jobtracker plug-ins to be activated.</description>
<property>
</property></property></property></property>
```

you can check the thrift service status in job-tracker's daemon log.

8- Hue submits all the jobs to oozie, to configure oozie with hue you need to update the oozie-site.xml.

```
<property>
<name>oozie.service.ProxyUserService.proxyuser.hue.hosts</name>
<value>*</value>
<property>
<property>
<name>oozie.service.ProxyUserService.proxyuser.hue.groups</name>
<value>*</value>
<property>
</property></property></property></property>
```

9- Hue comes with all default hive properties, if you have not changed any hive default configuration then you dont need to make any change for hive.

[Know more about Hue- www.gethue.com](http://gethue.com/)

