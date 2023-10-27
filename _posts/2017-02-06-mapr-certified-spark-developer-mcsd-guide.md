---
layout: post
title: Mapr Certified Spark Developer (MCSD) guide
date: 2017-02-06 01:20:23.000000000 -08:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Big Data
tags:
- java
- spark
meta:
  _edit_last: '1'
  _oembed_c5eecd3afe9fd0fda769b63a4c02732d: "{{unknown}}"
  interface_sidebarlayout: default
  _yoast_wpseo_content_score: '30'
  _yoast_wpseo_primary_category: '6'
  dsq_thread_id: '5524901644'
  _yoast_wpseo_focuskw_text_input: Mapr Certified Spark Developer (MCSD) guide,
    mock questions, suggestions about spark Databricks and cloudera certifications
  _yoast_wpseo_focuskw: Mapr Certified Spark Developer (MCSD) guide dumps, mock questions,
    suggestions about spark Databricks and cloudera certifications
  _yoast_wpseo_linkdex: '56'
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/mapr-certified-spark-developer-mcsd-guide/"
---
[![mcsd-img]({{ site.baseurl }}/assets/images/mcsd-img-150x150.png)](http://www.techsquids.com/wp-content/uploads/2017/02/mcsd-img.png)

# Tips to prepare Spark Certification

After a couple of months preparation, I am Spark Certified Developer. In this blog post, I will provide you with some essential tips to prepare for the MapR Spark Certification. Spark Certification is a valuable credential for anyone looking to prove their expertise in Apache Spark. Whether you're a seasoned Spark developer or just starting your journey, this certification can help you stand out in the competitive field of big data and analytics. 

## Why Mapr for Spark Certification?

Before we dive into the preparation tips, let's address the question of why you should consider the MapR Spark Certification. Spark certifications are offered by various organizations, including Databricks, MapR, Hortonworks, and Cloudera. While all these certifications are valuable, MapR and Databricks are among the most popular choices. If your organization uses MapR distribution, it makes sense to choose the MapR certification.

To help you understand the scope of the certification, here are the major topics covered in the exam:
  
| index | topic | time slot

(in minutes)

 | percentage |
| 1 | Load and inspect data. | 30 | 24% |
| 2 | Build an Apache spark application. | 15 | 14% |
| 3 | Working with Pair RDD. | 20 | 17% |
| 4 | Monitor Spark application. | 15 | 14% |
| 5 | Working with Data frames. | 12 | 10% |
| 6 | Spark Streaming | 12 | 10% |
| 7 | Advance Machine Learning programming. | 12 | 10% |
| | | | |

The certification exam is divided into different sections, each with a fixed number of questions. Allocate time strategically for each section. It's important to remember that once you move on to the next section, you cannot go back, so plan accordingly.

**Pointers to start Prepration:**

- I would suggest start by thoroughly studying the [**apache spark wiki**](http://spark.apache.org/docs/latest/programming-guide.html). This resource covers all the topics in-depth and is an excellent starting point for your preparation.
- Complete all&nbsp;Mapr spark tutorials and videos:
  - [http://learn.mapr.com/dev-360-apache-spark-essentials](http://www.techsquids.com/wp-admin/_wp_link_placeholder)
  - [http://learn.mapr.com/dev-361-build-and-monitor-apache-spark-applications](http://learn.mapr.com/dev-361-build-and-monitor-apache-spark-applications)
  - [http://learn.mapr.com/dev-362-create-data-pipelines-using-apache-spark](http://learn.mapr.com/dev-362-create-data-pipelines-using-apache-spark)

- Many of the exam questions are in Scala and often include code snippets. Make sure to practice Scala basics to tackle these questions effectively.

**Useful tips:**

- The first section of the exam places a significant emphasis on Pair RDD. Practice operations like groupByKey, reduceByKey, and combineByKey. Understand the performance differences between these operations.
  - GroupByKey vs ReduceByKey vs combineBy which one is faster?&nbsp;**[ReduceBykey is faster](https://databricks.gitbooks.io/databricks-spark-knowledge-base/content/best_practices/prefer_reducebykey_over_groupbykey.html)**

  - Be prepared to differentiate between reduce and fold and know the output of the rdd.collect method:
```
sum = data.combineByKey(value=> (value, 1),
                             (x, value)=> (x[0] + value, x[1] + 1),
                             (x, y): (x[0] + y[0], x[1] + y[1]))
averageByKey = sum.map((label, (value_sum, count))=> (label, value_sum / count))
```

- Difference between reduce & fold.
- What's output of&nbsp; **rdd.collect** &nbsp; method?

- Get comfortable with using accumulators and broadcast variables, as you may encounter questions related to these concepts in the exam.

```
val accum = sc.longAccumulator("My Accumulator")
val rdd=sc.parallelize(1 to N,X)
question 1:
rdd.foreach(x => accum.add(1)) 
accum
//result N
question 2:
rdd.foreEachParition(s=>{accum.add(1);s})
accumulator
//result X
```

- Supervised vs. Unsupervised Learning: Understand the difference between supervised and unsupervised learning. Familiarize yourself with Spark's machine learning algorithms and when to use them. [Spark Wiki](https://spark.apache.org/docs/latest/ml-guide.html)
  - Supervised
    - regression
      - Linear regression
      - logistic regression
    - classification
      - naive baise
      - SVM
      - readon decision forest.
  - Unsupervised:
    - Dimension reduction.
    - PCA
    - SVD

- Read about MLlib data types and know what values are contained in a LabeledPoint.

- Practice Spark Streaming, especially sliding window and window operations. Make sure you can correctly implement sliding window operations.

```
val lines = ssc.socketTextStream(args(0), args(1).toInt,.........) val words = lines.flatMap(\_.split(" ")) val wordCounts = words.map(x =\> (x, 1))  val runningCountStream = wordCounts.reduceByKeyAndWindow( (x: Int, y: Int) =\> x + y, (x: Int, y: Int) =\> x - y, windowSize, slidingInterval, 2, (x: (String, Int)) =\> x.\_2 != 0) runningCountStream.print() ssc.start() ssc.awaitTermination()
```

- Fault Tolerance and Back Pressure: Understand how fault tolerance is achieved in Spark Streaming and how back pressure is managed in streaming applications.

- Tuning Spark Jobs: Learn how to tune Spark jobs for optimal performance. You can find valuable information on this topic **[here](https://blog.cloudera.com/blog/2015/03/how-to-tune-your-apache-spark-jobs-part-1/).**

- Spark UI: Be ready to answer questions related to the Spark UI, such as the meaning of stages, job progress status, and the number of tasks or phases in a given code snippet.
  - What is the meaning of stages, job and job progress status(M+N/N) in spark UI that you find **[here&nbsp;](http://stackoverflow.com/questions/30245180/what-do-the-numbers-on-the-progress-bar-mean-in-spark-shell/30250120)**
  - How many tasks/phases for given code snippet.
```
val data=sc.parallelize(....).map(s **=\>** (s, 1))data.cache()data.reduceByKey( **\_** + **\_** )….data.foreach..groupBy
```

- Dataset: Understand the different methods for loading data and creating Dataset in Spark.? 

  - jdbc
  - load hdfs files - hadoop rdd.
  - text file- sc.textfile
  - sequence file- sc.sequenceFile.
  - whole text file- sc.wholeTextFile
  - Object File- sc.objectFile
  - DataFrames:
    - Read-
      - session.read.json
      - sc.parallelize(..).map(s=\> Object).toDS
      - sc.parallelize(..).map(s=\> Object).toDF
      - sqlContext.load("....")
      - sqlContext.read.option("",true).parquet(" ......")
    - Write: Modes- error, append, overwrite, ignore
      - df.write.save(".... ")
      - df.write.parquet("....")
      - df.write.format("parqueet").save("....")
- Read all DF operations: select, group, filter ...
  - df.filter("xyz\_col\>100")
  - df.select("name").distinct.show

- DataFrame Operations: familiarze with common DataFrame operations, including filtering, selecting, grouping, and more.

- Data Frame Show, Limit, and Take: Differentiate between show, limit, and take methods when working with DataFrames.

It's important to note that the exam does not include questions related to GraphX.

In conclusion, the preparation is key to success in the Spark Certification exam. By following these tips and dedicating sufficient time to each topic, you'll be well-prepared to showcase your expertise. Best of luck with your certification journey, and feel free to reach out if you have any questions or need further assistance. You've got this!

