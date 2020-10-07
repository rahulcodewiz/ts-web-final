---
layout: post
title: Apache Spark Operations  implementation in Java
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
<!-- wp:image {"id":627,"align":"center"} -->

<figure class="aligncenter"><img src="%7B%7B%20site.baseurl%20%7D%7D/assets/images/spark-and-java-8.png" alt="Spark with Java" class="wp-image-627"><br>
<figcaption>
</figcaption>
</figure>

<!-- /wp:image -->

<!-- wp:heading {"level":4} -->

#### How to Use non-serializable **classes** in Spark closures-

<!-- /wp:heading -->

<!-- wp:paragraph -->

Spark closures, objects must be serializable otherwise spark engine throws 'NotSerializableException'. You will often come across the situation when you can't change the actual class implementation. Resolve this error using the Kryo.

<!-- /wp:paragraph -->

<!-- wp:block {"ref":651} /-->

<!-- wp:heading {"level":4} -->

#### **Register classes as serializable in SparkContent-**

<!-- /wp:heading -->

<!-- wp:quote -->

> `//Exact exception spark throws when class is not serialize `
> 
> `java.io.NotSerializableException: com.ts.blog.batch.serialize.ABean Serialization stack: - object not serializable (class: com.ts.blog.batch.serialize.ABean, value: com.ts.blog.batch.serialize.ABean@27f71dca)`

<!-- /wp:quote -->

<!-- wp:preformatted -->

```java
/\*\* \* Create Custom KryoRegistrator implementation \*/ **public class** CustomKKryoRegistrator **implements** org.apache.spark.serializer.KryoRegistrator{ @Override **public void** registerClasses(Kryo kryo) { kryo.register(ABean. **class** ); //Register non serialize classes } } //Register Kryo in SparkConf- sparkConf.set( **"spark.kryo.registrar"** ,CustomKKryoRegistrator. **class**.getName());
```

<!-- /wp:preformatted -->

<!-- wp:heading {"level":4} -->

#### `Create Dataset using Encoder- `

<!-- /wp:heading -->

<!-- wp:preformatted -->

```java
**import** org.apache.spark.sql.Encoder; **import** org.apache.spark.sql.Encoders;Encoder<Employee> employeeEncoder = Encoders._`bean`_(Employee.class); Dataset<Employee> dataset= session.read().json(employee.json).as(employeeEncoder); **public class** Employee { **private** Integer **id** ; **private** String **name** ; }
```

<!-- /wp:preformatted -->

<!-- wp:quote -->

> cat employee.json  
> { **"id"** : 100, **"name"** : **"xyz"** }   
> { **"id"** : 200, **"name"** : **"prq"** }

<!-- /wp:quote -->

<!-- wp:heading {"level":4} -->

#### Find out the **Max value from Dataset column-**

<!-- /wp:heading -->

<!-- wp:preformatted -->

```java
Row max = dataset.agg(org.apache.spark.sql.functions._`max`_(dataset.col( **`"id"`** ))).as( **`"max"`** ).head();
System. **_`out`_**.println(max);
```

<!-- /wp:preformatted -->

<!-- wp:heading {"level":4} -->

#### Define custom **UDF Function with SparkSession**

<!-- /wp:heading -->

<!-- wp:code -->

```java
Dataset<Long> ds= SessionRegistry.session.range(1,20);

        ds.sparkSession().udf().register("add100",(Long l)->l+100,org.apache.spark.sql.types.DataTypes.LongType);

        ds.show();
        ds.registerTempTable("allnum");

        ds.sparkSession().sql("select add100(id) from allnum").show();
```

<!-- /wp:code -->

<!-- wp:heading {"level":4} -->

#### **Custom Property file in Spark** -

<!-- /wp:heading -->

<!-- wp:paragraph -->

Create property file- e.g. job.properties

<!-- /wp:paragraph -->

<!-- wp:quote -->

> custom.prop=xyz

<!-- /wp:quote -->

<!-- wp:code -->

```java
//Supply Propty to spark using spark-submit
${SPARK_HOME}/bin/spark-submit --files job.properties
//Read file in drive

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

<!-- /wp:code -->

<!-- wp:heading {"level":4} -->

#### **Accumulator** implementation-

<!-- /wp:heading -->

<!-- wp:preformatted -->

```java
_/\*\* \* The sample accumulator to store set of string values \*/_ **class** CustomAccumulator **extends** AccumulatorV2\<String,Set\<String\>\>{ Set\<String\> **myval** = **new** HashSet\<\>(); @Override **public void** merge(AccumulatorV2\<String, Set\<String\>\> other) { other.value().stream().forEach(val-\> **myval**.add(val)); } @Override **public boolean** isZero() { **return myval**.size()==0; } @Override **public** AccumulatorV2\<String, Set\<String\>\> copy() { **return this** ; } @Override **public void** reset() { **myval**.clear(); } @Override **public void** add(String v) { **myval**.add(v); } @Override **public** Set\<String\> value() { **return myval** ; } } //Register accumulator to SparkContext. jsc object is created during init section (begining) AccumulatorV2 accumulatorV2 = **new** CustomAccumulator();_jsc_.sc().register(accumulatorV2); //Use accumulatorV2 like normal accumulator
```

<!-- /wp:preformatted -->

<!-- wp:heading {"level":4} -->

#### Custom **Comparator implementation for the compare operations-**

<!-- /wp:heading -->

<!-- wp:preformatted -->

```java
/\*\* \* Comparator for Integer \*/ 
public **class** LengthComparator **implements** Comparator\<Integer\>{ 
  @Override **public int** compare(Integer o1, Integer o2) { **return** 0; 
  } 
  } 
  //jsc is JavaSparkContext defined in the beginning during init. 
  JavaRDD\<Integer\> javaRDD = _jsc_.parallelize(Arrays._asList_( **new** Integer[]{100,20,10,1020,100})); 
  //Find max value using custom implementation 
  Integer maxVal= javaRDD.max( **new** LengthComparator());
```

<!-- /wp:preformatted -->

<!-- wp:paragraph -->

<!-- /wp:paragraph -->

