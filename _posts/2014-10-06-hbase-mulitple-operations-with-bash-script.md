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
  wp-syntax-cache-content: "a:3:{i:1;s:501:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"code\"><pre class=\"sql\" style=\"font-family:monospace;\">e<span style=\"color:
    #66cc66;\">.</span>g<span style=\"color: #66cc66;\">.</span> <span style=\"color:
    #ff0000;\">&quot;create 'SAMPLE', {NAME ='UP' , VERSIONS =5}'&quot;</span> <span
    style=\"color: #66cc66;\">|</span> hbase shell</pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">e.g. &quot;create 'SAMPLE', {NAME ='UP' , VERSIONS =5}'&quot;
    | hbase shell</p></div>\n\";i:2;s:1776:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"line_numbers\"><pre>1\n2\n3\n4\n</pre></td><td class=\"code\"><pre class=\"sql\"
    style=\"font-family:monospace;\"><span style=\"color: #993333; font-weight: bold;\">CREATE</span>
    <span style=\"color: #ff0000;\">'TEST'</span><span style=\"color: #66cc66;\">,</span>
    <span style=\"color: #66cc66;\">&#123;</span>NAME <span style=\"color: #66cc66;\">=&gt;</span>
    <span style=\"color: #ff0000;\">'SE'</span><span style=\"color: #66cc66;\">&#125;</span>\n<span
    style=\"color: #993333; font-weight: bold;\">CREATE</span> <span style=\"color:
    #ff0000;\">'SAMPLE'</span><span style=\"color: #66cc66;\">,</span> <span style=\"color:
    #66cc66;\">&#123;</span>NAME <span style=\"color: #66cc66;\">=&gt;</span> <span
    style=\"color: #ff0000;\">'SA'</span><span style=\"color: #66cc66;\">&#125;</span>
    <span style=\"color: #66cc66;\">,</span> <span style=\"color: #66cc66;\">&#123;</span>NAME
    <span style=\"color: #66cc66;\">=&gt;</span> <span style=\"color: #ff0000;\">'AD'</span>
    <span style=\"color: #66cc66;\">,</span> VERSIONS <span style=\"color: #66cc66;\">=&gt;</span>
    <span style=\"color: #cc66cc;\">5</span><span style=\"color: #66cc66;\">&#125;</span>\n<span
    style=\"color: #993333; font-weight: bold;\">CREATE</span> <span style=\"color:
    #ff0000;\">'SAMPLE1'</span><span style=\"color: #66cc66;\">,</span> <span style=\"color:
    #66cc66;\">&#123;</span>NAME <span style=\"color: #66cc66;\">=&gt;</span> <span
    style=\"color: #ff0000;\">'FM'</span><span style=\"color: #66cc66;\">&#125;</span>\ndisable
    <span style=\"color: #ff0000;\">'TEST'</span></pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">create 'TEST', {NAME =&gt; 'SE'}\r\ncreate 'SAMPLE', {NAME
    =&gt; 'SA'} , {NAME =&gt; 'AD' , VERSIONS =&gt; 5}\r\ncreate 'SAMPLE1', {NAME
    =&gt; 'FM'}\r\ndisable 'TEST'</p></div>\n\";i:3;s:5205:\"\n<div class=\"wp_syntax\"
    style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n9\n10\n11\n12\n13\n14\n15\n16\n17\n18\n19\n20\n21\n22\n23\n24\n25\n26\n27\n28\n</pre></td><td
    class=\"code\"><pre class=\"powershell\" style=\"font-family:monospace;\"><span
    style=\"color: #008000;\">#!/bin/bash</span>\n<span style=\"color: #008000;\">#########################################</span>\n<span
    style=\"color: #008000;\"># Name of the Script        : ddl.sh</span>\n<span style=\"color:
    #008000;\"># No. of Input Parameters   : 2</span>\n<span style=\"color: #008000;\">#
    Input Parameter accepted  : &lt;command filepath&gt; &lt;table location in hbase&gt;
    | e.g. createtables.sh /home/hadoop/ /home/hadoop/hbasem7/path/</span>\n<span
    style=\"color: #008000;\"># Comment                   : This shell script run
    all the commands present in command file param $1.</span>\n<span style=\"color:
    #008000;\">###########################################</span>\nusage<span style=\"color:
    #000000;\">&#40;</span><span style=\"color: #000000;\">&#41;</span> <span style=\"color:
    #000000;\">&#123;</span>\n        <span style=\"color: #008080; font-weight: bold;\">echo</span>
    <span style=\"color: #800000;\">&quot;<span style=\"color: #008080; font-weight:
    bold;\">`d</span>ate +%Y%m%d%H%M%S<span style=\"color: #008080; font-weight: bold;\">`:</span>
    Usage: $0 &lt;hbase command file&gt; &lt;table location&gt;&quot;</span> <span
    style=\"color: #804000;\">1</span><span style=\"color: pink;\">&gt;&amp;</span><span
    style=\"color: #804000;\">2</span>;\n        exit <span style=\"color: #804000;\">1</span>;\n<span
    style=\"color: #000000;\">&#125;</span>\n<span style=\"color: #0000FF;\">if</span>
    <span style=\"color: #000000;\">&#91;</span> $<span style=\"color: #008000;\">#
    -ne 2 ]</span>\nthen\n        usage;\nfi;\nSTATUS<span style=\"color: pink;\">=</span><span
    style=\"color: #804000;\">0</span>\nfile_path<span style=\"color: pink;\">=</span><span
    style=\"color: #800080;\">$1</span>\nip<span style=\"color: pink;\">=</span>$<span
    style=\"color: #000000;\">&#40;</span><span style=\"color: #008080; font-weight:
    bold;\">echo</span> $<span style=\"color: #000000;\">&#123;</span><span style=\"color:
    #804000;\">2</span><span style=\"color: #000000;\">&#125;</span><span style=\"color:
    pink;\">|</span> sed <span style=\"color: #800000;\">'s/\\//\\\\\\//g'</span><span
    style=\"color: #000000;\">&#41;</span>\n<span style=\"color: #0000FF;\">while</span>
    read line;<span style=\"color: #0000FF;\">do</span>\n        command<span style=\"color:
    pink;\">=</span>$<span style=\"color: #000000;\">&#40;</span><span style=\"color:
    #008080; font-weight: bold;\">echo</span> $<span style=\"color: #000000;\">&#123;</span>line<span
    style=\"color: #000000;\">&#125;</span> <span style=\"color: pink;\">|</span>
    sed <span style=\"color: pink;\">-</span>e <span style=\"color: #800000;\">&quot;s/#table_path#/${ip}/g&quot;</span><span
    style=\"color: #000000;\">&#41;</span>\n        <span style=\"color: #008080;
    font-weight: bold;\">echo</span> <span style=\"color: #800000;\">&quot;executing
    command on hbase; ${command}&quot;</span>\n        <span style=\"color: #008080;
    font-weight: bold;\">echo</span> $<span style=\"color: #000000;\">&#123;</span>command<span
    style=\"color: #000000;\">&#125;</span><span style=\"color: pink;\">|</span> hbase
    shell\n        <span style=\"color: #0000FF;\">if</span> <span style=\"color:
    #000000;\">&#91;</span> <span style=\"color: #800000;\">&quot;$?&quot;</span>
    <span style=\"color: pink;\">!=</span> <span style=\"color: #800000;\">&quot;0&quot;</span>
    <span style=\"color: #000000;\">&#93;</span>; then\n        <span style=\"color:
    #008080; font-weight: bold;\">echo</span> <span style=\"color: #800000;\">&quot;Error
    while creating tables&quot;</span> <span style=\"color: #804000;\">1</span><span
    style=\"color: pink;\">&gt;&amp;</span><span style=\"color: #804000;\">2</span>\n
    \       STATUS<span style=\"color: pink;\">=</span><span style=\"color: #804000;\">1</span>;\nfi\ndone
    <span style=\"color: pink;\">&lt;</span><span style=\"color: #800000;\">&quot;${file_path}&quot;</span>\nexit
    $<span style=\"color: #000000;\">&#123;</span>STATUS<span style=\"color: #000000;\">&#125;</span>;</pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">#!/bin/bash\r\n#########################################\r\n#
    Name of the Script        : ddl.sh\r\n# No. of Input Parameters   : 2\r\n# Input
    Parameter accepted  : &lt;command filepath&gt; &lt;table location in hbase&gt;
    | e.g. createtables.sh /home/hadoop/ /home/hadoop/hbasem7/path/\r\n# Comment                   :
    This shell script run all the commands present in command file param $1.\r\n###########################################\r\nusage()
    {\r\n        echo &quot;`date +%Y%m%d%H%M%S`: Usage: $0 &lt;hbase command file&gt;
    &lt;table location&gt;&quot; 1&gt;&amp;2;\r\n        exit 1;\r\n}\r\nif [ $# -ne
    2 ]\r\nthen\r\n        usage;\r\nfi;\r\nSTATUS=0\r\nfile_path=$1\r\nip=$(echo
    ${2}| sed 's/\\//\\\\\\//g')\r\nwhile read line;do\r\n        command=$(echo ${line}
    | sed -e &quot;s/#table_path#/${ip}/g&quot;)\r\n        echo &quot;executing command
    on hbase; ${command}&quot;\r\n        echo ${command}| hbase shell\r\n        if
    [ &quot;$?&quot; != &quot;0&quot; ]; then\r\n        echo &quot;Error while creating
    tables&quot; 1&gt;&amp;2\r\n        STATUS=1;\r\nfi\r\ndone &lt;&quot;${file_path}&quot;\r\nexit
    ${STATUS};</p></div>\n\";}"
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/hbase-mulitple-operations-with-bash-script/"
---
 **Hbase mulitple operations with bash script or run the bulk of command from bash script**  
HBase latest version shell commands that provide a jruby-style object-oriented references for tables and reference variable can be used to perform the hbase operation directly in ruby shell, but there are no way to run the same into bash script.  
Using bash pipe a table operation(put,get, scan...) can be spawn to hbase shell, single operation will be performed at a time and variable table referencing can't be implemented with bash scripting.  
Here we will run the table operations such as puts, scans, and admin functionality such as disabling, dropping, describing tables using bash script.  
A single hbase operation can be launched from bash like this-

```
e.g. "create 'SAMPLE', {NAME ='UP' , VERSIONS =5}'" | hbase shell
```

here is example to run the bunch of commands from shell script-

- write all hbase commands into a file-

```
create 'TEST', {NAME =\> 'SE'} create 'SAMPLE', {NAME =\> 'SA'} , {NAME =\> 'AD' , VERSIONS =\> 5} create 'SAMPLE1', {NAME =\> 'FM'} disable 'TEST'
```

save all commands into a file 'hbase.script'

- create a bash script to read the each line of hbase script and pipe the commands to hbase shell-

```
#!/bin/bash ######################################### # Name of the Script : ddl.sh # No. of Input Parameters : 2 # Input Parameter accepted : <command filepath> <table location in hbase> | e.g. createtables.sh /home/hadoop/ /home/hadoop/hbasem7/path/
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

<p>find complete source at <a href="https://github.com/rahul86s/techsquids.git" title="github" target="_blank">github</a> under hbase root.</p>
</hbase>
</table></command>
```
