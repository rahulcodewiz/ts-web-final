---
layout: post
title: Java to yaml schema maven example
date: 2015-12-24 01:56:18.000000000 -08:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- java
tags:
- java
meta:
  _edit_last: '1'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: Java to yaml schema maven example
  _yoast_wpseo_title: Java to yaml schema maven example
  _yoast_wpseo_metadesc: Java to yaml schema maven example
  _yoast_wpseo_linkdex: '65'
  dsq_thread_id: '4429004354'
  wp-syntax-cache-content: "a:2:{i:1;s:3788:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n9\n10\n11\n12\n</pre></td><td
    class=\"code\"><pre class=\"xml\" style=\"font-family:monospace;\"><span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;dependencies<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>org.yaml<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>snakeyaml<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>1.16<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>com.esotericsoftware.yamlbeans<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>yamlbeans<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>1.09<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/dependencies<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">&lt;dependencies&gt;\r\n&lt;dependency&gt;\r\n\t\t\t&lt;groupId&gt;org.yaml&lt;/groupId&gt;\r\n\t\t\t&lt;artifactId&gt;snakeyaml&lt;/artifactId&gt;\r\n\t\t\t&lt;version&gt;1.16&lt;/version&gt;\r\n\t\t&lt;/dependency&gt;\r\n\t\t&lt;dependency&gt;\r\n\t\t\t&lt;groupId&gt;com.esotericsoftware.yamlbeans&lt;/groupId&gt;\r\n\t\t\t&lt;artifactId&gt;yamlbeans&lt;/artifactId&gt;\r\n\t\t\t&lt;version&gt;1.09&lt;/version&gt;\r\n\t\t&lt;/dependency&gt;\r\n&lt;/dependencies&gt;</p></div>\n\";i:2;s:2724:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n</pre></td><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\"> <span style=\"color:
    #000000; font-weight: bold;\">public</span> <span style=\"color: #000000; font-weight:
    bold;\">static</span> <span style=\"color: #000066; font-weight: bold;\">void</span>
    yamlGenerator<span style=\"color: #009900;\">&#40;</span>  <span style=\"color:
    #009900;\">&#41;</span> <span style=\"color: #000000; font-weight: bold;\">throws</span>
    <span style=\"color: #003399;\">IOException</span>\n    <span style=\"color: #009900;\">&#123;</span>\n
    \     <span style=\"color: #003399;\">Object</span> obj<span style=\"color: #339933;\">=</span><span
    style=\"color: #000000; font-weight: bold;\">new</span> <span style=\"color: #003399;\">Object</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n      YamlWriter writer <span style=\"color:
    #339933;\">=</span> <span style=\"color: #000000; font-weight: bold;\">new</span>
    YamlWriter<span style=\"color: #009900;\">&#40;</span><span style=\"color: #000000;
    font-weight: bold;\">new</span> <span style=\"color: #003399;\">FileWriter</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #0000ff;\">&quot;Object.yaml&quot;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n      writer.<span style=\"color: #006633;\">getConfig</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">setClassTag</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;Object&quot;</span>, <span style=\"color: #003399;\">Object</span>.<span
    style=\"color: #000000; font-weight: bold;\">class</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n      writer.<span
    style=\"color: #006633;\">write</span><span style=\"color: #009900;\">&#40;</span>obj<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n
    \     writer.<span style=\"color: #006633;\">close</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n    <span style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\"> public static void yamlGenerator(  )
    throws IOException\r\n    {\r\n      Object obj=new Object();\r\n      YamlWriter
    writer = new YamlWriter(new FileWriter(&quot;Object.yaml&quot;));\r\n      writer.getConfig().setClassTag(&quot;Object&quot;,
    Object.class);\r\n      writer.write(obj);\r\n      writer.close();\r\n    }</p></div>\n\";}"
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/java/java-to-yaml-schema-maven-example/"
---
 **Java to yaml schema maven example:**  
YAML and JSON are simple and nice format for structured data and easier for human to read and write than XML. But there have been no schema for YAML such as RelaxNG or DTD. Below is an example that convert java object to yaml.

- Create java maven project; **[maven](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html)**
- Add below dependencies to your project:

```
<dependencies>
<dependency>
			<groupid>org.yaml</groupid>
			<artifactid>snakeyaml</artifactid>
			<version>1.16</version>
		</dependency>
		<dependency>
			<groupid>com.esotericsoftware.yamlbeans</groupid>
			<artifactid>yamlbeans</artifactid>
			<version>1.09</version>
		</dependency>
</dependencies>
```
- Create java Object that you want to convert to yaml. In example I have used Object class, replace it with your own class object

```
public static void yamlGenerator( ) throws IOException { Object obj=new Object(); YamlWriter writer = new YamlWriter(new FileWriter("Object.yaml")); writer.getConfig().setClassTag("Object", Object.class); writer.write(obj); writer.close(); }
```
