---
layout: post
title: Spark Dataset Operations in java
date: 2017-02-23 09:57:12.000000000 -08:00
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
  _yoast_wpseo_focuskw_text_input: Spark Dataset Operations using java, FilterFunction,
    SparkSession
  _yoast_wpseo_focuskw: Spark Dataset Operations using java, FilterFunction, SparkSession
  _yoast_wpseo_linkdex: '45'
  dsq_thread_id: '5576718005'
  _yoast_wpseo_metadesc: Spark Dataset Operations in java, FilterFunction, SparkSession
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/spark-dataset-operations-java/"
---
## Spark Dataset Operations using java

This post demonstrate step by step setup of spark project and explore a few basics Spark dataset operations like create dataset and filter content.

### Create Maven project with POM:

```xml
<?xml version="1.0" encoding="UTF-8"?><project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemalocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelversion>4.0.0</modelversion>
    <groupid>com.ts.spark</groupid>
    <artifactid>api</artifactid>
    <version>1.0-SNAPSHOT</version>

<dependencies>
    <dependency>
        <groupid>org.apache.spark</groupid>
        <artifactid>spark-core_2.11</artifactid>
        <version>2.0.0</version>
    </dependency>
    <dependency>
        <groupid>org.apache.spark</groupid>
        <artifactid>spark-sql_2.11</artifactid>
        <version>2.0.0</version>
    </dependency>

</dependencies>
    <build>
        <plugins>
            <plugin>
                <groupid>org.apache.maven.plugins</groupid>
                <artifactid>maven-compiler-plugin</artifactid>
                <version>3.5.1</version>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
```

### Project structure:

[structure](/assets/images/Screen-Shot-2017-02-22-at-9.25.53-PM-150x150.png)

### Create Bean definition:

```java

public class People implements Serializable { 
  private String name; 
  private Long age; 
  public People() { } 
  public People(String name, Long age) { 
  this.name = name; 
  this.age = age; 
  } 
  
  public String getName() { 
  return name; 
  } 
  
  public void setName(String name) { 
    this.name = name; 
  } 
  
  public Long getAge() { 
    return age; 
  } 
  
  public void setAge(Long age) { 
    this.age = age;
  } 
  
}
```

Create people.json file in resource directory:  

```json

{"name":"PhilipHester","age":88}  
{"name":"DylanBecker","age":64}  
{"name":"JohnCarpenter","age":60}  
{"name":"DeclanBarton","age":64}  
{"name":"KennedySutton","age":91}  
{"name":"DolanRowland","age":96}  
{"name":"JonahWhitaker","age":41}

```

### Filter content of dataset:

```java 
public class Application { 
public static void main(String[] args) { 
  SparkSession session=SparkSession.builder().appName("dataset example").getOrCreate(); 
  /* Define encoder, used to convert data to binary format in jvm */ 
  
  Encoder encode= Encoders.bean(People.class); 
  /* Load dataset from json */ 
  
  Dataset ds= session.read().json(Thread.currentThread(). getContextClassLoader().getResource("people.json"). getPath()).as(encode); 
  ds.filter((FilterFunction<people>)s->s.getAge()>30)).show();

    }
}
```
