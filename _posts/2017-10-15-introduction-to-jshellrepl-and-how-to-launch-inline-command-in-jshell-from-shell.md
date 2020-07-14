---
layout: post
title: Introduction to jshell/REPL and how to launch inline command in jshell from
  shell
date: 2017-10-15 06:30:15.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Big Data
- java
tags:
- java
meta:
  _edit_last: '1'
  interface_sidebarlayout: default
  _yoast_wpseo_content_score: '30'
  _yoast_wpseo_primary_category: '6'
  _oembed_cc05adbb6956ea7064c45c0812cee487: "{{unknown}}"
  _oembed_7b221c9cfa20107d9e2252c7f1029ba6: "{{unknown}}"
  _yoast_wpseo_focuskw_text_input: Jshell java module example with bash.REPL (READ
    EVALUATE Print Loop) jshell example with unix shell. How to execute jshell commands
    from bash
  _yoast_wpseo_focuskw: Jshell java module example with bash.REPL (READ EVALUATE Print
    Loop) jshell example with unix shell. How to execute jshell commands from bash
  _yoast_wpseo_linkdex: '53'
  _oembed_9e39d5532e34a3b8c4bb4623fced0a1c: "{{unknown}}"
  dsq_thread_id: '6215879667'
  _wp_old_slug: introduction-to-repl-read-evaluate-print-loop-jshell-and-how-to-launch-inline-command-in-jshell
  wp-syntax-cache-content: "a:2:{i:1;s:5297:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\"><span style=\"color:
    #000000; font-weight: bold;\">package</span> <span style=\"color: #006699;\">com.ts.util</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">java.util.regex.Pattern</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\n<span style=\"color: #000000; font-weight:
    bold;\">public</span> <span style=\"color: #000000; font-weight: bold;\">class</span>
    Utils <span style=\"color: #009900;\">&#123;</span>\n    <span style=\"color:
    #008000; font-style: italic; font-weight: bold;\">/**\n     * Regex Replace example
    using pattern\n     * @param input source string\n     * @param regex regex to
    search pattern\n     * @param replacement replacement string\n     * @return\n
    \    */</span>\n    <span style=\"color: #000000; font-weight: bold;\">public</span>
    <span style=\"color: #000000; font-weight: bold;\">static</span> <span style=\"color:
    #003399;\">String</span> regexReplace<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #003399;\">String</span> input, <span style=\"color: #003399;\">String</span>
    regex, <span style=\"color: #003399;\">String</span> replacement<span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #009900;\">&#123;</span>\n        validateArg<span
    style=\"color: #009900;\">&#40;</span>input,<span style=\"color: #0000ff;\">&quot;input&quot;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n
    \       validateArg<span style=\"color: #009900;\">&#40;</span>input,<span style=\"color:
    #0000ff;\">&quot;regex&quot;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n        validateArg<span style=\"color: #009900;\">&#40;</span>input,<span
    style=\"color: #0000ff;\">&quot;replacement&quot;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n        <span style=\"color: #000000; font-weight:
    bold;\">return</span> Pattern.<span style=\"color: #006633;\">compile</span><span
    style=\"color: #009900;\">&#40;</span>regex<span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">matcher</span><span style=\"color: #009900;\">&#40;</span>input<span
    style=\"color: #009900;\">&#41;</span>.<span style=\"color: #006633;\">replaceAll</span><span
    style=\"color: #009900;\">&#40;</span>replacement<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n    <span style=\"color: #009900;\">&#125;</span>\n&nbsp;\n
    \   <span style=\"color: #000000; font-weight: bold;\">private</span> <span style=\"color:
    #000000; font-weight: bold;\">static</span> <span style=\"color: #000066; font-weight:
    bold;\">void</span> validateArg<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #003399;\">String</span> input,<span style=\"color: #003399;\">String</span>
    type<span style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n
    \       <span style=\"color: #000000; font-weight: bold;\">if</span><span style=\"color:
    #009900;\">&#40;</span>input <span style=\"color: #339933;\">==</span> <span style=\"color:
    #000066; font-weight: bold;\">null</span> <span style=\"color: #339933;\">||</span>
    input.<span style=\"color: #006633;\">isEmpty</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#123;</span>\n            <span style=\"color: #003399;\">System</span>.<span
    style=\"color: #006633;\">err</span>.<span style=\"color: #006633;\">println</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #003399;\">String</span>.<span
    style=\"color: #006633;\">format</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;%s is blank&quot;</span>,type<span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n            <span style=\"color: #003399;\">System</span>.<span
    style=\"color: #006633;\">exit</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #cc66cc;\">1</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n        <span style=\"color: #009900;\">&#125;</span>\n
    \   <span style=\"color: #009900;\">&#125;</span>\n<span style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">package com.ts.util;\r\n\r\nimport java.util.regex.Pattern;\r\n\r\npublic
    class Utils {\r\n    /**\r\n     * Regex Replace example using pattern\r\n     *
    @param input source string\r\n     * @param regex regex to search pattern\r\n
    \    * @param replacement replacement string\r\n     * @return\r\n     */\r\n
    \   public static String regexReplace(String input, String regex, String replacement){\r\n
    \       validateArg(input,&quot;input&quot;);\r\n        validateArg(input,&quot;regex&quot;);\r\n
    \       validateArg(input,&quot;replacement&quot;);\r\n        return Pattern.compile(regex).matcher(input).replaceAll(replacement);\r\n
    \   }\r\n\r\n    private static void validateArg(String input,String type) {\r\n
    \       if(input == null || input.isEmpty()){\r\n            System.err.println(String.format(&quot;%s
    is blank&quot;,type));\r\n            System.exit(1);\r\n        }\r\n    }\r\n}</p></div>\n\";i:2;s:404:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"code\"><pre
    class=\"java\" style=\"font-family:monospace;\">module com.<span style=\"color:
    #006633;\">ts</span>.<span style=\"color: #006633;\">util</span> <span style=\"color:
    #009900;\">&#123;</span><span style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">module com.ts.util {}</p></div>\n\";}"
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/introduction-to-jshellrepl-and-how-to-launch-inline-command-in-jshell-from-shell/"
---
**Pellucid tutorial using java modules, REPL(READ EVALUATE Print Loop) jshell and how to launch jshell inline command from shell**  
Jdk-9 is one of the major shift for java developers, it has so many powerful tools and jshell is one of them. Jshell shall be used to run small commands, utilities, expressions, tough it helps to avoid developing many standalone utilities but it shouldn’t be used to run java classes directly.

