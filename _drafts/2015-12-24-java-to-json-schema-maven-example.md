---
layout: post
title: Java to json schema maven example
date: 2015-12-24 02:03:26.000000000 -08:00
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
  _yoast_wpseo_focuskw: Java to json schema maven example
  _yoast_wpseo_title: Java to json schema maven example
  _yoast_wpseo_metadesc: Java to json schema maven example
  _yoast_wpseo_linkdex: '63'
  dsq_thread_id: '4544694644'
  wp-syntax-cache-content: "a:2:{i:1;s:2260:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n</pre></td><td class=\"code\"><pre
    class=\"xml\" style=\"font-family:monospace;\"><span style=\"color: #009900;\"><span
    style=\"color: #000000; font-weight: bold;\">&lt;dependencies<span style=\"color:
    #000000; font-weight: bold;\">&gt;</span></span></span>\n\t<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>com.fasterxml.jackson.module<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/groupId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>jackson-module-jsonSchema<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/artifactId<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>2.4.1<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/version<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n\t\t<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/dependency<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/dependencies<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">&lt;dependencies&gt;\r\n\t&lt;dependency&gt;\r\n\t\t\t&lt;groupId&gt;com.fasterxml.jackson.module&lt;/groupId&gt;\r\n\t\t\t&lt;artifactId&gt;jackson-module-jsonSchema&lt;/artifactId&gt;\r\n\t\t\t&lt;version&gt;2.4.1&lt;/version&gt;\r\n\t\t&lt;/dependency&gt;\r\n&lt;/dependencies&gt;</p></div>\n\";i:2;s:2795:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n</pre></td><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\"> <span style=\"color:
    #000000; font-weight: bold;\">public</span> <span style=\"color: #000000; font-weight:
    bold;\">static</span> <span style=\"color: #000066; font-weight: bold;\">void</span>
    \ jsonSchemaGenerator<span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #009900;\">&#41;</span> <span style=\"color: #000000; font-weight: bold;\">throws</span>
    JsonProcessingException<span style=\"color: #009900;\">&#123;</span>\n      ObjectMapper
    mapper <span style=\"color: #339933;\">=</span> <span style=\"color: #000000;
    font-weight: bold;\">new</span> ObjectMapper<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n
    \     SchemaFactoryWrapper actionRes <span style=\"color: #339933;\">=</span>
    <span style=\"color: #000000; font-weight: bold;\">new</span> SchemaFactoryWrapper<span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n      mapper.<span style=\"color: #006633;\">acceptJsonFormatVisitor</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #003399;\">Object</span>.<span
    style=\"color: #000000; font-weight: bold;\">class</span>, actionRes<span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n      JsonSchema
    schema <span style=\"color: #339933;\">=</span> actionRes.<span style=\"color:
    #006633;\">finalSchema</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n
    \     <span style=\"color: #003399;\">System</span>.<span style=\"color: #006633;\">out</span>.<span
    style=\"color: #006633;\">println</span><span style=\"color: #009900;\">&#40;</span>mapper.<span
    style=\"color: #006633;\">writerWithDefaultPrettyPrinter</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>.<span style=\"color:
    #006633;\">writeValueAsString</span><span style=\"color: #009900;\">&#40;</span>schema<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n    <span style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\"> public static void  jsonSchemaGenerator()
    throws JsonProcessingException{\r\n      ObjectMapper mapper = new ObjectMapper();\r\n
    \     SchemaFactoryWrapper actionRes = new SchemaFactoryWrapper();\r\n      mapper.acceptJsonFormatVisitor(Object.class,
    actionRes);\r\n      JsonSchema schema = actionRes.finalSchema();\r\n      System.out.println(mapper.writerWithDefaultPrettyPrinter().writeValueAsString(schema));\r\n
    \   }</p></div>\n\";}"
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/java/java-to-json-schema-maven-example/"
---
 **Java to json schema maven example:**  
YAML and JSON are simple and nice format for structured data and easier for human to read and write than XML. But there have been no schema for YAML such as RelaxNG or DTD. Below is an example that convert java object to json schema. Check post for java object to yaml example**[java to yaml](http://www.techsquids.com/java/java-to-yaml-schema-maven-example/)**

- Create java maven project; **[maven](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html)**
- Add below dependencies to your project:

```
<dependencies>
	<dependency>
			<groupid>com.fasterxml.jackson.module</groupid>
			<artifactid>jackson-module-jsonSchema</artifactid>
			<version>2.4.1</version>
		</dependency>
</dependencies>
```
- Create class that you want to convert to json schema. In example I have used Object class, replace it with your own class-

```
public static void jsonSchemaGenerator() throws JsonProcessingException{ ObjectMapper mapper = new ObjectMapper(); SchemaFactoryWrapper actionRes = new SchemaFactoryWrapper(); mapper.acceptJsonFormatVisitor(Object.class, actionRes); JsonSchema schema = actionRes.finalSchema(); System.out.println(mapper.writerWithDefaultPrettyPrinter().writeValueAsString(schema)); }
```
