---
layout: post
title: Spark Socket streaming example windows
date: 2017-02-26 12:10:47.000000000 -08:00
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
- spark
meta:
  _edit_last: '1'
  interface_sidebarlayout: default
  _yoast_wpseo_content_score: '30'
  _yoast_wpseo_primary_category: '6'
  _yoast_wpseo_focuskw_text_input: Spark Socket streaming example windows, custom
    Streaming receiver and Socket server
  _yoast_wpseo_focuskw: Spark Socket streaming example windows, custom Streaming receiver
    and Socket server
  _yoast_wpseo_linkdex: '49'
  dsq_thread_id: '5585108724'
  wp-syntax-cache-content: "a:2:{i:1;s:20091:\"\n<div class=\"wp_syntax\" style=\"position:relative;\"><table><tr><td
    class=\"code\"><pre class=\"java\" style=\"font-family:monospace;\"><span style=\"color:
    #000000; font-weight: bold;\">package</span> <span style=\"color: #006699;\">com.ts.spark.streaming</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">java.io.*</span><span style=\"color:
    #339933;\">;</span>\n<span style=\"color: #000000; font-weight: bold;\">import</span>
    <span style=\"color: #006699;\">java.net.ServerSocket</span><span style=\"color:
    #339933;\">;</span>\n<span style=\"color: #000000; font-weight: bold;\">import</span>
    <span style=\"color: #006699;\">java.net.Socket</span><span style=\"color: #339933;\">;</span>\n<span
    style=\"color: #000000; font-weight: bold;\">import</span> <span style=\"color:
    #006699;\">java.util.Scanner</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n<span
    style=\"color: #008000; font-style: italic; font-weight: bold;\">/**\n * &lt;p&gt;This
    class create server socket, open InputStream through\n * System.in and read data
    until find &quot;close&quot; text in separate line&lt;/p&gt;\n */</span>\n<span
    style=\"color: #000000; font-weight: bold;\">public</span> <span style=\"color:
    #000000; font-weight: bold;\">class</span> SocketWriter <span style=\"color: #009900;\">&#123;</span>\n&nbsp;\n
    \   <span style=\"color: #000000; font-weight: bold;\">public</span> <span style=\"color:
    #000000; font-weight: bold;\">static</span> <span style=\"color: #000066; font-weight:
    bold;\">void</span> main<span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #003399;\">String</span><span style=\"color: #009900;\">&#91;</span><span style=\"color:
    #009900;\">&#93;</span> args<span style=\"color: #009900;\">&#41;</span> <span
    style=\"color: #000000; font-weight: bold;\">throws</span> <span style=\"color:
    #003399;\">Exception</span> <span style=\"color: #009900;\">&#123;</span>\n        <span
    style=\"color: #003399;\">System</span>.<span style=\"color: #006633;\">out</span>.<span
    style=\"color: #006633;\">println</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;Begin&quot;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n        <span style=\"color: #008000; font-style:
    italic; font-weight: bold;\">/**\n         * Create socket server\n         */</span>\n
    \       <span style=\"color: #003399;\">ServerSocket</span> server <span style=\"color:
    #339933;\">=</span> <span style=\"color: #000000; font-weight: bold;\">new</span>
    <span style=\"color: #003399;\">ServerSocket</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #cc66cc;\">9999</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n        <span style=\"color: #666666; font-style:
    italic;\">//open socket</span>\n        <span style=\"color: #003399;\">Socket</span>
    socket <span style=\"color: #339933;\">=</span> server.<span style=\"color: #006633;\">accept</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\n        <span style=\"color: #003399;\">DataOutputStream</span>
    outputStream <span style=\"color: #339933;\">=</span> <span style=\"color: #000000;
    font-weight: bold;\">new</span> <span style=\"color: #003399;\">DataOutputStream</span><span
    style=\"color: #009900;\">&#40;</span>socket.<span style=\"color: #006633;\">getOutputStream</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n
    \       <span style=\"color: #003399;\">System</span>.<span style=\"color: #006633;\">out</span>.<span
    style=\"color: #006633;\">println</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;Start writing data. Enter close when finish&quot;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n
    \       Scanner sc <span style=\"color: #339933;\">=</span> <span style=\"color:
    #000000; font-weight: bold;\">new</span> Scanner<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #003399;\">System</span>.<span style=\"color: #006633;\">in</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n
    \       <span style=\"color: #003399;\">String</span> str<span style=\"color:
    #339933;\">;</span>\n        <span style=\"color: #008000; font-style: italic;
    font-weight: bold;\">/**\n         * Read content from scanner and write to socket.\n
    \        */</span>\n        <span style=\"color: #000000; font-weight: bold;\">while</span>
    <span style=\"color: #009900;\">&#40;</span><span style=\"color: #339933;\">!</span><span
    style=\"color: #009900;\">&#40;</span>str <span style=\"color: #339933;\">=</span>
    sc.<span style=\"color: #006633;\">nextLine</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">equals</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;close&quot;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n
    \           outputStream.<span style=\"color: #006633;\">writeUTF</span><span
    style=\"color: #009900;\">&#40;</span>str<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n        <span style=\"color: #009900;\">&#125;</span>\n
    \       <span style=\"color: #666666; font-style: italic;\">//close connection
    now.</span>\n        server.<span style=\"color: #006633;\">close</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n    <span style=\"color: #009900;\">&#125;</span>\n&nbsp;\n<span
    style=\"color: #009900;\">&#125;</span>\n&nbsp;\n<span style=\"color: #339933;\">&lt;/</span>pre\n&nbsp;\n&nbsp;\n<span
    style=\"color: #339933;\">&lt;</span>li<span style=\"color: #339933;\">&gt;</span>\n<span
    style=\"color: #339933;\">&lt;</span>strong<span style=\"color: #339933;\">&gt;</span><span
    style=\"color: #000000; font-weight: bold;\">Default</span> socket receiver will
    not work as <span style=\"color: #003399;\">DataOutputStream</span> is required
    to read data from socket. <span style=\"color: #006633;\">Use</span> below receiver<span
    style=\"color: #339933;\">:&lt;/</span>strong<span style=\"color: #339933;\">&gt;</span>\n<span
    style=\"color: #339933;\">&lt;/</span>li<span style=\"color: #339933;\">&gt;</span>\n<span
    style=\"color: #339933;\">&lt;</span>pre lang<span style=\"color: #339933;\">=</span><span
    style=\"color: #0000ff;\">&quot;java&quot;</span><span style=\"color: #339933;\">&gt;</span>\n<span
    style=\"color: #000000; font-weight: bold;\">package</span> <span style=\"color:
    #006699;\">com.ts.spark.streaming</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n<span
    style=\"color: #000000; font-weight: bold;\">import</span> <span style=\"color:
    #006699;\">org.apache.spark.storage.StorageLevel</span><span style=\"color: #339933;\">;</span>\n<span
    style=\"color: #000000; font-weight: bold;\">import</span> <span style=\"color:
    #006699;\">org.apache.spark.streaming.receiver.Receiver</span><span style=\"color:
    #339933;\">;</span>\n&nbsp;\n<span style=\"color: #000000; font-weight: bold;\">import</span>
    <span style=\"color: #006699;\">java.io.DataInputStream</span><span style=\"color:
    #339933;\">;</span>\n<span style=\"color: #000000; font-weight: bold;\">import</span>
    <span style=\"color: #006699;\">java.net.ConnectException</span><span style=\"color:
    #339933;\">;</span>\n<span style=\"color: #000000; font-weight: bold;\">import</span>
    <span style=\"color: #006699;\">java.net.Socket</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n<span
    style=\"color: #008000; font-style: italic; font-weight: bold;\">/**\n * Custom
    java socket receiver\n * Replaced BufferedReader with DataSocketStream.\n */</span>\n<span
    style=\"color: #000000; font-weight: bold;\">public</span> <span style=\"color:
    #000000; font-weight: bold;\">class</span> JavaCustomSocketReceiver <span style=\"color:
    #000000; font-weight: bold;\">extends</span> Receiver<span style=\"color: #339933;\">&lt;</span>String<span
    style=\"color: #339933;\">&gt;</span> <span style=\"color: #009900;\">&#123;</span>\n&nbsp;\n
    \   <span style=\"color: #003399;\">String</span> host <span style=\"color: #339933;\">=</span>
    <span style=\"color: #000066; font-weight: bold;\">null</span><span style=\"color:
    #339933;\">;</span>\n    <span style=\"color: #000066; font-weight: bold;\">int</span>
    port <span style=\"color: #339933;\">=</span> <span style=\"color: #339933;\">-</span><span
    style=\"color: #cc66cc;\">1</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n
    \   <span style=\"color: #000000; font-weight: bold;\">public</span> JavaCustomSocketReceiver<span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #003399;\">String</span>
    host_ , <span style=\"color: #000066; font-weight: bold;\">int</span> port_<span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n
    \       <span style=\"color: #000000; font-weight: bold;\">super</span><span style=\"color:
    #009900;\">&#40;</span>StorageLevel.<span style=\"color: #006633;\">MEMORY_AND_DISK_2</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n
    \       host <span style=\"color: #339933;\">=</span> host_<span style=\"color:
    #339933;\">;</span>\n        port <span style=\"color: #339933;\">=</span> port_<span
    style=\"color: #339933;\">;</span>\n    <span style=\"color: #009900;\">&#125;</span>\n&nbsp;\n
    \   <span style=\"color: #000000; font-weight: bold;\">public</span> <span style=\"color:
    #000066; font-weight: bold;\">void</span> onStart<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n
    \       <span style=\"color: #666666; font-style: italic;\">// Start the thread
    that receives data over a connection</span>\n        <span style=\"color: #000000;
    font-weight: bold;\">new</span> <span style=\"color: #003399;\">Thread</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>
    \ <span style=\"color: #009900;\">&#123;</span>\n            @Override <span style=\"color:
    #000000; font-weight: bold;\">public</span> <span style=\"color: #000066; font-weight:
    bold;\">void</span> run<span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n                receive<span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n            <span style=\"color: #009900;\">&#125;</span>\n
    \       <span style=\"color: #009900;\">&#125;</span>.<span style=\"color: #006633;\">start</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n    <span style=\"color: #009900;\">&#125;</span>\n&nbsp;\n
    \   <span style=\"color: #000000; font-weight: bold;\">public</span> <span style=\"color:
    #000066; font-weight: bold;\">void</span> onStop<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n
    \       <span style=\"color: #666666; font-style: italic;\">// There is nothing
    much to do as the thread calling receive()</span>\n        <span style=\"color:
    #666666; font-style: italic;\">// is designed to stop by itself if isStopped()
    returns false</span>\n    <span style=\"color: #009900;\">&#125;</span>\n&nbsp;\n
    \   <span style=\"color: #008000; font-style: italic; font-weight: bold;\">/**
    Create a socket connection and receive data until receiver is stopped */</span>\n
    \   <span style=\"color: #000000; font-weight: bold;\">private</span> <span style=\"color:
    #000066; font-weight: bold;\">void</span> receive<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n
    \       <span style=\"color: #003399;\">Socket</span> socket <span style=\"color:
    #339933;\">=</span> <span style=\"color: #000066; font-weight: bold;\">null</span><span
    style=\"color: #339933;\">;</span>\n        <span style=\"color: #003399;\">String</span>
    userInput <span style=\"color: #339933;\">=</span> <span style=\"color: #000066;
    font-weight: bold;\">null</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n
    \       <span style=\"color: #000000; font-weight: bold;\">try</span> <span style=\"color:
    #009900;\">&#123;</span>\n            <span style=\"color: #666666; font-style:
    italic;\">// connect to the server</span>\n            socket <span style=\"color:
    #339933;\">=</span> <span style=\"color: #000000; font-weight: bold;\">new</span>
    <span style=\"color: #003399;\">Socket</span><span style=\"color: #009900;\">&#40;</span>host,
    port<span style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n
    \           <span style=\"color: #003399;\">DataInputStream</span> reader<span
    style=\"color: #339933;\">=</span><span style=\"color: #000000; font-weight: bold;\">new</span>
    <span style=\"color: #003399;\">DataInputStream</span><span style=\"color: #009900;\">&#40;</span>socket.<span
    style=\"color: #006633;\">getInputStream</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n            <span style=\"color: #666666;
    font-style: italic;\">// Until stopped or connection broken continue reading</span>\n
    \           <span style=\"color: #000000; font-weight: bold;\">while</span> <span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #339933;\">!</span>isStopped<span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #339933;\">&amp;&amp;</span> <span style=\"color: #009900;\">&#40;</span>userInput
    <span style=\"color: #339933;\">=</span> reader.<span style=\"color: #006633;\">readUTF</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #339933;\">!=</span>
    <span style=\"color: #000066; font-weight: bold;\">null</span><span style=\"color:
    #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n                store<span
    style=\"color: #009900;\">&#40;</span>userInput<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n            <span style=\"color: #009900;\">&#125;</span>\n
    \           reader.<span style=\"color: #006633;\">close</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n            socket.<span style=\"color: #006633;\">close</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\n            <span style=\"color: #666666;
    font-style: italic;\">// Restart in an attempt to connect again when server is
    active again</span>\n            restart<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;Trying to connect again&quot;</span><span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n        <span
    style=\"color: #009900;\">&#125;</span> <span style=\"color: #000000; font-weight:
    bold;\">catch</span><span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #003399;\">ConnectException</span> ce<span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #009900;\">&#123;</span>\n            <span style=\"color:
    #666666; font-style: italic;\">// restart if could not connect to server</span>\n
    \           restart<span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #0000ff;\">&quot;Could not connect&quot;</span>, ce<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n        <span style=\"color: #009900;\">&#125;</span>
    <span style=\"color: #000000; font-weight: bold;\">catch</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #003399;\">Throwable</span> t<span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #009900;\">&#123;</span>\n
    \           <span style=\"color: #666666; font-style: italic;\">// restart if
    there is any other error</span>\n            restart<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;Error receiving data&quot;</span>, t<span style=\"color:
    #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n        <span
    style=\"color: #009900;\">&#125;</span>\n    <span style=\"color: #009900;\">&#125;</span>\n<span
    style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">package com.ts.spark.streaming;\r\n\r\nimport java.io.*;\r\nimport
    java.net.ServerSocket;\r\nimport java.net.Socket;\r\nimport java.util.Scanner;\r\n\r\n/**\r\n
    * &lt;p&gt;This class create server socket, open InputStream through\r\n * System.in
    and read data until find &quot;close&quot; text in separate line&lt;/p&gt;\r\n
    */\r\npublic class SocketWriter {\r\n\r\n    public static void main(String[]
    args) throws Exception {\r\n        System.out.println(&quot;Begin&quot;);\r\n
    \       /**\r\n         * Create socket server\r\n         */\r\n        ServerSocket
    server = new ServerSocket(9999);\r\n        //open socket\r\n        Socket socket
    = server.accept();\r\n\r\n        DataOutputStream outputStream = new DataOutputStream(socket.getOutputStream());\r\n\r\n
    \       System.out.println(&quot;Start writing data. Enter close when finish&quot;);\r\n
    \       Scanner sc = new Scanner(System.in);\r\n        String str;\r\n        /**\r\n
    \        * Read content from scanner and write to socket.\r\n         */\r\n        while
    (!(str = sc.nextLine()).equals(&quot;close&quot;)) {\r\n            outputStream.writeUTF(str);\r\n
    \       }\r\n        //close connection now.\r\n        server.close();\r\n    }\r\n\r\n}\r\n\r\n&lt;/pre\r\n\r\n\r\n&lt;li&gt;\r\n&lt;strong&gt;Default
    socket receiver will not work as DataOutputStream is required to read data from
    socket. Use below receiver:&lt;/strong&gt;\r\n&lt;/li&gt;\r\n&lt;pre lang=&quot;java&quot;&gt;\r\npackage
    com.ts.spark.streaming;\r\n\r\nimport org.apache.spark.storage.StorageLevel;\r\nimport
    org.apache.spark.streaming.receiver.Receiver;\r\n\r\nimport java.io.DataInputStream;\r\nimport
    java.net.ConnectException;\r\nimport java.net.Socket;\r\n\r\n/**\r\n * Custom
    java socket receiver\r\n * Replaced BufferedReader with DataSocketStream.\r\n
    */\r\npublic class JavaCustomSocketReceiver extends Receiver&lt;String&gt; {\r\n\r\n
    \   String host = null;\r\n    int port = -1;\r\n\r\n    public JavaCustomSocketReceiver(String
    host_ , int port_) {\r\n        super(StorageLevel.MEMORY_AND_DISK_2());\r\n        host
    = host_;\r\n        port = port_;\r\n    }\r\n\r\n    public void onStart() {\r\n
    \       // Start the thread that receives data over a connection\r\n        new
    Thread()  {\r\n            @Override public void run() {\r\n                receive();\r\n
    \           }\r\n        }.start();\r\n    }\r\n\r\n    public void onStop() {\r\n
    \       // There is nothing much to do as the thread calling receive()\r\n        //
    is designed to stop by itself if isStopped() returns false\r\n    }\r\n\r\n    /**
    Create a socket connection and receive data until receiver is stopped */\r\n    private
    void receive() {\r\n        Socket socket = null;\r\n        String userInput
    = null;\r\n\r\n        try {\r\n            // connect to the server\r\n            socket
    = new Socket(host, port);\r\n\r\n            DataInputStream reader=new DataInputStream(socket.getInputStream());\r\n
    \           // Until stopped or connection broken continue reading\r\n            while
    (!isStopped() &amp;&amp; (userInput = reader.readUTF()) != null) {\r\n                store(userInput);\r\n
    \           }\r\n            reader.close();\r\n            socket.close();\r\n\r\n
    \           // Restart in an attempt to connect again when server is active again\r\n
    \           restart(&quot;Trying to connect again&quot;);\r\n        } catch(ConnectException
    ce) {\r\n            // restart if could not connect to server\r\n            restart(&quot;Could
    not connect&quot;, ce);\r\n        } catch(Throwable t) {\r\n            // restart
    if there is any other error\r\n            restart(&quot;Error receiving data&quot;,
    t);\r\n        }\r\n    }\r\n}</p></div>\n\";i:2;s:10149:\"\n<div class=\"wp_syntax\"
    style=\"position:relative;\"><table><tr><td class=\"code\"><pre class=\"java\"
    style=\"font-family:monospace;\"><span style=\"color: #000000; font-weight: bold;\">package</span>
    <span style=\"color: #006699;\">com.ts.spark.streaming</span><span style=\"color:
    #339933;\">;</span>\n&nbsp;\n<span style=\"color: #000000; font-weight: bold;\">import</span>
    <span style=\"color: #006699;\">org.apache.spark.Accumulator</span><span style=\"color:
    #339933;\">;</span>\n<span style=\"color: #000000; font-weight: bold;\">import</span>
    <span style=\"color: #006699;\">org.apache.spark.SparkConf</span><span style=\"color:
    #339933;\">;</span>\n<span style=\"color: #000000; font-weight: bold;\">import</span>
    <span style=\"color: #006699;\">org.apache.spark.streaming.Durations</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">org.apache.spark.streaming.api.java.JavaDStream</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">org.apache.spark.streaming.api.java.JavaPairDStream</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">org.apache.spark.streaming.api.java.JavaReceiverInputDStream</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">org.apache.spark.streaming.api.java.JavaStreamingContext</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">scala.Tuple2</span><span
    style=\"color: #339933;\">;</span>\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">scala.tools.cmd.Spec</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\n<span style=\"color: #000000; font-weight:
    bold;\">import</span> <span style=\"color: #006699;\">java.util.Arrays</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\n<span style=\"color: #008000; font-style:
    italic; font-weight: bold;\">/**\n * Socket stream word count example.\n */</span>\n<span
    style=\"color: #000000; font-weight: bold;\">public</span> <span style=\"color:
    #000000; font-weight: bold;\">class</span> SocketStreamingExample <span style=\"color:
    #009900;\">&#123;</span>\n    <span style=\"color: #000000; font-weight: bold;\">public</span>
    <span style=\"color: #000000; font-weight: bold;\">static</span> <span style=\"color:
    #000066; font-weight: bold;\">void</span> main<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #003399;\">String</span><span style=\"color: #009900;\">&#91;</span><span
    style=\"color: #009900;\">&#93;</span> args<span style=\"color: #009900;\">&#41;</span>
    <span style=\"color: #000000; font-weight: bold;\">throws</span> <span style=\"color:
    #003399;\">Exception</span> <span style=\"color: #009900;\">&#123;</span>\n&nbsp;\n
    \       SparkConf sparkConf <span style=\"color: #339933;\">=</span> <span style=\"color:
    #000000; font-weight: bold;\">new</span> SparkConf<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span>.<span style=\"color: #006633;\">setAppName</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #0000ff;\">&quot;word
    count example&quot;</span><span style=\"color: #009900;\">&#41;</span>.<span style=\"color:
    #006633;\">setMaster</span><span style=\"color: #009900;\">&#40;</span><span style=\"color:
    #0000ff;\">&quot;local[*]&quot;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n        JavaStreamingContext ssc <span style=\"color:
    #339933;\">=</span> <span style=\"color: #000000; font-weight: bold;\">new</span>
    JavaStreamingContext<span style=\"color: #009900;\">&#40;</span>sparkConf, Durations.<span
    style=\"color: #006633;\">minutes</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #cc66cc;\">1</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n
    \       Accumulator<span style=\"color: #339933;\">&lt;</span>Integer<span style=\"color:
    #339933;\">&gt;</span> count<span style=\"color: #339933;\">=</span> ssc.<span
    style=\"color: #006633;\">sparkContext</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span>.<span style=\"color: #006633;\">accumulator</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #cc66cc;\">0</span>,<span
    style=\"color: #0000ff;\">&quot;Ts&quot;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n        JavaReceiverInputDStream<span style=\"color:
    #339933;\">&lt;</span>String<span style=\"color: #339933;\">&gt;</span> lines
    <span style=\"color: #339933;\">=</span> ssc.<span style=\"color: #006633;\">receiverStream</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #000000; font-weight:
    bold;\">new</span> JavaCustomSocketReceiver<span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #0000ff;\">&quot;localhost&quot;</span>, <span style=\"color: #cc66cc;\">9999</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\n        JavaDStream<span style=\"color:
    #339933;\">&lt;</span>String<span style=\"color: #339933;\">&gt;</span> words
    <span style=\"color: #339933;\">=</span> lines.<span style=\"color: #006633;\">flatMap</span><span
    style=\"color: #009900;\">&#40;</span>x <span style=\"color: #339933;\">-&gt;</span><span
    style=\"color: #009900;\">&#123;</span>count.<span style=\"color: #006633;\">add</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #cc66cc;\">1</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>
    <span style=\"color: #000000; font-weight: bold;\">return</span>  <span style=\"color:
    #003399;\">Arrays</span>.<span style=\"color: #006633;\">asList</span><span style=\"color:
    #009900;\">&#40;</span>x.<span style=\"color: #006633;\">split</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #0000ff;\">&quot; &quot;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span>.<span
    style=\"color: #006633;\">iterator</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span><span
    style=\"color: #009900;\">&#125;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\n        JavaPairDStream<span style=\"color:
    #339933;\">&lt;</span><span style=\"color: #003399;\">String</span>, Integer<span
    style=\"color: #339933;\">&gt;</span> wordCounts <span style=\"color: #339933;\">=</span>
    words.<span style=\"color: #006633;\">mapToPair</span><span style=\"color: #009900;\">&#40;</span>s
    <span style=\"color: #339933;\">-&gt;</span> <span style=\"color: #000000; font-weight:
    bold;\">new</span> Tuple2<span style=\"color: #339933;\">&lt;</span><span style=\"color:
    #003399;\">String</span>, Integer<span style=\"color: #339933;\">&gt;</span><span
    style=\"color: #009900;\">&#40;</span>s, <span style=\"color: #cc66cc;\">1</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #009900;\">&#41;</span>\n
    \               .<span style=\"color: #006633;\">reduceByKey</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#40;</span>i1, i2<span
    style=\"color: #009900;\">&#41;</span> <span style=\"color: #339933;\">-&gt;</span>
    i1 <span style=\"color: #339933;\">+</span> i2<span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #339933;\">;</span>\n&nbsp;\n        wordCounts.<span style=\"color:
    #006633;\">foreachRDD</span><span style=\"color: #009900;\">&#40;</span>rdd<span
    style=\"color: #339933;\">-&gt;</span>rdd.<span style=\"color: #006633;\">saveAsTextFile</span><span
    style=\"color: #009900;\">&#40;</span><span style=\"color: #0000ff;\">&quot;&lt;path
    to save data&gt;&quot;</span><span style=\"color: #009900;\">&#41;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n&nbsp;\n
    \       ssc.<span style=\"color: #006633;\">start</span><span style=\"color: #009900;\">&#40;</span><span
    style=\"color: #009900;\">&#41;</span><span style=\"color: #339933;\">;</span>\n
    \       ssc.<span style=\"color: #006633;\">awaitTermination</span><span style=\"color:
    #009900;\">&#40;</span><span style=\"color: #009900;\">&#41;</span><span style=\"color:
    #339933;\">;</span>\n&nbsp;\n    <span style=\"color: #009900;\">&#125;</span>\n<span
    style=\"color: #009900;\">&#125;</span></pre></td></tr></table><p class=\"theCode\"
    style=\"display:none;\">package com.ts.spark.streaming;\r\n\r\nimport org.apache.spark.Accumulator;\r\nimport
    org.apache.spark.SparkConf;\r\nimport org.apache.spark.streaming.Durations;\r\nimport
    org.apache.spark.streaming.api.java.JavaDStream;\r\nimport org.apache.spark.streaming.api.java.JavaPairDStream;\r\nimport
    org.apache.spark.streaming.api.java.JavaReceiverInputDStream;\r\nimport org.apache.spark.streaming.api.java.JavaStreamingContext;\r\nimport
    scala.Tuple2;\r\nimport scala.tools.cmd.Spec;\r\n\r\nimport java.util.Arrays;\r\n\r\n/**\r\n
    * Socket stream word count example.\r\n */\r\npublic class SocketStreamingExample
    {\r\n    public static void main(String[] args) throws Exception {\r\n\r\n        SparkConf
    sparkConf = new SparkConf().setAppName(&quot;word count example&quot;).setMaster(&quot;local[*]&quot;);\r\n
    \       JavaStreamingContext ssc = new JavaStreamingContext(sparkConf, Durations.minutes(1));\r\n\r\n
    \       Accumulator&lt;Integer&gt; count= ssc.sparkContext().accumulator(0,&quot;Ts&quot;);\r\n
    \       JavaReceiverInputDStream&lt;String&gt; lines = ssc.receiverStream(new
    JavaCustomSocketReceiver(&quot;localhost&quot;, 9999));\r\n\r\n        JavaDStream&lt;String&gt;
    words = lines.flatMap(x -&gt;{count.add(1); return  Arrays.asList(x.split(&quot;
    &quot;)).iterator();});\r\n\r\n        JavaPairDStream&lt;String, Integer&gt;
    wordCounts = words.mapToPair(s -&gt; new Tuple2&lt;String, Integer&gt;(s, 1))\r\n
    \               .reduceByKey((i1, i2) -&gt; i1 + i2);\r\n\r\n        wordCounts.foreachRDD(rdd-&gt;rdd.saveAsTextFile(&quot;&lt;path
    to save data&gt;&quot;));\r\n       \r\n        ssc.start();\r\n        ssc.awaitTermination();\r\n\r\n
    \   }\r\n}</p></div>\n\";}"
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/spark-socket-streaming-example-windows/"
---
Spark Socket streaming example windows:  
Windows OS doesn't provide any netcat utility and if you are trying to test your spark streaming socket program in windows then either you download external netcat utility or create socket program equivalent to netcat.

The spark streaming socket [word count example](http://spark.apache.org/docs/latest/streaming-programming-guide.html#a-quick-example) is implemented using netcat command.

Create socket utility using java, integrate it with Spark streaming and CustomSocketReceiver in java.

- 

**Create socket server utility which opens port and write data to socket:**

```
package com.ts.spark.streaming; import java.io.\*; import java.net.ServerSocket; import java.net.Socket; import java.util.Scanner; /\*\* \* 

This class create server socket, open InputStream through \* System.in and read data until find "close" text in separate line

 \*/ public class SocketWriter { public static void main(String[] args) throws Exception { System.out.println("Begin"); /\*\* \* Create socket server \*/ ServerSocket server = new ServerSocket(9999); //open socket Socket socket = server.accept(); DataOutputStream outputStream = new DataOutputStream(socket.getOutputStream()); System.out.println("Start writing data. Enter close when finish"); Scanner sc = new Scanner(System.in); String str; /\*\* \* Read content from scanner and write to socket. \*/ while (!(str = sc.nextLine()).equals("close")) { outputStream.writeUTF(str); } //close connection now. server.close(); } }
```
- **Default socket receiver will not work as DataOutputStream is required to read data from socket. Use below receiver:**

```
package com.ts.spark.streaming; import org.apache.spark.storage.StorageLevel; import org.apache.spark.streaming.receiver.Receiver; import java.io.DataInputStream; import java.net.ConnectException; import java.net.Socket; /\*\* \* Custom java socket receiver \* Replaced BufferedReader with DataSocketStream. \*/ public class JavaCustomSocketReceiver extends Receiver<string> {

    String host = null;
    int port = -1;

    public JavaCustomSocketReceiver(String host_ , int port_) {
        super(StorageLevel.MEMORY_AND_DISK_2());
        host = host_;
        port = port_;
    }

    public void onStart() {
        // Start the thread that receives data over a connection
        new Thread() {
            @Override public void run() {
                receive();
            }
        }.start();
    }

    public void onStop() {
        // There is nothing much to do as the thread calling receive()
        // is designed to stop by itself if isStopped() returns false
    }

    /** Create a socket connection and receive data until receiver is stopped */
    private void receive() {
        Socket socket = null;
        String userInput = null;

        try {
            // connect to the server
            socket = new Socket(host, port);

            DataInputStream reader=new DataInputStream(socket.getInputStream());
            // Until stopped or connection broken continue reading
            while (!isStopped() &amp;&amp; (userInput = reader.readUTF()) != null) {
                store(userInput);
            }
            reader.close();
            socket.close();

            // Restart in an attempt to connect again when server is active again
            restart("Trying to connect again");
        } catch(ConnectException ce) {
            // restart if could not connect to server
            restart("Could not connect", ce);
        } catch(Throwable t) {
            // restart if there is any other error
            restart("Error receiving data", t);
        }
    }
}

</string>
```
- **Finally use your new Receiver in wordCount. I am saving each red to disk:**

```
package com.ts.spark.streaming; import org.apache.spark.Accumulator; import org.apache.spark.SparkConf; import org.apache.spark.streaming.Durations; import org.apache.spark.streaming.api.java.JavaDStream; import org.apache.spark.streaming.api.java.JavaPairDStream; import org.apache.spark.streaming.api.java.JavaReceiverInputDStream; import org.apache.spark.streaming.api.java.JavaStreamingContext; import scala.Tuple2; import scala.tools.cmd.Spec; import java.util.Arrays; /\*\* \* Socket stream word count example. \*/ public class SocketStreamingExample { public static void main(String[] args) throws Exception { SparkConf sparkConf = new SparkConf().setAppName("word count example").setMaster("local[\*]"); JavaStreamingContext ssc = new JavaStreamingContext(sparkConf, Durations.minutes(1)); Accumulator<integer> count= ssc.sparkContext().accumulator(0,"Ts");
        JavaReceiverInputDStream<string> lines = ssc.receiverStream(new JavaCustomSocketReceiver("localhost", 9999));

        JavaDStream<string> words = lines.flatMap(x -&gt;{count.add(1); return Arrays.asList(x.split(" ")).iterator();});

        JavaPairDStream<string integer> wordCounts = words.mapToPair(s -&gt; new Tuple2<string integer>(s, 1))
                .reduceByKey((i1, i2) -&gt; i1 + i2);

        wordCounts.foreachRDD(rdd-&gt;rdd.saveAsTextFile("<path to save data>"));
       
        ssc.start();
        ssc.awaitTermination();

    }
}

</path></string></string></string></string></integer>
```

Thanks for reading this blog.

