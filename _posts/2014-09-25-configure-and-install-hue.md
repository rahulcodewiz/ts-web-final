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
  wp-syntax-cache-content: "a:8:{i:1;s:2815:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n9\n10\n11\n12\n13\n14\n15\n16\n17\n18\n</pre></td><td
    class=\"code\"><pre class=\"powershell\" style=\"font-family:monospace;\">Commands
    to install the required libraries<span style=\"color: pink;\">-</span>\nsudo apt<span
    style=\"color: pink;\">-</span>get install ant\nsudo apt<span style=\"color: pink;\">-</span>get
    install gcc\nsudo apt<span style=\"color: pink;\">-</span>get install  g<span
    style=\"color: pink;\">++</span>\nsudo apt<span style=\"color: pink;\">-</span>get
    install  libkrb5<span style=\"color: pink;\">-</span>dev\nsudo apt<span style=\"color:
    pink;\">-</span>get install  libmysqlclient<span style=\"color: pink;\">-</span>dev\nsudo
    apt<span style=\"color: pink;\">-</span>get install  libssl<span style=\"color:
    pink;\">-</span>dev\nsudo apt<span style=\"color: pink;\">-</span>get install
    \ libsasl2<span style=\"color: pink;\">-</span>dev\nsudo apt<span style=\"color:
    pink;\">-</span>get install  libsasl2<span style=\"color: pink;\">-</span>modules<span
    style=\"color: pink;\">-</span>gssapi<span style=\"color: pink;\">-</span>mit\nsudo
    apt<span style=\"color: pink;\">-</span>get install  libsqlite3<span style=\"color:
    pink;\">-</span>dev\nsudo apt<span style=\"color: pink;\">-</span>get install
    libtidy<span style=\"color: pink;\">-</span><span style=\"color: #804000;\">0.99</span><span
    style=\"color: pink;\">-</span><span style=\"color: #804000;\">0</span>\nsudo
    apt<span style=\"color: pink;\">-</span>get install libxml2<span style=\"color:
    pink;\">-</span>dev\nsudo apt<span style=\"color: pink;\">-</span>get install
    libxslt<span style=\"color: pink;\">-</span>dev\nsudo apt<span style=\"color:
    pink;\">-</span>get install mvn\nsudo apt<span style=\"color: pink;\">-</span>get
    install openldap<span style=\"color: pink;\">-</span>dev\nsudo apt<span style=\"color:
    pink;\">-</span>get installpython<span style=\"color: pink;\">-</span>dev\nsudo
    apt<span style=\"color: pink;\">-</span>get install python<span style=\"color:
    pink;\">-</span>simplejson\nsudo apt<span style=\"color: pink;\">-</span>get install
    python<span style=\"color: pink;\">-</span>setuptools</pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">Commands to install the required libraries-\r\nsudo
    apt-get install ant\r\nsudo apt-get install gcc\r\nsudo apt-get install  g++\r\nsudo
    apt-get install  libkrb5-dev\r\nsudo apt-get install  libmysqlclient-dev\r\nsudo
    apt-get install  libssl-dev\r\nsudo apt-get install  libsasl2-dev\r\nsudo apt-get
    install  libsasl2-modules-gssapi-mit\r\nsudo apt-get install  libsqlite3-dev\r\nsudo
    apt-get install libtidy-0.99-0\r\nsudo apt-get install libxml2-dev\r\nsudo apt-get
    install libxslt-dev\r\nsudo apt-get install mvn\r\nsudo apt-get install openldap-dev\r\nsudo
    apt-get installpython-dev\r\nsudo apt-get install python-simplejson\r\nsudo apt-get
    install python-setuptools</p></div>\n\";i:2;s:561:\"\n<div class=\"wp_syntax\"
    style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n3\n</pre></td><td
    class=\"code\"><pre class=\"powershell\" style=\"font-family:monospace;\">unzip
    hue<span style=\"color: pink;\">-</span>master.zip <span style=\"color: pink;\">-</span>d
    hue\n<span style=\"color: #008080; font-weight: bold;\">cd</span> hue<span style=\"color:
    pink;\">/</span>hue<span style=\"color: pink;\">-</span>master\nmake apps</pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">unzip hue-master.zip -d hue\r\ncd hue/hue-master\r\nmake
    apps</p></div>\n\";i:3;s:751:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n</pre></td><td class=\"code\"><pre
    class=\"powershell\" style=\"font-family:monospace;\">vi ~<span style=\"color:
    pink;\">/</span>.bashrc\nexport HUE_HOME\ne.g. export HUE_HOME<span style=\"color:
    pink;\">=/</span>home<span style=\"color: pink;\">/</span>ubuntu<span style=\"color:
    pink;\">/</span>software<span style=\"color: pink;\">/</span>hue<span style=\"color:
    pink;\">/</span>hue<span style=\"color: pink;\">-</span>master\n&nbsp;\nsource
    ~<span style=\"color: pink;\">/</span>.bashrc</pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">vi ~/.bashrc\r\nexport HUE_HOME\r\ne.g. export HUE_HOME=/home/ubuntu/software/hue/hue-master\r\n\r\nsource
    ~/.bashrc</p></div>\n\";i:4;s:1102:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n</pre></td><td class=\"code\"><pre
    class=\"powershell\" style=\"font-family:monospace;\">vi <span style=\"color:
    #800080;\">$HADOOP_HOME</span><span style=\"color: pink;\">/</span>conf<span style=\"color:
    pink;\">/</span>hdfs<span style=\"color: pink;\">-</span>site.xml\n<span style=\"color:
    pink;\">&lt;</span>property<span style=\"color: pink;\">&gt;</span>\n<span style=\"color:
    pink;\">&lt;</span>name<span style=\"color: pink;\">&gt;</span>dfs.webhdfs.enabled<span
    style=\"color: pink;\">&lt;/</span>name<span style=\"color: pink;\">&gt;</span>\n<span
    style=\"color: pink;\">&lt;</span>value<span style=\"color: pink;\">&gt;</span>true<span
    style=\"color: pink;\">&lt;</span>value<span style=\"color: pink;\">&gt;</span>\n<span
    style=\"color: pink;\">&lt;/</span>property<span style=\"color: pink;\">&gt;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">vi $HADOOP_HOME/conf/hdfs-site.xml\r\n&lt;property&gt;\r\n&lt;name&gt;dfs.webhdfs.enabled&lt;/name&gt;\r\n&lt;value&gt;true&lt;value&gt;\r\n&lt;/property&gt;</p></div>\n\";i:5;s:1951:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n9\n10\n</pre></td><td
    class=\"code\"><pre class=\"powershell\" style=\"font-family:monospace;\">vi <span
    style=\"color: #800080;\">$HADOOP_HOME</span><span style=\"color: pink;\">/</span>conf<span
    style=\"color: pink;\">/</span>core<span style=\"color: pink;\">-</span>site.html.\n&nbsp;\n<span
    style=\"color: pink;\">&lt;</span>property<span style=\"color: pink;\">&gt;</span>\n<span
    style=\"color: pink;\">&lt;</span>name<span style=\"color: pink;\">&gt;</span>hadoop.proxyuser.hue.hosts<span
    style=\"color: pink;\">&lt;/</span>name<span style=\"color: pink;\">&gt;</span>\n<span
    style=\"color: pink;\">&lt;</span>value<span style=\"color: pink;\">&gt;*&lt;/</span>value<span
    style=\"color: pink;\">&gt;</span>\n<span style=\"color: pink;\">&lt;</span>property<span
    style=\"color: pink;\">&gt;</span>\n<span style=\"color: pink;\">&lt;</span>property<span
    style=\"color: pink;\">&gt;</span>\n<span style=\"color: pink;\">&lt;</span>name<span
    style=\"color: pink;\">&gt;</span>hadoop.proxyuser.hue.groups<span style=\"color:
    pink;\">&lt;/</span>name<span style=\"color: pink;\">&gt;</span>\n<span style=\"color:
    pink;\">&lt;</span>value<span style=\"color: pink;\">&gt;*&lt;/</span>value<span
    style=\"color: pink;\">&gt;</span>\n<span style=\"color: pink;\">&lt;</span>property<span
    style=\"color: pink;\">&gt;&lt;</span>code class<span style=\"color: pink;\">=</span><span
    style=\"color: #800000;\">&quot;literal&quot;</span><span style=\"color: pink;\">&gt;&lt;/</span>code<span
    style=\"color: pink;\">&gt;</span></pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">vi $HADOOP_HOME/conf/core-site.html.\r\n\r\n&lt;property&gt;\r\n&lt;name&gt;hadoop.proxyuser.hue.hosts&lt;/name&gt;\r\n&lt;value&gt;*&lt;/value&gt;\r\n&lt;property&gt;\r\n&lt;property&gt;\r\n&lt;name&gt;hadoop.proxyuser.hue.groups&lt;/name&gt;\r\n&lt;value&gt;*&lt;/value&gt;\r\n&lt;property&gt;&lt;code
    class=&quot;literal&quot;&gt;&lt;/code&gt;</p></div>\n\";i:6;s:662:\"\n<div class=\"wp_syntax\"
    style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n</pre></td><td
    class=\"code\"><pre class=\"powershell\" style=\"font-family:monospace;\">sh <span
    style=\"color: #800080;\">$HADOOP_HOME</span><span style=\"color: pink;\">/</span>bin<span
    style=\"color: pink;\">/</span>stop<span style=\"color: pink;\">-</span>all.sh\nsh
    <span style=\"color: #800080;\">$HADOOP_HOME</span><span style=\"color: pink;\">/</span>bin<span
    style=\"color: pink;\">/</span>start<span style=\"color: pink;\">-</span>all.sh</pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">sh $HADOOP_HOME/bin/stop-all.sh\r\nsh
    $HADOOP_HOME/bin/start-all.sh</p></div>\n\";i:7;s:3325:\"\n<div class=\"wp_syntax\"
    style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n9\n10\n11\n12\n13\n14\n15\n</pre></td><td
    class=\"code\"><pre class=\"powershell\" style=\"font-family:monospace;\"><span
    style=\"color: #008080; font-weight: bold;\">copy</span> hue jar files to hadoop
    lib\n<span style=\"color: #008080; font-weight: bold;\">cp</span> <span style=\"color:
    #800080;\">$HUE_HOME</span><span style=\"color: pink;\">/</span>desktop<span style=\"color:
    pink;\">/</span>libs<span style=\"color: pink;\">/</span>hadoop<span style=\"color:
    pink;\">/</span>java<span style=\"color: pink;\">-</span>lib<span style=\"color:
    pink;\">/</span>hue<span style=\"color: pink;\">-</span>plugins<span style=\"color:
    pink;\">-*</span>.jar <span style=\"color: #800080;\">$HADOOP_HOME</span><span
    style=\"color: pink;\">/</span>lib<span style=\"color: pink;\">/</span>.\n&nbsp;\nadd
    the below properties to mapred<span style=\"color: pink;\">-</span>site.xml then
    restart the job<span style=\"color: pink;\">-</span>tracker\nvi <span style=\"color:
    #800080;\">$HADOOP_HOME</span><span style=\"color: pink;\">/</span>conf<span style=\"color:
    pink;\">/</span>mapred<span style=\"color: pink;\">-</span>site.html\n&nbsp;\n<span
    style=\"color: pink;\">&lt;</span>property<span style=\"color: pink;\">&gt;</span>\n<span
    style=\"color: pink;\">&lt;</span>name<span style=\"color: pink;\">&gt;</span>jobtracker.thrift.address<span
    style=\"color: pink;\">&lt;/</span>name<span style=\"color: pink;\">&gt;</span>\n<span
    style=\"color: pink;\">&lt;</span>value<span style=\"color: pink;\">&gt;</span>0.0.0.0:<span
    style=\"color: #804000;\">9290</span><span style=\"color: pink;\">&lt;/</span>value<span
    style=\"color: pink;\">&gt;</span>\n<span style=\"color: pink;\">&lt;</span>property<span
    style=\"color: pink;\">&gt;</span>\n<span style=\"color: pink;\">&lt;</span>property<span
    style=\"color: pink;\">&gt;</span>\n<span style=\"color: pink;\">&lt;</span>name<span
    style=\"color: pink;\">&gt;</span>mapred.jobtracker.plugins<span style=\"color:
    pink;\">&lt;/</span>name<span style=\"color: pink;\">&gt;</span>\n<span style=\"color:
    pink;\">&lt;</span>value<span style=\"color: pink;\">&gt;</span>org.apache.hadoop.thriftfs.ThriftJobTrackerPlugin<span
    style=\"color: pink;\">&lt;/</span>value<span style=\"color: pink;\">&gt;</span>\n<span
    style=\"color: pink;\">&lt;</span>description<span style=\"color: pink;\">&gt;</span>Comma<span
    style=\"color: pink;\">-</span>separated list of jobtracker plug<span style=\"color:
    pink;\">-</span>ins to be activated.<span style=\"color: pink;\">&lt;/</span>description<span
    style=\"color: pink;\">&gt;</span>\n<span style=\"color: pink;\">&lt;</span>property<span
    style=\"color: pink;\">&gt;</span></pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">copy hue jar files to hadoop lib\r\ncp $HUE_HOME/desktop/libs/hadoop/java-lib/hue-plugins-*.jar
    $HADOOP_HOME/lib/.\r\n\r\nadd the below properties to mapred-site.xml then restart
    the job-tracker\r\nvi $HADOOP_HOME/conf/mapred-site.html\r\n\r\n&lt;property&gt;\r\n&lt;name&gt;jobtracker.thrift.address&lt;/name&gt;\r\n&lt;value&gt;0.0.0.0:9290&lt;/value&gt;\r\n&lt;property&gt;\r\n&lt;property&gt;\r\n&lt;name&gt;mapred.jobtracker.plugins&lt;/name&gt;\r\n&lt;value&gt;org.apache.hadoop.thriftfs.ThriftJobTrackerPlugin&lt;/value&gt;\r\n&lt;description&gt;Comma-separated
    list of jobtracker plug-ins to be activated.&lt;/description&gt;\r\n&lt;property&gt;</p></div>\n\";i:8;s:831:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n</pre></td><td
    class=\"code\"><pre class=\"html\" style=\"font-family:monospace;\">&lt;property&gt;\r\n&lt;name&gt;oozie.service.ProxyUserService.proxyuser.hue.hosts&lt;/name&gt;\r\n&lt;value&gt;*&lt;/value&gt;\r\n&lt;property&gt;\r\n&lt;property&gt;\r\n&lt;name&gt;oozie.service.ProxyUserService.proxyuser.hue.groups&lt;/name&gt;\r\n&lt;value&gt;*&lt;/value&gt;\r\n&lt;property&gt;</pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">&lt;property&gt;\r\n&lt;name&gt;oozie.service.ProxyUserService.proxyuser.hue.hosts&lt;/name&gt;\r\n&lt;value&gt;*&lt;/value&gt;\r\n&lt;property&gt;\r\n&lt;property&gt;\r\n&lt;name&gt;oozie.service.ProxyUserService.proxyuser.hue.groups&lt;/name&gt;\r\n&lt;value&gt;*&lt;/value&gt;\r\n&lt;property&gt;</p></div>\n\";}"
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/configure-and-install-hue/"
---
Configure and install Hue-  
1- Hue Native lib dependencies-  
Hue has many modules which are dependent on native library.

```
Commands to install the required libraries- sudo apt-get install ant sudo apt-get install gcc sudo apt-get install g++ sudo apt-get install libkrb5-dev sudo apt-get install libmysqlclient-dev sudo apt-get install libssl-dev sudo apt-get install libsasl2-dev sudo apt-get install libsasl2-modules-gssapi-mit sudo apt-get install libsqlite3-dev sudo apt-get install libtidy-0.99-0 sudo apt-get install libxml2-dev sudo apt-get install libxslt-dev sudo apt-get install mvn sudo apt-get install openldap-dev sudo apt-get installpython-dev sudo apt-get install python-simplejson sudo apt-get install python-setuptools
```

2- download hue from Github-[https://codeload.github.com/cloudera/hue/zip/master](https://codeload.github.com/cloudera/hue/zip/master)

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

