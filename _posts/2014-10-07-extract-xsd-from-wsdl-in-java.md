---
layout: post
title: Extract XSD from WSDL in Java
date: 2014-10-07 18:20:30.000000000 -07:00
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
  _yoast_wpseo_focuskw: Extract XSD from WSDL in Java
  _yoast_wpseo_title: Extract XSD from WSDL in Java
  _yoast_wpseo_metadesc: Extract XSD from WSDL in Java, webservice top down approach
    fetch separate xsd and wsdl. create xsd from wsdl.
  _yoast_wpseo_linkdex: '79'
  dsq_thread_id: '3092988473'
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/extract-xsd-from-wsdl-in-java/"
---
 ## Extract XSD from WSDL in Java

In the top-down approach of webserivce development, we create the Web service from a WSDL file. In this approach very first service definition is written up.The complete service definition, message format, transport protocol, security and everything is described in WSDL.

wsdl has Types container for data type definitions using some type system (such as XSD), xsd could be either imported using xsd:import or written inside wsdl

if the xsd is part of WSDl and sometime you need to extract the XSD from wsdl, there are no utility to do this task for you.  
The wsimport tool from jdk 1.7 is used to parse an existing WSDL and generate required files (JAX-WS portable artifacts) for WSDL.

1. Java code to extract and write xsd into separate file.

```java
package com.ts.common.xsd; 
import java.io.File; 
import java.io.FileInputStream; 
import java.io.IOException; 
import java.io.InputStream; 
import java.io.OutputStream; 
import java.io.PrintWriter; 
import java.io.StringWriter; 
import java.util.logging.Logger; 
import javax.xml.parsers.DocumentBuilder; 
import javax.xml.parsers.DocumentBuilderFactory; 
import javax.xml.parsers.ParserConfigurationException; 
import org.apache.commons.io.output.WriterOutputStream; 
import org.w3c.dom.Document; 
import org.w3c.dom.Element; 
import org.w3c.dom.Node; 
import org.w3c.dom.NodeList; 
import org.w3c.dom.ls.DOMImplementationLS; 
import org.w3c.dom.ls.LSSerializer; 
public class WsdlToXsdGenerator { 

  private static Logger logger =Logger.getLogger(WsdlToXsdGenerator.class.getName()); 
  public static void wsdlToXSD(InputStream is , OutputStream os) { 
  DocumentBuilder builder; 
    try {
      builder = getDocBuilder(); 
      Document wsdlDoc = builder.parse(is); 
      Document xsdDoc = getDocBuilder().newDocument(); 
      populateXsdDoc(wsdlDoc, xsdDoc); 
      writeToStream(xsdDoc,os); 
      is.close(); 
      os.flush(); 
      os.close(); 
    } catch (Exception e) { 
      StringWriter sw = new StringWriter(); 
      e.printStackTrace(new PrintWriter(sw));
      logger.error(sw.toString()); 
    } 
} 

private static void populateXsdDoc(Document wsdlDoc, Document xsdDoc) { 

Element root = xsdDoc.createElement("xsd:schema"); 
root.setAttribute("xmlns:xsd", "http://www.w3.org/2001/XMLSchema"); 
xsdDoc.appendChild(root); 
Element element = wsdlDoc.getDocumentElement(); 
Node node = element.getElementsByTagName("wsdl:types").item(0); 
NodeList lst = node.getChildNodes(); 
for (int i = 0; i < lst.getLength(); i++) { 
Node nd = lst.item(i); 

  if(nd.getNodeName().equals("xsd:schema")){ 

    NodeList xsdNodes = nd.getChildNodes(); 
    for (int j = 0; j < xsdNodes.getLength(); j++) { 
      Node temp = xsdNodes.item(j); 
      Node toAdded = xsdDoc.importNode(temp, true); 
      root.appendChild(toAdded); 
    } 
    } 
    } 
  } 

  private static void writeToStream(Document document, OutputStream os) throws IOException { 
    DOMImplementationLS domImplementationLS = (DOMImplementationLS) 
    document.getImplementation(); 
    LSSerializer lsSerializer = domImplementationLS.createLSSerializer(); 
    String xsd = lsSerializer.writeToString(document); 
    PrintWriter pw = new PrintWriter(os); 
    // logger.debug(xsd); 
    pw.write(xsd); 
    pw.flush(); 
  } 
  private static DocumentBuilder getDocBuilder() throws ParserConfigurationException{ 
    DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance(); 
    DocumentBuilder builder = factory.newDocumentBuilder(); 
    return builder; 
  } 

  public static void main(String[] args) { 
    StringBuffer sb = new StringBuffer(); 
    WsdlToXsdGenerator.wsdlToXSD(new FileInputStream(new File("ts.wsdl")), new WriterOutputStream( new StringWriter(sb))); 
    System.out.println(sb.toString()); 
  } 
}
```

