---
layout: post
title: Apache Spark Examples in Java
date: 2018-01-26 04:22:02.000000000 -08:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Big Data
- java
tags:
- bigdata
- java
- spark
meta:
  _edit_last: '1'
  _yoast_wpseo_primary_category: '6'
  interface_sidebarlayout: default
  _yoast_wpseo_focuskw: Spark Java tutorial
  _yoast_wpseo_linkdex: '38'
  _yoast_wpseo_content_score: '30'
  _wp_old_slug: spark-java-tutorial
  _wp_old_date: '2019-08-26'
  _ez-toc-disabled: ''
  _ez-toc-insert: ''
  _ez-toc-heading-levels: a:0:{}
  _ez-toc-alttext: ''
  _ez-toc-exclude: ''
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/useful-spark-methods-implementation-in-java/"
---

This post attempts to share the common issues that data engineer face while writing Spark in Java and how to solve those issues. Writing Spark in Java isn't fun and my preference is always Scala but there can be situations when you don't have luxyary to choose language of your preference.

![Spark and Java](/assets/images/spark-and-java-8.png)



## How to Use non-serializable **classes** in Spark closures-


Spark closures, objects must be serializable otherwise spark engine throws 'NotSerializableException'. You will often come across the situation when you can't change the actual class implementation. You can explicitly tell Spark to serialize certain classes using serializer. In this example I implemented a custom Java class using Kryo to to register non-serializable classes.


*Register classes as serializable in SparkContent*


    //Exact exception spark throws when class is not serialize 
    java.io.NotSerializableException: com.ts.blog.batch.serialize.ABean Serialization stack: -
    object not serializable (class: com.ts.blog.batch.serialize.ABean, value: com.ts.blog.batch.serialize.ABean@27f71dca)



```java
/* Create Custom KryoRegistrator implementation*/

public class CustomKKryoRegistrator implements org.apache.spark.serializer.KryoRegistrator{

  @Override public void registerClasses(Kryo kryo) {
    kryo.register(ABean.class ); //Register non serialize classes 
  } 
} 
//Register Kryo in SparkConf- 

sparkConf.set( "spark.kryo.registrar",CustomKKryoRegistrator.class.getName());
```

*Reference*
[Apache Spark Wiki](https://spark.apache.org/docs/latest/tuning.html#data-serialization)

## Create Dataset using Encoder:

Encoder is part of Spark's tungusten framework and backbone of Spark 2.0 project. It helps to define custom datatypes or schema for dataset. Encoders are generally created automatically through implicits from a SparkSession, or can be explicitly created by calling static methods on Encoders. In this example we will use Encoders static method to define new class.

**Dataset Encoder**

```java
import org.apache.spark.sql.Encoder; 
import org.apache.spark.sql.Encoders;

Encoder<Employee> employeeEncoder = Encoders.bean(Employee.class); 
Dataset<Employee> dataset= session.read().json(employee.json).as(employeeEncoder); 
public class Employee { 
  private Integer id ; 
  private String name ; 
}
```

**Dataset**
    cat employee.json  
    { "id" : 100, "name" : "xyz" }   
    { "id" : 200, "name" : "prq" }


**Find out the Max value from Dataset column**


```java
Row max = dataset.agg(org.apache.spark.sql.functions.max(dataset.col( "id" ))).as( "max" ).head();
System.out.println(max);
```

**Define custom UDF Function with SparkSession**

```java
Dataset<Long> ds= SessionRegistry.session.range(1,20);

        ds.sparkSession().udf().register("add100",(Long l)->l+100,org.apache.spark.sql.types.DataTypes.LongType);

        ds.show();
        ds.registerTempTable("allnum");

        ds.sparkSession().sql("select add100(id) from allnum").show();
```

*Reference*
[Apache Spark Wiki](https://spark.apache.org/docs/latest/api/java/index.html?org/apache/spark/sql/Dataset.html)


## How to use Custom Property file in Spark -

Config driven development is very important for jvm based languages and can save huge artifact build cycle time. This section covers:

- How to declare property file
- Spark Submit command
- How to access config attribute programatically.


**Declare property file- e.g. job.properties**

> custom.prop=xyz

**Spark submit command**


    ${SPARK_HOME}/bin/spark-submit --files job.properties

In this case Spark driver will run in local model and file to be present in directory where spark-submit is executed

**Read file in Spark Driver**

```java

import java.util.Properties;
import org.apache.hadoop.fs.FSDataInputStream;
import org.apache.hadoop.fs.FileSystem;
import org.apache.hadoop.fs.Path;
import org.apache.spark.SparkFiles;
import java.io.InputStream;
import java.io.FileInputStream;

//Load file to propert object using HDFS FileSystem
String fileName = SparkFiles.get("job.properties")
Configuration hdfsConf = new Configuration();
FileSystem fs = FileSystem.get(hdfsConf);

//THe file name contains absolute path of file
FSDataInputStream is = fs.open(new Path(fileName));

Properties prop = new Properties();
//load properties
prop.load(is)
//retrieve properties
prop.getProperty("custom.prop");
```


## Accumulator implementation-

Accumulators are shared varibles and very helpful with operations like count during map or action. Custom types accumulars are supported in spark and only restriction is that it should be associative and commutative.

**Accumulators java example**

```java
/* The sample accumulator to store set of string values */
class CustomAccumulator extends AccumulatorV2<String,Set<String>>{
  Set<String> myval = new HashSet<>(); 
  @Override public void merge(AccumulatorV2<String, Set<String>> other) {
    other.value().stream().forEach(val-> myval.add(val));
    } 
    
    @Override public boolean isZero() { 
      return myval.size()==0; 
    } 
    
    @Override public AccumulatorV2<String, Set<String>> copy() { 
      return this ; 
     }
     
     @Override public void reset() {
        myval.clear(); 
      } 
      
      @Override public void add(String v) { 
        myval.add(v); 
      } 
      
      @Override public Set<String> value() { 
        return myval; 
        } 
       } 
       
       //Register accumulator to SparkContext. jsc object is created during init section (begining) 
       
       AccumulatorV2 accumulatorV2 = new CustomAccumulator();
       
       jsc.sc().register(accumulatorV2); 
       //Use accumulatorV2 like normal accumulator
```

*References*

[Spark Wiki Accumulators](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#accumulators)

#### Custom Type Comparator-

Comparator play important role in data comparison for actions like min, max, sort etc and there are out of the comparator for in-built datatypes (String, int, float, double). But there are cases when you need to run those Spark actions on custom defined objects and you need to tell Spark engine how to compare objects. 


**Comparator for custom object**
```java

public class MyBean{
  public String name;
  public Integer Id;
  public integer address;
}
```

For the mathematically inclined, the relation that defines the imposed ordering that a given comparator c imposes on a given set of objects S is:

       {(name, id) such that c.compare(name, id) <= 0}.
 
The quotient for this total order is:

       {(name, id) such that c.compare(name, id) == 0}.

**Comparator Declaration and use for compare**

```java

public class LengthComparator implements Comparator<MyBean>{ 
  @Override public int compare(MyBean o1, MyBean o2) { 
    int name = o1.name.compareTo(o2.name);  
        if (name != 0) {  
            return name;  
        } 
      return o1.id.compareTo(o2.id); 
    
  } 
} 
  
  //jsc is JavaSparkContext defined in the beginning during init. 
  
  JavaRDD<Integer> javaRDD = jsc.parallelize(Arrays.asList( new MyBean("abc",100,...), new MyBean("cde",200,...))); 
  //Find max value using custom implementation 
  Integer maxVal= javaRDD.max( new LengthComparator());
```

