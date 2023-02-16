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

1. Call java static method from bash in jshell-

```bash
echo 'String.format("%06d", 19)'|jshell 

output: | Welcome to JShell -- Version 9 | For an introduction type: /help intro jshell\> String.format("%06d", 19) $1 ==\> "000019"
```

Run jshell in concise feedback mode to skip Command and Declaration details and filter result.

```
echo 'String.format("%06d", 19)' | jshell --feedback concise \
| sed -n '2p' |sed -En 's/[^\>]\*\>(.+)/\1/gp'
```

2. We can call stanalone java utilities from jshell, below example uses java module and jshell to run custom utilities.  
 Create below directory structure and java classes**

```
tree common-utils/src common-utils/src 
└── com.ts.util 
├── com 
│ └── ts 
│ └── util 
│ └── Utils.java 
└── module-info.java
```

3. Let's create a simple utility class and run with jshell

Utils.java

```java
package com.ts.util; 
import java.util.regex.Pattern; 

public class Utils {
  /* Regex Replace example using pattern 
  @param input source string 
  @param regex regex to search pattern 
  @param replacement replacement string 
  @return 
  */ 

  public static String regexReplace(String input, String regex, String replacement){ 
    validateArg(input,"input"); 
    validateArg(input,"regex"); 
    validateArg(input,"replacement"); 
    return Pattern.compile(regex).matcher(input).replaceAll(replacement); } 
    
    private static void validateArg(String input,String type) { 
      if(input == null || input.isEmpty()){ 
        System.err.println(String.format("%s is blank",type)); System.exit(1); 
      } 
    } 
}
```

module-info.java

```
module com.ts.util {}
```

4. Compile module and classes**

```bash
javac -d mods --module-source-path src $(find src -name '\*.java')
```

5. finally, lets test the implementation

```bash
java -p mods -m com.ts.util/com.ts.util.Utils
```

**Create package/jar**

```
jar --create --file=mods/com.ts.util@1.0.jar --module-version=1.0 -C mods/com.ts.util . jar --create --file=mods/com.ts.util.jar --main-class com.ts.util.Utils -C mods/com.ts.util .
```

**View content**

```
tree mods 
mods 
├── com.ts.util 
│  ├── com 
│  │   └── ts │
│  └── util 
│  │    └── Utils.class 
│  └── module-info.class 
├── com.ts.util.jar 
└── com.ts.util@1.0.jar
```

**All set to test on jshell-**

```
rahul$ jshell --class-path 'mods/com.ts.util@1.0.jar' 
jshell\> com.ts.util.Utils.regexReplace("jshell hello world","\\s","++") $1 ==\> "jshell++hello++world"
```

**Run from bash**

```bash
echo 'com.ts.util.Utils.regexReplace("jshell hello world","\\s","++")' \
| jshell --class-path 'mods/com.ts.util@1.0.jar' --feedback concise \
| sed -n '2p' | sed -En 's/[^>]*>(.+)/\1/gp'`
```

You can also create one more script that will take argument as java command and run on jshell

```bash
echo "$1" | jshell --class-path '/Users/rahul/Documents/jshell-example/common-utils/mods/com.ts.util@1.0.jar' \ --feedback concise |sed -n '2p' | sed -En 's/[^\>]\*\>(.+)/\1/gp'
```

**Execute command using another script**

```bash
./common-utils/bin/run-jshell.sh 'com.ts.util.Utils.regexReplace("jshell hello world","\\s","++")'
```

[Fork on github to download full source code](https://github.com/rahulsquid/jshell-example)