[![]({{ site.baseurl }}/assets/images/jdk9-repl-150x150.png)](http://www.techsquids.com/wp-content/uploads/2017/10/jdk9-repl.png)

**1.**  **Call java static method from bash in jshell-**

```
echo 'String.format("%06d", 19)'|jshell output: | Welcome to JShell -- Version 9 | For an introduction type: /help intro jshell\> String.format("%06d", 19) $1 ==\> "000019"
```

Run jshell in concise feedback mode to skip Command and Declaration details and filter result.

```
echo 'String.format("%06d", 19)' | jshell --feedback concise \ | sed -n '2p' |sed -En 's/[^\>]\*\>(.+)/\1/gp'
```

**2. We can call stanalone java utilities from jshell, below example uses java module and jshell to run custom utilities.  
 Create below directory structure and java classes**

```
tree common-utils/src common-utils/src └── com.ts.util ├── com │ └── ts │ └── util │ └── Utils.java └── module-info.java
```

&nbsp;

**Utils.java**

```
package com.ts.util; import java.util.regex.Pattern; public class Utils { /\*\* \* Regex Replace example using pattern \* @param input source string \* @param regex regex to search pattern \* @param replacement replacement string \* @return \*/ public static String regexReplace(String input, String regex, String replacement){ validateArg(input,"input"); validateArg(input,"regex"); validateArg(input,"replacement"); return Pattern.compile(regex).matcher(input).replaceAll(replacement); } private static void validateArg(String input,String type) { if(input == null || input.isEmpty()){ System.err.println(String.format("%s is blank",type)); System.exit(1); } } }
```

module-info.java

```
module com.ts.util {}
```

**Compile module and classes**

```
javac -d mods --module-source-path src $(find src -name '\*.java')
```

**Test**

```
java -p mods -m com.ts.util/com.ts.util.Utils
```

**Create package/jar**

```
jar --create --file=mods/com.ts.util@1.0.jar --module-version=1.0 -C mods/com.ts.util . jar --create --file=mods/com.ts.util.jar --main-class com.ts.util.Utils -C mods/com.ts.util .
```

**View content**

```
tree mods mods ├── com.ts.util │&nbsp;&nbsp; ├── com │&nbsp;&nbsp; │&nbsp;&nbsp; └── ts │&nbsp;&nbsp; │&nbsp;&nbsp; └── util │&nbsp;&nbsp; │&nbsp;&nbsp; └── Utils.class │&nbsp;&nbsp; └── module-info.class ├── com.ts.util.jar └── com.ts.util@1.0.jar
```

**All set to test on jshell-**

```
rauls-MacBook-Pro:common-utils rahul$ jshell --class-path 'mods/com.ts.util@1.0.jar' | Welcome to JShell -- Version 9 | For an introduction type: /help intro jshell\> com.ts.util.Utils.regexReplace("jshell hello world","\\s","++") $1 ==\> "jshell++hello++world"
```

**Run from bash**

`echo 'com.ts.util.Utils.regexReplace("jshell hello world","\\s","++")' | jshell --class-path 'mods/com.ts.util@1.0.jar' --feedback concise |sed -n '2p' | sed -En 's/[^>]*>(.+)/\1/gp'`

You can also create one more script that will take argument as java command and run on jshell

```
echo "$1" | jshell --class-path '/Users/rahul/Documents/jshell-example/common-utils/mods/com.ts.util@1.0.jar' \ --feedback concise |sed -n '2p' | sed -En 's/[^\>]\*\>(.+)/\1/gp'
```

**Execute command using another script**

`./common-utils/bin/run-jshell.sh 'com.ts.util.Utils.regexReplace("jshell hello world","\\s","++")'
`

[Fork on github to download full source code](https://github.com/rahulsquid/jshell-example)

