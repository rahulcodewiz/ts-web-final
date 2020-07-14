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
  _yoast_wpseo_focuskw_text_input: Mapr Certified Spark Developer (MCSD) guide dumps,
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

**Tips to prepare Mapr Spark Certification-**

Yes finally I did it&nbsp;:) After couple of months preparation I am finally Mapr certified spark developer. I wrote the exam on Nov 2016. Spark certification is sponsored by many organizations DataBricks, Mapr, Hortonworks, Cloudera... the DataBricks and Mapr are the popular one, I am bias towards both providers and I chose to Mapr because my organization is using Mapr distribution.

If you are planning to write MCSD then read [**apache spark wiki**](http://spark.apache.org/docs/latest/programming-guide.html) thoroughly and have hands on experience too.

**The major topics MCSD covers:**  
  
http://learn.mapr.com/free-spark-certification-study-guide/60807

- Load and inspect data.
- Build an Apache spark application.
- Working with Pair RDD.
- Monitor Spark application.
- Working with Data frames.
- Spark Streaming
- Advance Machine Learning programming.

**Pointers to start Prepration:**

- The Apache spark wiki has covered all the topics in depth, throughly study it.
- Complete all&nbsp;Mapr spark tutorials and videos:
  - [http://learn.mapr.com/dev-360-apache-spark-essentials](http://www.techsquids.com/wp-admin/_wp_link_placeholder)
  - [http://learn.mapr.com/dev-361-build-and-monitor-apache-spark-applications](http://learn.mapr.com/dev-361-build-and-monitor-apache-spark-applications)
  - [http://learn.mapr.com/dev-362-create-data-pipelines-using-apache-spark](http://learn.mapr.com/dev-362-create-data-pipelines-using-apache-spark)
- The overall exam is divided into set of topics listed above, with 2 hrs time slot for all the topics. Each topic has fixed set of questions so assign time slot(in minutes) for each section, the reason is as you move to next topic you are not allowed to browse previous topic and don't assign uniformly **&nbsp;** time slot for each topic because few of the topics has less number of questions than others.

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

- Most of the questions were in scala given with code snippet, so you practice scala basics.

**Useful tips:**

- In first section majority of the questions based on PairRDD, practice all pairRDD: groupByKey, reduceByKey, combineByKey:
  - GroupByKey vs ReduceByKey vs combineBy which one is faster?&nbsp;**[ReduceBykey is faster](https://databricks.gitbooks.io/databricks-spark-knowledge-base/content/best_practices/prefer_reducebykey_over_groupbykey.html)**
  - Average for key/value, what value below code will produce with given datasets:
```
sum = data.combineByKey(value=> (value, 1),
                             (x, value)=> (x[0] + value, x[1] + 1),
                             (x, y): (x[0] + y[0], x[1] + y[1]))
averageByKey = sum.map((label, (value_sum, count))=> (label, value_sum / count))
```
- Difference between reduce & fold.
- What's output of&nbsp; **rdd.collect** &nbsp; method?
- Practice accumulator and broadcast variables:

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

- Difference between supervised & unSupervised learning. Which one is unsupervised learning algorithm with below options? [Spark Wiki](https://spark.apache.org/docs/latest/ml-guide.html)
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
- Read&nbsp;MLLib datatypes. What type of value LabeledPoint contains?&nbsp;double.
- Practice Streaming&nbsp; sliding window and window operations, find out the correct implication of sliding window.

```
val lines = ssc.socketTextStream(args(0), args(1).toInt,.........) val words = lines.flatMap(\_.split(" ")) val wordCounts = words.map(x =\> (x, 1))   val runningCountStream = wordCounts.reduceByKeyAndWindow( (x: Int, y: Int) =\> x + y, (x: Int, y: Int) =\> x - y, windowSize, slidingInterval, 2, (x: (String, Int)) =\> x.\_2 != 0) runningCountStream.print() ssc.start() ssc.awaitTermination()
```

- How fault tolerant is achieved is spark streaming.
- How back pressure is achieved in stremaing.
- Read how to tune spark job? Read **[here](https://blog.cloudera.com/blog/2015/03/how-to-tune-your-apache-spark-jobs-part-1/).**
- All spark UI questions were easy,
  - What is the meaning of stages, job and job progress status(M+N/N) in spark UI? Read **[here&nbsp;](http://stackoverflow.com/questions/30245180/what-do-the-numbers-on-the-progress-bar-mean-in-spark-shell/30250120)**
  - How many tasks/phases for given code snippet.
```
val data=sc.parallelize(....).map(s **=\>** (s, 1))data.cache()data.reduceByKey( **\_** + **\_** )….data.foreach..groupBy
```
- What are the different ways to load data and create dataframes? \*\*\*\*\*.
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
- Difference between data frame show, limit & take.
- Exam doesn't include graphX.

&nbsp;

Should you need any further assistance or have any queries, please comment!  
Wish you all the best for your exam.

