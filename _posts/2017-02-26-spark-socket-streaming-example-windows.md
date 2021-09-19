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

```java

package com.ts.spark.streaming; 
import java.io.*; 
import java.net.ServerSocket; 
import java.net.Socket; 
import java.util.Scanner; 

/* 

This class create server socket, open InputStream through \* System.in and read data until find "close" text in separate line

*/ 

public class SocketWriter { 
  public static void main(String[] args) throws Exception {
    System.out.println("Begin"); 
    /* Create socket server */ 
    ServerSocket server = new ServerSocket(9999); 
    //open socket Socket socket = server.accept(); 
    DataOutputStream outputStream = new DataOutputStream(socket.getOutputStream()); 
    System.out.println("Start writing data. Enter close when finish");
    Scanner sc = new Scanner(System.in); 
    String str; 
    /* Read content from scanner and write to socket. */ 

    while (!(str = sc.nextLine()).equals("close")) { 
      outputStream.writeUTF(str); 
      } 
      //close connection now. 

      server.close();
  } 
}
```
- **Default socket receiver will not work as DataOutputStream is required to read data from socket. Use below receiver:**

```java

package com.ts.spark.streaming; 
import org.apache.spark.storage.StorageLevel; 
import org.apache.spark.streaming.receiver.Receiver; 
import java.io.DataInputStream; 
import java.net.ConnectException;
import java.net.Socket; 

/* Custom java socket receive. Replaced BufferedReader with DataSocketStream. */ 

public class JavaCustomSocketReceiver extends Receiver<string> {

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

```
- **Finally use your new Receiver in wordCount. I am saving each red to disk:**

```java

package com.ts.spark.streaming; 
import org.apache.spark.Accumulator; 
import org.apache.spark.SparkConf; 
import org.apache.spark.streaming.Durations; 
import org.apache.spark.streaming.api.java.JavaDStream; 
import org.apache.spark.streaming.api.java.JavaPairDStream; 
import org.apache.spark.streaming.api.java.JavaReceiverInputDStream; 
import org.apache.spark.streaming.api.java.JavaStreamingContext; 
import scala.Tuple2; 
import scala.tools.cmd.Spec; 
import java.util.Arrays; 

/* Socket stream word count example. */

public class SocketStreamingExample { 
        public static void main(String[] args) throws Exception { 
        SparkConf sparkConf = new SparkConf().setAppName("word count example").setMaster("local[*]"); 

        JavaStreamingContext ssc = new JavaStreamingContext(sparkConf, Durations.minutes(1)); 
        Accumulator<integer> count= ssc.sparkContext().accumulator(0,"Ts");
        JavaReceiverInputDStream<string> lines = ssc.receiverStream(new JavaCustomSocketReceiver("localhost", 9999));

        JavaDStream<string> words = lines.flatMap(x ->{
        count.add(1); 
        return Arrays.asList(x.split(" ")).iterator();
        });

        JavaPairDStream<string integer> wordCounts = words.mapToPair(s -> new Tuple2<string integer>(s, 1))
                .reduceByKey((i1, i2) -> i1 + i2);

        wordCounts.foreachRDD(rdd->rdd.saveAsTextFile("<path to save data>"));
       
        ssc.start();
        ssc.awaitTermination();

    }
}
```

Thanks for reading this blog.

