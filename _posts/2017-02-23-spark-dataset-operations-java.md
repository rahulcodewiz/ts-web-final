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
# Guide to Setting Up a Spark Project and Exploring Basic Spark Dataset Operations

Spark is a powerful framework for big data processing, and it's essential to understand how to set up a Spark project and work with Spark datasets. In this blog post, we'll walk you through the process step by step, from creating a Maven project to filtering data in a Spark dataset. Let's get started!

This application does the following:

- Creates a Spark session.
- Defines an encoder for the People class.
- Loads the dataset from the people.json file.
- Filters the dataset to show only individuals with an age greater than 30.


### Create Maven project with POM:

The first step is to create a Maven project for your Spark application. Maven is a popular build and project management tool for Java applications. You can set up your project by creating a pom.xml file with the following content:

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

This pom.xml file defines your project's dependencies, including Spark Core and Spark SQL.


### Project structure:

Before you start coding, let's take a quick look at the project structure:

[structure](/assets/images/Screen-Shot-2017-02-22-at-9.25.53-PM-150x150.png)

### Create Bean definition:

In this step, you'll create a Java class to represent the data you'll be working with. In this example, we're using a People class to represent individuals with a name and age. Here's the code for the People class:

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

You'll need some data to work with. Create a `people.json`` file in your project's resource directory with the following content:

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

Now, let's write the Spark application to load the dataset and filter its content based on a condition. Here's the Java code for your Spark application:

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

In conclusion, you've just completed a step-by-step setup of a Spark project and explored basic Spark dataset operations. You can use this foundation to build more complex data processing and analysis tasks with Apache Spark. Have fun exploring the world of big data processing!
