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
  wp-syntax-cache-content: "a:3:{i:1;s:21643:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n9\n10\n11\n12\n13\n14\n15\n16\n17\n18\n19\n20\n21\n22\n23\n24\n25\n26\n27\n28\n29\n30\n31\n32\n33\n34\n35\n36\n37\n38\n39\n40\n41\n42\n43\n44\n45\n46\n47\n48\n49\n50\n51\n52\n53\n54\n55\n56\n57\n58\n59\n60\n61\n62\n63\n64\n65\n66\n67\n68\n69\n70\n71\n72\n73\n74\n75\n76\n77\n</pre></td><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\"><span style=\"color:
    #000000; font-weight: bold;\">package</span> <span style=\"color: #006699;\">com.ts.common.xsd</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">java.io.File</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">java.io.FileInputStream</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">java.io.IOException</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">java.io.InputStream</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">java.io.OutputStream</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">java.io.PrintWriter</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">java.io.StringWriter</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">java.util.logging.Logger</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">javax.xml.parsers.DocumentBuilder</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">javax.xml.parsers.DocumentBuilderFactory</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">javax.xml.parsers.ParserConfigurationException</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">org.apache.commons.io.output.WriterOutputStream</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">org.w3c.dom.Document</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">org.w3c.dom.Element</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">org.w3c.dom.Node</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">org.w3c.dom.NodeList</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">org.w3c.dom.ls.DOMImplementationLS</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">org.w3c.dom.ls.LSSerializer</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">public</span> <span style=\"color: #000000; font-weight: bold;\">class</span>
    WsdlToXsdGenerator <span style=\"color: #009900;\">&#123;</span>\n<span style=\"color:
    #000000; font-weight: bold;\">private</span> <span style=\"color: #000000; font-weight:
    bold;\">static</span> Logger logger <span style=\"color: #339933;\">=</span>Logger.<span
    style=\"color: #006633;\">getLogger</span><span style=\"color: #009900;\">&#40;</span>WsdlToXsdGenerator.<span
    style=\"color: #000000; font-weight: bold;\">class</span>.<span style=\"color:
    #006633;\">getName</span><span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n<span style=\"color: #000000; font-weight: bold;\">public</span>
    <span style=\"color: #000000; font-weight: bold;\">static</span> <span style=\"color:
    #000066; font-weight: bold;\">void</span> wsdlToXSD<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #003399;\">InputStream</span> is , <span style=\"color: #003399;\">OutputStream</span>
    os<span style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\nDocumentBuilder
    builder<span style=\"color: #339933;\">;</span>\n<span style=\"color: #000000;
    font-weight: bold;\">try</span> <span style=\"color: #009900;\">&#123;</span>\nbuilder
    <span style=\"color: #339933;\">=</span> getDocBuilder<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n<span
    style=\"color: #003399;\">Document</span> wsdlDoc <span style=\"color: #339933;\">=</span>
    builder.<span style=\"color: #006633;\">parse</span><span style=\"color: #009900;\">&#40;</span>is<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n<span
    style=\"color: #003399;\">Document</span> xsdDoc <span style=\"color: #339933;\">=</span>
    getDocBuilder<span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #009900;\">&#41;</span>.<span style=\"color: #006633;\">newDocument</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\npopulateXsdDoc<span style=\"color: #009900;\">&#40;</span>wsdlDoc,
    xsdDoc<span style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\nwriteToStream<span
    style=\"color: #009900;\">&#40;</span>xsdDoc,os<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\nis.<span style=\"color: #006633;\">close</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\nos.<span style=\"color: #006633;\">flush</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\nos.<span style=\"color: #006633;\">close</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #009900;\">&#125;</span>
    <span style=\"color: #000000; font-weight: bold;\">catch</span> <span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #003399;\">Exception</span> e<span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n<span
    style=\"color: #003399;\">StringWriter</span> sw <span style=\"color: #339933;\">=</span>
    <span style=\"color: #000000; font-weight: bold;\">new</span> <span style=\"color:
    #003399;\">StringWriter</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\ne.<span
    style=\"color: #006633;\">printStackTrace</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #000000; font-weight: bold;\">new</span> <span style=\"color: #003399;\">PrintWriter</span><span
    style=\"color: #009900;\">&#40;</span>sw<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\nlogger.<span
    style=\"color: #006633;\">error</span><span style=\"color: #009900;\">&#40;</span>sw.<span
    style=\"color: #006633;\">toString</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #009900;\">&#125;</span>\n<span
    style=\"color: #009900;\">&#125;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">private</span> <span style=\"color: #000000; font-weight: bold;\">static</span>
    <span style=\"color: #000066; font-weight: bold;\">void</span> populateXsdDoc<span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #003399;\">Document</span>
    wsdlDoc, <span style=\"color: #003399;\">Document</span> xsdDoc<span style=\"color:
    #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n<span style=\"color:
    #003399;\">Element</span> root <span style=\"color: #339933;\">=</span> xsdDoc.<span
    style=\"color: #006633;\">createElement</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;xsd:schema&quot;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\nroot.<span style=\"color: #006633;\">setAttribute</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #0000ff;\">&quot;xmlns:xsd&quot;</span>,
    <span style=\"color: #0000ff;\">&quot;http://www.w3.org/2001/XMLSchema&quot;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\nxsdDoc.<span
    style=\"color: #006633;\">appendChild</span><span style=\"color: #009900;\">&#40;</span>root<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n<span
    style=\"color: #003399;\">Element</span> element <span style=\"color: #339933;\">=</span>
    wsdlDoc.<span style=\"color: #006633;\">getDocumentElement</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\nNode node <span style=\"color: #339933;\">=</span> element.<span
    style=\"color: #006633;\">getElementsByTagName</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;wsdl:types&quot;</span><span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">item</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #cc66cc;\">0</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\nNodeList lst <span style=\"color: #339933;\">=</span>
    node.<span style=\"color: #006633;\">getChildNodes</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n<span style=\"color: #000000; font-weight: bold;\">for</span>
    <span style=\"color: #009900;\">&#40;</span><span style=\"color: #000066; font-weight:
    bold;\">int</span> i <span style=\"color: #339933;\">=</span> <span style=\"color:
    #cc66cc;\">0</span><span style=\"color: #339933;\">;</span> i <span style=\"color:
    #339933;\">&lt;</span> lst.<span style=\"color: #006633;\">getLength</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span> i<span style=\"color: #339933;\">++</span><span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\nNode
    nd <span style=\"color: #339933;\">=</span> lst.<span style=\"color: #006633;\">item</span><span
    style=\"color: #009900;\">&#40;</span>i<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">if</span><span style=\"color: #009900;\">&#40;</span>nd.<span style=\"color:
    #006633;\">getNodeName</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span>.<span style=\"color: #006633;\">equals</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #0000ff;\">&quot;xsd:schema&quot;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#123;</span>\nNodeList xsdNodes <span style=\"color:
    #339933;\">=</span> nd.<span style=\"color: #006633;\">getChildNodes</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">for</span> <span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #000066; font-weight: bold;\">int</span> j <span style=\"color: #339933;\">=</span>
    <span style=\"color: #cc66cc;\">0</span><span style=\"color: #339933;\">;</span>
    j <span style=\"color: #339933;\">&lt;</span> xsdNodes.<span style=\"color: #006633;\">getLength</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span> j<span style=\"color: #339933;\">++</span><span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\nNode
    temp <span style=\"color: #339933;\">=</span> xsdNodes.<span style=\"color: #006633;\">item</span><span
    style=\"color: #009900;\">&#40;</span>j<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\nNode toAdded <span style=\"color: #339933;\">=</span>
    xsdDoc.<span style=\"color: #006633;\">importNode</span><span style=\"color: #009900;\">&#40;</span>temp,
    <span style=\"color: #000066; font-weight: bold;\">true</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\nroot.<span style=\"color:
    #006633;\">appendChild</span><span style=\"color: #009900;\">&#40;</span>toAdded<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n<span
    style=\"color: #009900;\">&#125;</span>\n<span style=\"color: #009900;\">&#125;</span>\n<span
    style=\"color: #009900;\">&#125;</span>\n<span style=\"color: #009900;\">&#125;</span>\n<span
    style=\"color: #000000; font-weight: bold;\">private</span> <span style=\"color:
    #000000; font-weight: bold;\">static</span> <span style=\"color: #000066; font-weight:
    bold;\">void</span> writeToStream<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #003399;\">Document</span> document, <span style=\"color: #003399;\">OutputStream</span>
    os<span style=\"color: #009900;\">&#41;</span> <span style=\"color: #000000; font-weight:
    bold;\">throws</span> <span style=\"color: #003399;\">IOException</span> <span
    style=\"color: #009900;\">&#123;</span>\nDOMImplementationLS domImplementationLS
    <span style=\"color: #339933;\">=</span> <span style=\"color: #009900;\">&#40;</span>DOMImplementationLS<span
    style=\"color: #009900;\">&#41;</span> document.<span style=\"color: #006633;\">getImplementation</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\nLSSerializer lsSerializer <span style=\"color:
    #339933;\">=</span> domImplementationLS.<span style=\"color: #006633;\">createLSSerializer</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #003399;\">String</span>
    xsd <span style=\"color: #339933;\">=</span> lsSerializer.<span style=\"color:
    #006633;\">writeToString</span><span style=\"color: #009900;\">&#40;</span>document<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n<span
    style=\"color: #003399;\">PrintWriter</span> pw <span style=\"color: #339933;\">=</span>
    <span style=\"color: #000000; font-weight: bold;\">new</span> <span style=\"color:
    #003399;\">PrintWriter</span><span style=\"color: #009900;\">&#40;</span>os<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n<span
    style=\"color: #666666; font-style: italic;\">// logger.debug(xsd);</span>\npw.<span
    style=\"color: #006633;\">write</span><span style=\"color: #009900;\">&#40;</span>xsd<span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\npw.<span
    style=\"color: #006633;\">flush</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n<span
    style=\"color: #009900;\">&#125;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">private</span> <span style=\"color: #000000; font-weight: bold;\">static</span>
    DocumentBuilder getDocBuilder<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #000000; font-weight:
    bold;\">throws</span> ParserConfigurationException<span style=\"color: #009900;\">&#123;</span>\nDocumentBuilderFactory
    factory <span style=\"color: #339933;\">=</span> DocumentBuilderFactory.<span
    style=\"color: #006633;\">newInstance</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\nDocumentBuilder
    builder <span style=\"color: #339933;\">=</span> factory.<span style=\"color:
    #006633;\">newDocumentBuilder</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n<span
    style=\"color: #000000; font-weight: bold;\">return</span> builder<span style=\"color:
    #339933;\">;</span>\n<span style=\"color: #009900;\">&#125;</span>\n<span style=\"color:
    #000000; font-weight: bold;\">public</span> <span style=\"color: #000000; font-weight:
    bold;\">static</span> <span style=\"color: #000066; font-weight: bold;\">void</span>
    main<span style=\"color: #009900;\">&#40;</span><span style=\"color: #003399;\">String</span><span
    style=\"color: #009900;\">&#91;</span><span style=\"color: #009900;\">&#93;</span>
    args<span style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n<span
    style=\"color: #003399;\">StringBuffer</span> sb <span style=\"color: #339933;\">=</span>
    <span style=\"color: #000000; font-weight: bold;\">new</span> <span style=\"color:
    #003399;\">StringBuffer</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\nWsdlToXsdGenerator.<span
    style=\"color: #006633;\">wsdlToXSD</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #000000; font-weight: bold;\">new</span> <span style=\"color: #003399;\">FileInputStream</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #000000; font-weight:
    bold;\">new</span> <span style=\"color: #003399;\">File</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #0000ff;\">&quot;ts.wsdl&quot;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span>,
    <span style=\"color: #000000; font-weight: bold;\">new</span> WriterOutputStream<span
    style=\"color: #009900;\">&#40;</span> <span style=\"color: #000000; font-weight:
    bold;\">new</span> <span style=\"color: #003399;\">StringWriter</span><span style=\"color:
    #009900;\">&#40;</span>sb<span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n<span style=\"color: #003399;\">System</span>.<span style=\"color:
    #006633;\">out</span>.<span style=\"color: #006633;\">println</span><span style=\"color:
    #009900;\">&#40;</span>sb.<span style=\"color: #006633;\">toString</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n<span
    style=\"color: #009900;\">&#125;</span>\n<span style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">package com.ts.common.xsd;\r\nimport
    java.io.File;\r\nimport java.io.FileInputStream;\r\nimport java.io.IOException;\r\nimport
    java.io.InputStream;\r\nimport java.io.OutputStream;\r\nimport java.io.PrintWriter;\r\nimport
    java.io.StringWriter;\r\nimport java.util.logging.Logger;\r\nimport javax.xml.parsers.DocumentBuilder;\r\nimport
    javax.xml.parsers.DocumentBuilderFactory;\r\nimport javax.xml.parsers.ParserConfigurationException;\r\nimport
    org.apache.commons.io.output.WriterOutputStream;\r\nimport org.w3c.dom.Document;\r\nimport
    org.w3c.dom.Element;\r\nimport org.w3c.dom.Node;\r\nimport org.w3c.dom.NodeList;\r\nimport
    org.w3c.dom.ls.DOMImplementationLS;\r\nimport org.w3c.dom.ls.LSSerializer;\r\npublic
    class WsdlToXsdGenerator {\r\nprivate static Logger logger =Logger.getLogger(WsdlToXsdGenerator.class.getName());\r\npublic
    static void wsdlToXSD(InputStream is , OutputStream os) {\r\nDocumentBuilder builder;\r\ntry
    {\r\nbuilder = getDocBuilder();\r\nDocument wsdlDoc = builder.parse(is);\r\nDocument
    xsdDoc = getDocBuilder().newDocument();\r\npopulateXsdDoc(wsdlDoc, xsdDoc);\r\nwriteToStream(xsdDoc,os);\r\nis.close();\r\nos.flush();\r\nos.close();\r\n}
    catch (Exception e) {\r\nStringWriter sw = new StringWriter();\r\ne.printStackTrace(new
    PrintWriter(sw));\r\nlogger.error(sw.toString());\r\n}\r\n}\r\nprivate static
    void populateXsdDoc(Document wsdlDoc, Document xsdDoc) {\r\nElement root = xsdDoc.createElement(&quot;xsd:schema&quot;);\r\nroot.setAttribute(&quot;xmlns:xsd&quot;,
    &quot;http://www.w3.org/2001/XMLSchema&quot;);\r\nxsdDoc.appendChild(root);\r\nElement
    element = wsdlDoc.getDocumentElement();\r\nNode node = element.getElementsByTagName(&quot;wsdl:types&quot;).item(0);\r\nNodeList
    lst = node.getChildNodes();\r\nfor (int i = 0; i &lt; lst.getLength(); i++) {\r\nNode
    nd = lst.item(i);\r\nif(nd.getNodeName().equals(&quot;xsd:schema&quot;)){\r\nNodeList
    xsdNodes = nd.getChildNodes();\r\nfor (int j = 0; j &lt; xsdNodes.getLength();
    j++) {\r\nNode temp = xsdNodes.item(j);\r\nNode toAdded = xsdDoc.importNode(temp,
    true);\r\nroot.appendChild(toAdded);\r\n}\r\n}\r\n}\r\n}\r\nprivate static void
    writeToStream(Document document, OutputStream os) throws IOException {\r\nDOMImplementationLS
    domImplementationLS = (DOMImplementationLS) document.getImplementation();\r\nLSSerializer
    lsSerializer = domImplementationLS.createLSSerializer();\r\nString xsd = lsSerializer.writeToString(document);\r\nPrintWriter
    pw = new PrintWriter(os);\r\n// logger.debug(xsd);\r\npw.write(xsd);\r\npw.flush();\r\n}\r\nprivate
    static DocumentBuilder getDocBuilder() throws ParserConfigurationException{\r\nDocumentBuilderFactory
    factory = DocumentBuilderFactory.newInstance();\r\nDocumentBuilder builder = factory.newDocumentBuilder();\r\nreturn
    builder;\r\n}\r\npublic static void main(String[] args) {\r\nStringBuffer sb =
    new StringBuffer();\r\nWsdlToXsdGenerator.wsdlToXSD(new FileInputStream(new File(&quot;ts.wsdl&quot;)),
    new WriterOutputStream( new StringWriter(sb)));\r\nSystem.out.println(sb.toString());\r\n}\r\n}</p></div>\n\";i:2;s:29239:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n9\n10\n11\n12\n13\n14\n15\n16\n17\n18\n19\n20\n21\n22\n23\n24\n25\n26\n27\n28\n29\n30\n31\n32\n33\n34\n35\n36\n37\n38\n39\n40\n41\n42\n43\n44\n45\n46\n47\n48\n49\n50\n51\n52\n53\n54\n55\n56\n57\n58\n59\n60\n61\n62\n63\n64\n65\n66\n67\n68\n69\n70\n71\n72\n73\n74\n75\n76\n77\n78\n79\n80\n81\n82\n83\n84\n85\n86\n87\n</pre></td><td
    class=\"code\"><pre class=\"xml\" style=\"font-family:monospace;\"><span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;?xml</span>
    <span style=\"color: #000066;\">version</span>=<span style=\"color: #ff0000;\">&quot;1.0&quot;</span>
    <span style=\"color: #000066;\">encoding</span>=<span style=\"color: #ff0000;\">&quot;UTF-8&quot;</span>
    <span style=\"color: #000066;\">standalone</span>=<span style=\"color: #ff0000;\">&quot;no&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">?&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;wsdl:definitions</span>
    <span style=\"color: #000066;\">xmlns:soap</span>=<span style=\"color: #ff0000;\">&quot;http://schemas.xmlsoap.org/wsdl/soap/&quot;</span>
    <span style=\"color: #000066;\">xmlns:ts</span>=<span style=\"color: #ff0000;\">&quot;http://techsquids.com/ts/&quot;</span>
    <span style=\"color: #000066;\">xmlns:wsdl</span>=<span style=\"color: #ff0000;\">&quot;http://schemas.xmlsoap.org/wsdl/&quot;</span>
    <span style=\"color: #000066;\">xmlns:xsd</span>=<span style=\"color: #ff0000;\">&quot;http://www.w3.org/2001/XMLSchema&quot;</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;ts&quot;</span>
    <span style=\"color: #000066;\">targetNamespace</span>=<span style=\"color: #ff0000;\">&quot;http://techsquids.com/ts/&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;wsdl:types<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:schema</span>
    <span style=\"color: #000066;\">targetNamespace</span>=<span style=\"color: #ff0000;\">&quot;http://techsquids.com/ts/&quot;</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;ts&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #808080; font-style: italic;\">&lt;!-- Request / response types --&gt;</span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:element</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;tsRequest&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:complexType<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:sequence<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:element</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;year&quot;</span>
    <span style=\"color: #000066;\">type</span>=<span style=\"color: #ff0000;\">&quot;ts:year&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:element<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:element</span> <span style=\"color: #000066;\">name</span>=<span
    style=\"color: #ff0000;\">&quot;month&quot;</span> <span style=\"color: #000066;\">type</span>=<span
    style=\"color: #ff0000;\">&quot;ts:month&quot;</span><span style=\"color: #000000;
    font-weight: bold;\">&gt;</span><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:element<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:sequence<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:complexType<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:element<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:element</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;tsResponse&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:complexType<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:sequence<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:element</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;year&quot;</span>
    <span style=\"color: #000066;\">type</span>=<span style=\"color: #ff0000;\">&quot;ts:year&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:element<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:element</span> <span style=\"color: #000066;\">name</span>=<span
    style=\"color: #ff0000;\">&quot;month&quot;</span> <span style=\"color: #000066;\">type</span>=<span
    style=\"color: #ff0000;\">&quot;ts:month&quot;</span><span style=\"color: #000000;
    font-weight: bold;\">&gt;</span><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:element<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:element</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;status&quot;</span>
    <span style=\"color: #000066;\">type</span>=<span style=\"color: #ff0000;\">&quot;ts:response&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:element<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:element</span> <span style=\"color: #000066;\">name</span>=<span
    style=\"color: #ff0000;\">&quot;output&quot;</span> <span style=\"color: #000066;\">type</span>=<span
    style=\"color: #ff0000;\">&quot;xsd:string&quot;</span><span style=\"color: #000000;
    font-weight: bold;\">&gt;</span><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:element<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:sequence<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:complexType<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:element<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:simpleType</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;year&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:restriction</span>
    <span style=\"color: #000066;\">base</span>=<span style=\"color: #ff0000;\">&quot;xsd:int&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:minExclusive</span>
    <span style=\"color: #000066;\">value</span>=<span style=\"color: #ff0000;\">&quot;1970&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:minExclusive<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:maxExclusive</span> <span style=\"color:
    #000066;\">value</span>=<span style=\"color: #ff0000;\">&quot;9999&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:maxExclusive<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;/xsd:restriction<span style=\"color: #000000;
    font-weight: bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span
    style=\"color: #000000; font-weight: bold;\">&lt;/xsd:simpleType<span style=\"color:
    #000000; font-weight: bold;\">&gt;</span></span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:simpleType</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;month&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:restriction</span>
    <span style=\"color: #000066;\">base</span>=<span style=\"color: #ff0000;\">&quot;xsd:int&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:minInclusive</span>
    <span style=\"color: #000066;\">value</span>=<span style=\"color: #ff0000;\">&quot;1&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:minInclusive<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:maxInclusive</span> <span style=\"color:
    #000066;\">value</span>=<span style=\"color: #ff0000;\">&quot;12&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:maxInclusive<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;/xsd:restriction<span style=\"color: #000000;
    font-weight: bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span
    style=\"color: #000000; font-weight: bold;\">&lt;/xsd:simpleType<span style=\"color:
    #000000; font-weight: bold;\">&gt;</span></span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:complexType</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;response&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:sequence<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:element</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;code&quot;</span>
    <span style=\"color: #000066;\">type</span>=<span style=\"color: #ff0000;\">&quot;xsd:int&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:element<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:element</span> <span style=\"color: #000066;\">name</span>=<span
    style=\"color: #ff0000;\">&quot;message&quot;</span> <span style=\"color: #000066;\">type</span>=<span
    style=\"color: #ff0000;\">&quot;xsd:string&quot;</span><span style=\"color: #000000;
    font-weight: bold;\">&gt;</span><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:element<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:element</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;appCode&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:annotation<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:annotation<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:simpleType<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:restriction</span>
    <span style=\"color: #000066;\">base</span>=<span style=\"color: #ff0000;\">&quot;xsd:string&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:enumeration</span>
    <span style=\"color: #000066;\">value</span>=<span style=\"color: #ff0000;\">&quot;1&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:enumeration<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:enumeration</span> <span style=\"color:
    #000066;\">value</span>=<span style=\"color: #ff0000;\">&quot;2&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:enumeration<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:enumeration</span> <span style=\"color:
    #000066;\">value</span>=<span style=\"color: #ff0000;\">&quot;3&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:enumeration<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:enumeration</span> <span style=\"color:
    #000066;\">value</span>=<span style=\"color: #ff0000;\">&quot;4&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:enumeration<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:enumeration</span> <span style=\"color:
    #000066;\">value</span>=<span style=\"color: #ff0000;\">&quot;5&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:enumeration<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:enumeration</span> <span style=\"color:
    #000066;\">value</span>=<span style=\"color: #ff0000;\">&quot;6&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:enumeration<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;/xsd:restriction<span style=\"color: #000000;
    font-weight: bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span
    style=\"color: #000000; font-weight: bold;\">&lt;/xsd:simpleType<span style=\"color:
    #000000; font-weight: bold;\">&gt;</span></span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:element<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:sequence<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:complexType<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:schema<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/wsdl:types<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;wsdl:message</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;getTSDataRequest&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;wsdl:part</span>
    <span style=\"color: #000066;\">element</span>=<span style=\"color: #ff0000;\">&quot;ts:tsRequest&quot;</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;parameters&quot;</span>
    <span style=\"color: #000000; font-weight: bold;\">/&gt;</span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/wsdl:message<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;wsdl:message</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;getTSDataResponse&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;wsdl:part</span>
    <span style=\"color: #000066;\">element</span>=<span style=\"color: #ff0000;\">&quot;ts:tsResponse&quot;</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;parameters&quot;</span>
    <span style=\"color: #000000; font-weight: bold;\">/&gt;</span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/wsdl:message<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;wsdl:portType</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;TSDataService&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;wsdl:operation</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;getTSData&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;wsdl:input</span>
    <span style=\"color: #000066;\">message</span>=<span style=\"color: #ff0000;\">&quot;ts:getTSDataRequest&quot;</span>
    <span style=\"color: #000000; font-weight: bold;\">/&gt;</span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;wsdl:output</span>
    <span style=\"color: #000066;\">message</span>=<span style=\"color: #ff0000;\">&quot;ts:getTSDataResponse&quot;</span>
    <span style=\"color: #000000; font-weight: bold;\">/&gt;</span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/wsdl:operation<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/wsdl:portType<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;wsdl:binding</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;TSDataServiceSOAP&quot;</span>
    <span style=\"color: #000066;\">type</span>=<span style=\"color: #ff0000;\">&quot;ts:TSDataService&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;soap:binding</span>
    <span style=\"color: #000066;\">style</span>=<span style=\"color: #ff0000;\">&quot;document&quot;</span>
    <span style=\"color: #000066;\">transport</span>=<span style=\"color: #ff0000;\">&quot;http://schemas.xmlsoap.org/soap/http&quot;</span>
    <span style=\"color: #000000; font-weight: bold;\">/&gt;</span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;wsdl:operation</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;getTSData&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;soap:operation</span>
    <span style=\"color: #000066;\">soapAction</span>=<span style=\"color: #ff0000;\">&quot;getTSData&quot;</span>
    <span style=\"color: #000000; font-weight: bold;\">/&gt;</span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;wsdl:input<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;soap:body</span>
    <span style=\"color: #000066;\">use</span>=<span style=\"color: #ff0000;\">&quot;literal&quot;</span>
    <span style=\"color: #000000; font-weight: bold;\">/&gt;</span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/wsdl:input<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;wsdl:output<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;soap:body</span>
    <span style=\"color: #000066;\">use</span>=<span style=\"color: #ff0000;\">&quot;literal&quot;</span>
    <span style=\"color: #000000; font-weight: bold;\">/&gt;</span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/wsdl:output<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/wsdl:operation<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/wsdl:binding<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;wsdl:service</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;TSDataService&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;wsdl:port</span>
    <span style=\"color: #000066;\">binding</span>=<span style=\"color: #ff0000;\">&quot;ts:TSDataServiceSOAP&quot;</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;TSDataServiceSOAP&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;soap:address</span>
    <span style=\"color: #000066;\">location</span>=<span style=\"color: #ff0000;\">&quot;https://techsquids.com/&quot;</span>
    <span style=\"color: #000000; font-weight: bold;\">/&gt;</span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/wsdl:port<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/wsdl:service<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/wsdl:definitions<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\">&lt;?xml version=&quot;1.0&quot; encoding=&quot;UTF-8&quot;
    standalone=&quot;no&quot;?&gt;\r\n&lt;wsdl:definitions xmlns:soap=&quot;http://schemas.xmlsoap.org/wsdl/soap/&quot;
    xmlns:ts=&quot;http://techsquids.com/ts/&quot; xmlns:wsdl=&quot;http://schemas.xmlsoap.org/wsdl/&quot;
    xmlns:xsd=&quot;http://www.w3.org/2001/XMLSchema&quot; name=&quot;ts&quot; targetNamespace=&quot;http://techsquids.com/ts/&quot;&gt;\r\n&lt;wsdl:types&gt;\r\n&lt;xsd:schema
    targetNamespace=&quot;http://techsquids.com/ts/&quot; name=&quot;ts&quot;&gt;\r\n&lt;!--
    Request / response types --&gt;\r\n&lt;xsd:element name=&quot;tsRequest&quot;&gt;\r\n&lt;xsd:complexType&gt;\r\n&lt;xsd:sequence&gt;\r\n&lt;xsd:element
    name=&quot;year&quot; type=&quot;ts:year&quot;&gt;&lt;/xsd:element&gt;\r\n&lt;xsd:element
    name=&quot;month&quot; type=&quot;ts:month&quot;&gt;&lt;/xsd:element&gt;\r\n&lt;/xsd:sequence&gt;\r\n&lt;/xsd:complexType&gt;\r\n&lt;/xsd:element&gt;\r\n&lt;xsd:element
    name=&quot;tsResponse&quot;&gt;\r\n&lt;xsd:complexType&gt;\r\n&lt;xsd:sequence&gt;\r\n&lt;xsd:element
    name=&quot;year&quot; type=&quot;ts:year&quot;&gt;&lt;/xsd:element&gt;\r\n&lt;xsd:element
    name=&quot;month&quot; type=&quot;ts:month&quot;&gt;&lt;/xsd:element&gt;\r\n&lt;xsd:element
    name=&quot;status&quot; type=&quot;ts:response&quot;&gt;&lt;/xsd:element&gt;\r\n&lt;xsd:element
    name=&quot;output&quot; type=&quot;xsd:string&quot;&gt;&lt;/xsd:element&gt;\r\n&lt;/xsd:sequence&gt;\r\n&lt;/xsd:complexType&gt;\r\n&lt;/xsd:element&gt;\r\n&lt;xsd:simpleType
    name=&quot;year&quot;&gt;\r\n&lt;xsd:restriction base=&quot;xsd:int&quot;&gt;\r\n&lt;xsd:minExclusive
    value=&quot;1970&quot;&gt;&lt;/xsd:minExclusive&gt;\r\n&lt;xsd:maxExclusive value=&quot;9999&quot;&gt;&lt;/xsd:maxExclusive&gt;\r\n&lt;/xsd:restriction&gt;\r\n&lt;/xsd:simpleType&gt;\r\n&lt;xsd:simpleType
    name=&quot;month&quot;&gt;\r\n&lt;xsd:restriction base=&quot;xsd:int&quot;&gt;\r\n&lt;xsd:minInclusive
    value=&quot;1&quot;&gt;&lt;/xsd:minInclusive&gt;\r\n&lt;xsd:maxInclusive value=&quot;12&quot;&gt;&lt;/xsd:maxInclusive&gt;\r\n&lt;/xsd:restriction&gt;\r\n&lt;/xsd:simpleType&gt;\r\n&lt;xsd:complexType
    name=&quot;response&quot;&gt;\r\n&lt;xsd:sequence&gt;\r\n&lt;xsd:element name=&quot;code&quot;
    type=&quot;xsd:int&quot;&gt;&lt;/xsd:element&gt;\r\n&lt;xsd:element name=&quot;message&quot;
    type=&quot;xsd:string&quot;&gt;&lt;/xsd:element&gt;\r\n&lt;xsd:element name=&quot;appCode&quot;&gt;\r\n&lt;xsd:annotation&gt;\r\n&lt;/xsd:annotation&gt;\r\n&lt;xsd:simpleType&gt;\r\n&lt;xsd:restriction
    base=&quot;xsd:string&quot;&gt;\r\n&lt;xsd:enumeration value=&quot;1&quot;&gt;&lt;/xsd:enumeration&gt;\r\n&lt;xsd:enumeration
    value=&quot;2&quot;&gt;&lt;/xsd:enumeration&gt;\r\n&lt;xsd:enumeration value=&quot;3&quot;&gt;&lt;/xsd:enumeration&gt;\r\n&lt;xsd:enumeration
    value=&quot;4&quot;&gt;&lt;/xsd:enumeration&gt;\r\n&lt;xsd:enumeration value=&quot;5&quot;&gt;&lt;/xsd:enumeration&gt;\r\n&lt;xsd:enumeration
    value=&quot;6&quot;&gt;&lt;/xsd:enumeration&gt;\r\n&lt;/xsd:restriction&gt;\r\n&lt;/xsd:simpleType&gt;\r\n&lt;/xsd:element&gt;\r\n&lt;/xsd:sequence&gt;\r\n&lt;/xsd:complexType&gt;\r\n&lt;/xsd:schema&gt;\r\n&lt;/wsdl:types&gt;\r\n&lt;wsdl:message
    name=&quot;getTSDataRequest&quot;&gt;\r\n&lt;wsdl:part element=&quot;ts:tsRequest&quot;
    name=&quot;parameters&quot; /&gt;\r\n&lt;/wsdl:message&gt;\r\n&lt;wsdl:message
    name=&quot;getTSDataResponse&quot;&gt;\r\n&lt;wsdl:part element=&quot;ts:tsResponse&quot;
    name=&quot;parameters&quot; /&gt;\r\n&lt;/wsdl:message&gt;\r\n&lt;wsdl:portType
    name=&quot;TSDataService&quot;&gt;\r\n&lt;wsdl:operation name=&quot;getTSData&quot;&gt;\r\n&lt;wsdl:input
    message=&quot;ts:getTSDataRequest&quot; /&gt;\r\n&lt;wsdl:output message=&quot;ts:getTSDataResponse&quot;
    /&gt;\r\n&lt;/wsdl:operation&gt;\r\n&lt;/wsdl:portType&gt;\r\n&lt;wsdl:binding
    name=&quot;TSDataServiceSOAP&quot; type=&quot;ts:TSDataService&quot;&gt;\r\n&lt;soap:binding
    style=&quot;document&quot; transport=&quot;http://schemas.xmlsoap.org/soap/http&quot;
    /&gt;\r\n&lt;wsdl:operation name=&quot;getTSData&quot;&gt;\r\n&lt;soap:operation
    soapAction=&quot;getTSData&quot; /&gt;\r\n&lt;wsdl:input&gt;\r\n&lt;soap:body
    use=&quot;literal&quot; /&gt;\r\n&lt;/wsdl:input&gt;\r\n&lt;wsdl:output&gt;\r\n&lt;soap:body
    use=&quot;literal&quot; /&gt;\r\n&lt;/wsdl:output&gt;\r\n&lt;/wsdl:operation&gt;\r\n&lt;/wsdl:binding&gt;\r\n&lt;wsdl:service
    name=&quot;TSDataService&quot;&gt;\r\n&lt;wsdl:port binding=&quot;ts:TSDataServiceSOAP&quot;
    name=&quot;TSDataServiceSOAP&quot;&gt;\r\n&lt;soap:address location=&quot;https://techsquids.com/&quot;
    /&gt;\r\n&lt;/wsdl:port&gt;\r\n&lt;/wsdl:service&gt;\r\n&lt;/wsdl:definitions&gt;</p></div>\n\";i:3;s:18061:\"\n<div
    class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td class=\"line_numbers\"><pre>1\n2\n3\n4\n5\n6\n7\n8\n9\n10\n11\n12\n13\n14\n15\n16\n17\n18\n19\n20\n21\n22\n23\n24\n25\n26\n27\n28\n29\n30\n31\n32\n33\n34\n35\n36\n37\n38\n39\n40\n41\n42\n43\n44\n45\n46\n47\n48\n49\n50\n51\n52\n53\n</pre></td><td
    class=\"code\"><pre class=\"xml\" style=\"font-family:monospace;\"> <span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:schema</span>
    <span style=\"color: #000066;\">targetNamespace</span>=<span style=\"color: #ff0000;\">&quot;http://techsquids.com/ts/&quot;</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;ts&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #808080; font-style: italic;\">&lt;!-- Request / response types --&gt;</span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:element</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;tsRequest&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:complexType<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:sequence<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:element</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;year&quot;</span>
    <span style=\"color: #000066;\">type</span>=<span style=\"color: #ff0000;\">&quot;ts:year&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:element<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:element</span> <span style=\"color: #000066;\">name</span>=<span
    style=\"color: #ff0000;\">&quot;month&quot;</span> <span style=\"color: #000066;\">type</span>=<span
    style=\"color: #ff0000;\">&quot;ts:month&quot;</span><span style=\"color: #000000;
    font-weight: bold;\">&gt;</span><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:element<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:sequence<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:complexType<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:element<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:element</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;tsResponse&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:complexType<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:sequence<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:element</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;year&quot;</span>
    <span style=\"color: #000066;\">type</span>=<span style=\"color: #ff0000;\">&quot;ts:year&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:element<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:element</span> <span style=\"color: #000066;\">name</span>=<span
    style=\"color: #ff0000;\">&quot;month&quot;</span> <span style=\"color: #000066;\">type</span>=<span
    style=\"color: #ff0000;\">&quot;ts:month&quot;</span><span style=\"color: #000000;
    font-weight: bold;\">&gt;</span><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:element<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:element</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;status&quot;</span>
    <span style=\"color: #000066;\">type</span>=<span style=\"color: #ff0000;\">&quot;ts:response&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:element<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:element</span> <span style=\"color: #000066;\">name</span>=<span
    style=\"color: #ff0000;\">&quot;output&quot;</span> <span style=\"color: #000066;\">type</span>=<span
    style=\"color: #ff0000;\">&quot;xsd:string&quot;</span><span style=\"color: #000000;
    font-weight: bold;\">&gt;</span><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:element<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:sequence<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:complexType<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:element<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:simpleType</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;year&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:restriction</span>
    <span style=\"color: #000066;\">base</span>=<span style=\"color: #ff0000;\">&quot;xsd:int&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:minExclusive</span>
    <span style=\"color: #000066;\">value</span>=<span style=\"color: #ff0000;\">&quot;1970&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:minExclusive<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:maxExclusive</span> <span style=\"color:
    #000066;\">value</span>=<span style=\"color: #ff0000;\">&quot;9999&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:maxExclusive<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;/xsd:restriction<span style=\"color: #000000;
    font-weight: bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span
    style=\"color: #000000; font-weight: bold;\">&lt;/xsd:simpleType<span style=\"color:
    #000000; font-weight: bold;\">&gt;</span></span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:simpleType</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;month&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:restriction</span>
    <span style=\"color: #000066;\">base</span>=<span style=\"color: #ff0000;\">&quot;xsd:int&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:minInclusive</span>
    <span style=\"color: #000066;\">value</span>=<span style=\"color: #ff0000;\">&quot;1&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:minInclusive<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:maxInclusive</span> <span style=\"color:
    #000066;\">value</span>=<span style=\"color: #ff0000;\">&quot;12&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:maxInclusive<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;/xsd:restriction<span style=\"color: #000000;
    font-weight: bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span
    style=\"color: #000000; font-weight: bold;\">&lt;/xsd:simpleType<span style=\"color:
    #000000; font-weight: bold;\">&gt;</span></span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:complexType</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;response&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:sequence<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:element</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;code&quot;</span>
    <span style=\"color: #000066;\">type</span>=<span style=\"color: #ff0000;\">&quot;xsd:int&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:element<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:element</span> <span style=\"color: #000066;\">name</span>=<span
    style=\"color: #ff0000;\">&quot;message&quot;</span> <span style=\"color: #000066;\">type</span>=<span
    style=\"color: #ff0000;\">&quot;xsd:string&quot;</span><span style=\"color: #000000;
    font-weight: bold;\">&gt;</span><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:element<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:element</span>
    <span style=\"color: #000066;\">name</span>=<span style=\"color: #ff0000;\">&quot;appCode&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:annotation<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:annotation<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:simpleType<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:restriction</span>
    <span style=\"color: #000066;\">base</span>=<span style=\"color: #ff0000;\">&quot;xsd:string&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;xsd:enumeration</span>
    <span style=\"color: #000066;\">value</span>=<span style=\"color: #ff0000;\">&quot;1&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:enumeration<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:enumeration</span> <span style=\"color:
    #000066;\">value</span>=<span style=\"color: #ff0000;\">&quot;2&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:enumeration<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:enumeration</span> <span style=\"color:
    #000066;\">value</span>=<span style=\"color: #ff0000;\">&quot;3&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:enumeration<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:enumeration</span> <span style=\"color:
    #000066;\">value</span>=<span style=\"color: #ff0000;\">&quot;4&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:enumeration<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:enumeration</span> <span style=\"color:
    #000066;\">value</span>=<span style=\"color: #ff0000;\">&quot;5&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:enumeration<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;xsd:enumeration</span> <span style=\"color:
    #000066;\">value</span>=<span style=\"color: #ff0000;\">&quot;6&quot;</span><span
    style=\"color: #000000; font-weight: bold;\">&gt;</span><span style=\"color: #000000;
    font-weight: bold;\">&lt;/xsd:enumeration<span style=\"color: #000000; font-weight:
    bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span style=\"color:
    #000000; font-weight: bold;\">&lt;/xsd:restriction<span style=\"color: #000000;
    font-weight: bold;\">&gt;</span></span></span>\n<span style=\"color: #009900;\"><span
    style=\"color: #000000; font-weight: bold;\">&lt;/xsd:simpleType<span style=\"color:
    #000000; font-weight: bold;\">&gt;</span></span></span>\n<span style=\"color:
    #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:element<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:sequence<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:complexType<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span>\n<span
    style=\"color: #009900;\"><span style=\"color: #000000; font-weight: bold;\">&lt;/xsd:schema<span
    style=\"color: #000000; font-weight: bold;\">&gt;</span></span></span></pre></td></tr></table><p
    class=\"theCode\" style=\"display:none;\"> &lt;xsd:schema targetNamespace=&quot;http://techsquids.com/ts/&quot;
    name=&quot;ts&quot;&gt;\r\n&lt;!-- Request / response types --&gt;\r\n&lt;xsd:element
    name=&quot;tsRequest&quot;&gt;\r\n&lt;xsd:complexType&gt;\r\n&lt;xsd:sequence&gt;\r\n&lt;xsd:element
    name=&quot;year&quot; type=&quot;ts:year&quot;&gt;&lt;/xsd:element&gt;\r\n&lt;xsd:element
    name=&quot;month&quot; type=&quot;ts:month&quot;&gt;&lt;/xsd:element&gt;\r\n&lt;/xsd:sequence&gt;\r\n&lt;/xsd:complexType&gt;\r\n&lt;/xsd:element&gt;\r\n&lt;xsd:element
    name=&quot;tsResponse&quot;&gt;\r\n&lt;xsd:complexType&gt;\r\n&lt;xsd:sequence&gt;\r\n&lt;xsd:element
    name=&quot;year&quot; type=&quot;ts:year&quot;&gt;&lt;/xsd:element&gt;\r\n&lt;xsd:element
    name=&quot;month&quot; type=&quot;ts:month&quot;&gt;&lt;/xsd:element&gt;\r\n&lt;xsd:element
    name=&quot;status&quot; type=&quot;ts:response&quot;&gt;&lt;/xsd:element&gt;\r\n&lt;xsd:element
    name=&quot;output&quot; type=&quot;xsd:string&quot;&gt;&lt;/xsd:element&gt;\r\n&lt;/xsd:sequence&gt;\r\n&lt;/xsd:complexType&gt;\r\n&lt;/xsd:element&gt;\r\n&lt;xsd:simpleType
    name=&quot;year&quot;&gt;\r\n&lt;xsd:restriction base=&quot;xsd:int&quot;&gt;\r\n&lt;xsd:minExclusive
    value=&quot;1970&quot;&gt;&lt;/xsd:minExclusive&gt;\r\n&lt;xsd:maxExclusive value=&quot;9999&quot;&gt;&lt;/xsd:maxExclusive&gt;\r\n&lt;/xsd:restriction&gt;\r\n&lt;/xsd:simpleType&gt;\r\n&lt;xsd:simpleType
    name=&quot;month&quot;&gt;\r\n&lt;xsd:restriction base=&quot;xsd:int&quot;&gt;\r\n&lt;xsd:minInclusive
    value=&quot;1&quot;&gt;&lt;/xsd:minInclusive&gt;\r\n&lt;xsd:maxInclusive value=&quot;12&quot;&gt;&lt;/xsd:maxInclusive&gt;\r\n&lt;/xsd:restriction&gt;\r\n&lt;/xsd:simpleType&gt;\r\n&lt;xsd:complexType
    name=&quot;response&quot;&gt;\r\n&lt;xsd:sequence&gt;\r\n&lt;xsd:element name=&quot;code&quot;
    type=&quot;xsd:int&quot;&gt;&lt;/xsd:element&gt;\r\n&lt;xsd:element name=&quot;message&quot;
    type=&quot;xsd:string&quot;&gt;&lt;/xsd:element&gt;\r\n&lt;xsd:element name=&quot;appCode&quot;&gt;\r\n&lt;xsd:annotation&gt;\r\n&lt;/xsd:annotation&gt;\r\n&lt;xsd:simpleType&gt;\r\n&lt;xsd:restriction
    base=&quot;xsd:string&quot;&gt;\r\n&lt;xsd:enumeration value=&quot;1&quot;&gt;&lt;/xsd:enumeration&gt;\r\n&lt;xsd:enumeration
    value=&quot;2&quot;&gt;&lt;/xsd:enumeration&gt;\r\n&lt;xsd:enumeration value=&quot;3&quot;&gt;&lt;/xsd:enumeration&gt;\r\n&lt;xsd:enumeration
    value=&quot;4&quot;&gt;&lt;/xsd:enumeration&gt;\r\n&lt;xsd:enumeration value=&quot;5&quot;&gt;&lt;/xsd:enumeration&gt;\r\n&lt;xsd:enumeration
    value=&quot;6&quot;&gt;&lt;/xsd:enumeration&gt;\r\n&lt;/xsd:restriction&gt;\r\n&lt;/xsd:simpleType&gt;\r\n&lt;/xsd:element&gt;\r\n&lt;/xsd:sequence&gt;\r\n&lt;/xsd:complexType&gt;\r\n&lt;/xsd:schema&gt;</p></div>\n\";}"
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/extract-xsd-from-wsdl-in-java/"
---
 **Extract XSD from WSDL in Java..**

In the top-down approach of webserivce development, we create the Web service from a WSDL file. In this approach very first service definition is written up.The complete service definition, message format, transport protocol, security and everything is described in WSDL.

wsdl has Types container for data type definitions using some type system (such as XSD), xsd could be either imported using xsd:import or written inside wsdl

if the xsd is part of WSDl and sometime you need to extract the XSD from wsdl, there are no utility to do this task for you.  
The wsimport tool from jdk 1.7 is used to parse an existing WSDL and generate required files (JAX-WS portable artifacts) for WSDL.

1. Java code to extract and write xsd into separate file.

```
package com.ts.common.xsd; import java.io.File; import java.io.FileInputStream; import java.io.IOException; import java.io.InputStream; import java.io.OutputStream; import java.io.PrintWriter; import java.io.StringWriter; import java.util.logging.Logger; import javax.xml.parsers.DocumentBuilder; import javax.xml.parsers.DocumentBuilderFactory; import javax.xml.parsers.ParserConfigurationException; import org.apache.commons.io.output.WriterOutputStream; import org.w3c.dom.Document; import org.w3c.dom.Element; import org.w3c.dom.Node; import org.w3c.dom.NodeList; import org.w3c.dom.ls.DOMImplementationLS; import org.w3c.dom.ls.LSSerializer; public class WsdlToXsdGenerator { private static Logger logger =Logger.getLogger(WsdlToXsdGenerator.class.getName()); public static void wsdlToXSD(InputStream is , OutputStream os) { DocumentBuilder builder; try { builder = getDocBuilder(); Document wsdlDoc = builder.parse(is); Document xsdDoc = getDocBuilder().newDocument(); populateXsdDoc(wsdlDoc, xsdDoc); writeToStream(xsdDoc,os); is.close(); os.flush(); os.close(); } catch (Exception e) { StringWriter sw = new StringWriter(); e.printStackTrace(new PrintWriter(sw)); logger.error(sw.toString()); } } private static void populateXsdDoc(Document wsdlDoc, Document xsdDoc) { Element root = xsdDoc.createElement("xsd:schema"); root.setAttribute("xmlns:xsd", "http://www.w3.org/2001/XMLSchema"); xsdDoc.appendChild(root); Element element = wsdlDoc.getDocumentElement(); Node node = element.getElementsByTagName("wsdl:types").item(0); NodeList lst = node.getChildNodes(); for (int i = 0; i \< lst.getLength(); i++) { Node nd = lst.item(i); if(nd.getNodeName().equals("xsd:schema")){ NodeList xsdNodes = nd.getChildNodes(); for (int j = 0; j \< xsdNodes.getLength(); j++) { Node temp = xsdNodes.item(j); Node toAdded = xsdDoc.importNode(temp, true); root.appendChild(toAdded); } } } } private static void writeToStream(Document document, OutputStream os) throws IOException { DOMImplementationLS domImplementationLS = (DOMImplementationLS) document.getImplementation(); LSSerializer lsSerializer = domImplementationLS.createLSSerializer(); String xsd = lsSerializer.writeToString(document); PrintWriter pw = new PrintWriter(os); // logger.debug(xsd); pw.write(xsd); pw.flush(); } private static DocumentBuilder getDocBuilder() throws ParserConfigurationException{ DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance(); DocumentBuilder builder = factory.newDocumentBuilder(); return builder; } public static void main(String[] args) { StringBuffer sb = new StringBuffer(); WsdlToXsdGenerator.wsdlToXSD(new FileInputStream(new File("ts.wsdl")), new WriterOutputStream( new StringWriter(sb))); System.out.println(sb.toString()); } }
```
2. input

```
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