2. input

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?><definitions xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/" xmlns:ts="http://techsquids.com/ts/" xmlns:wsdl="http://schemas.xmlsoap.org/wsdl/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" name="ts" targetnamespace="http://techsquids.com/ts/">
<types>
<schema targetnamespace="http://techsquids.com/ts/" name="ts">
<!-- Request / response types -->
<element name="tsRequest">
<complextype>
<sequence>
<element name="year" type="ts:year"></element>
<element name="month" type="ts:month"></element>
</sequence>
</complextype>
</element>
<element name="tsResponse">
<complextype>
<sequence>
<element name="year" type="ts:year"></element>
<element name="month" type="ts:month"></element>
<element name="status" type="ts:response"></element>
<element name="output" type="xsd:string"></element>
</sequence>
</complextype>
</element>
<simpletype name="year">
<restriction base="xsd:int">
<minexclusive value="1970"></minexclusive>
<maxexclusive value="9999"></maxexclusive>
</restriction>
</simpletype>
<simpletype name="month">
<restriction base="xsd:int">
<mininclusive value="1"></mininclusive>
<maxinclusive value="12"></maxinclusive>
</restriction>
</simpletype>
<complextype name="response">
<sequence>
<element name="code" type="xsd:int"></element>
<element name="message" type="xsd:string"></element>
<element name="appCode">
<annotation>
</annotation>
<simpletype>
<restriction base="xsd:string">
<enumeration value="1"></enumeration>
<enumeration value="2"></enumeration>
<enumeration value="3"></enumeration>
<enumeration value="4"></enumeration>
<enumeration value="5"></enumeration>
<enumeration value="6"></enumeration>
</restriction>
</simpletype>
</element>
</sequence>
</complextype>
</schema>
</types>
<message name="getTSDataRequest">
<part element="ts:tsRequest" name="parameters"></part>
</message>
<message name="getTSDataResponse">
<part element="ts:tsResponse" name="parameters"></part>
</message>
<porttype name="TSDataService">
<operation name="getTSData">
<input message="ts:getTSDataRequest">
<output message="ts:getTSDataResponse"></output>
</operation>
</porttype>
<binding name="TSDataServiceSOAP" type="ts:TSDataService">
<binding style="document" transport="http://schemas.xmlsoap.org/soap/http"></binding>
<operation name="getTSData">
<operation soapaction="getTSData"></operation>
<input>
<output>
<body use="literal"></body>
</output>
</operation>
</binding>
<service name="TSDataService">
<port binding="ts:TSDataServiceSOAP" name="TSDataServiceSOAP">
<address location="https://techsquids.com/"></address>
</port>
</service>
</definitions>
```
3. output

```
<schema targetnamespace="http://techsquids.com/ts/" name="ts">
<!-- Request / response types -->
<element name="tsRequest">
<complextype>
<sequence>
<element name="year" type="ts:year"></element>
<element name="month" type="ts:month"></element>
</sequence>
</complextype>
</element>
<element name="tsResponse">
<complextype>
<sequence>
<element name="year" type="ts:year"></element>
<element name="month" type="ts:month"></element>
<element name="status" type="ts:response"></element>
<element name="output" type="xsd:string"></element>
</sequence>
</complextype>
</element>
<simpletype name="year">
<restriction base="xsd:int">
<minexclusive value="1970"></minexclusive>
<maxexclusive value="9999"></maxexclusive>
</restriction>
</simpletype>
<simpletype name="month">
<restriction base="xsd:int">
<mininclusive value="1"></mininclusive>
<maxinclusive value="12"></maxinclusive>
</restriction>
</simpletype>
<complextype name="response">
<sequence>
<element name="code" type="xsd:int"></element>
<element name="message" type="xsd:string"></element>
<element name="appCode">
<annotation>
</annotation>
<simpletype>
<restriction base="xsd:string">
<enumeration value="1"></enumeration>
<enumeration value="2"></enumeration>
<enumeration value="3"></enumeration>
<enumeration value="4"></enumeration>
<enumeration value="5"></enumeration>
<enumeration value="6"></enumeration>
</restriction>
</simpletype>
</element>
</sequence>
</complextype>
</schema>
```

complete source code with wsdl at [github](https://github.com/rahul86s/techsquids.git "techsquids") inside java-common project.

