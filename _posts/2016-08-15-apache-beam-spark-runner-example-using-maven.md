---
layout: post
title: Apache Beam Spark Runner example using Maven
date: 2016-08-15 11:39:47.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Big Data
tags:
- apache Beam
- hadoop
- java
- spark
meta:
  _edit_last: '1'
  interface_sidebarlayout: default
  _yoast_wpseo_content_score: '30'
  _yoast_wpseo_primary_category: '6'
  _yoast_wpseo_focuskw_text_input: Apache Beam Spark Runner example using Maven eclipse
  _yoast_wpseo_focuskw: Apache Beam Spark Runner example using Maven eclipse
  _yoast_wpseo_title: Apache Beam Spark Runner example using Maven
  _yoast_wpseo_linkdex: '67'
  _yoast_wpseo_metadesc: Steps by step guide to create Apache Beam Spark Runner example
    using Maven eclipse.
  dsq_thread_id: '5066596040'
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/apache-beam-spark-runner-example-using-maven/"
---
In this post I will share how to create Apache Beam Spark Runner project using Maven.

Tools/ Frameworks used:

- Java 8
- Apache Spark
- Maven
- Intellij
- Apache Beam

  
1. Add Cloudera repository in maven settings.xml

```
<repository>
      <id>cloudera</id>
      <url>https://repository.cloudera.com/artifactory/cloudera-repos/</url>
    </repository>
```

full settings.xml file:

```
<settings></settings><profiles><profile>
      <id>cld</id>

      <repositories>
       <repository>
      <id>cloudera</id>
      <url>https://repository.cloudera.com/artifactory/cloudera-repos/</url>
    </repository>
     <repository>
      <id>mvn</id>
      <url>http://repo1.maven.org/maven2/</url>
    <release>
    	<enabled>true</enabled>
    </release>
    <snapshots>
    	<enabled>true</enabled>
    </snapshots>
    </repository>
      </repositories>
      
    </profile> </profiles> <activeprofiles>
    <activeprofile>cld</activeprofile>
  </activeprofiles>
```

2. Create maven project

```
mvn archetype:generate -DgroupId=com.ts.spark -DartifactId=beam-spark -DarchetypeArtifactId=maven-archetype-quickstart
```

3. Add Below dependencies to pom file:

```
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemalocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelversion>4.0.0</modelversion>

	<groupid>com.ts.spark</groupid>
	<artifactid>beam-spark</artifactid>
	<version>0.0.1-SNAPSHOT</version>
	<packaging>jar</packaging>

	<name>beam-spark</name>
	<url>http://maven.apache.org</url>

	<properties>
        <project.build.sourceencoding>UTF-8</project.build.sourceencoding>
        <project.reporting.outputencoding>UTF-8</project.reporting.outputencoding>
        <java.version>1.7</java.version>
        <spark.version>1.5.2</spark.version>
        <google-cloud-dataflow-version>1.3.0</google-cloud-dataflow-version>
    </properties>

	<dependencies>
		<dependency>
			<groupid>org.testng</groupid>
			<artifactid>testng</artifactid>
			<version>6.8</version>
			<scope>test</scope>
		</dependency>
		<dependency>
			<groupid>com.cloudera.dataflow.spark</groupid>
			<artifactid>spark-dataflow</artifactid>
			<version>0.4.2</version>
		</dependency>
		<dependency>
            <groupid>org.apache.spark</groupid>
            <artifactid>spark-core_2.10</artifactid>
            <version>${spark.version}</version>
        </dependency>
        <dependency>
            <groupid>org.apache.spark</groupid>
            <artifactid>spark-streaming_2.10</artifactid>
            <version>${spark.version}</version>
            <scope>provided</scope>
        </dependency>
        <dependency>
            <groupid>com.google.cloud.dataflow</groupid>
            <artifactid>google-cloud-dataflow-java-sdk-all</artifactid>
            <version>${google-cloud-dataflow-version}</version>
            <exclusions>
                <!-- Use Hadoop/Spark's backend logger -->
                <exclusion>
                    <groupid>org.slf4j</groupid>
                    <artifactid>slf4j-jdk14</artifactid>
                </exclusion>
            </exclusions>
        </dependency>
        <dependency>
            <groupid>com.google.cloud.dataflow</groupid>
            <artifactid>google-cloud-dataflow-java-examples-all</artifactid>
            <version>${google-cloud-dataflow-version}</version>
            <exclusions>
                <!-- Use Hadoop/Spark's backend logger -->
                <exclusion>
                    <groupid>org.slf4j</groupid>
                    <artifactid>slf4j-jdk14</artifactid>
                </exclusion>
            </exclusions>
        </dependency>
       	</dependencies>

    <build>
        <plugins>
            <plugin>
                <groupid>org.apache.maven.plugins</groupid>
                <artifactid>maven-compiler-plugin</artifactid>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>

        </plugins>

    </build>
</project>
```

4. Function to extract words:

```
static class ExtractWordsFn extends DoFn<string string> {
		private final Aggregator<long long> emptyLines =
				createAggregator("emptyLines", new Sum.SumLongFn());

		@Override
		public void processElement(ProcessContext c) {
			if (c.element().trim().isEmpty()) {
				emptyLines.addValue(1L);
			}

			// Split the line into words.
			String[] words = c.element().split("[^a-zA-Z']+");

			// Output each word encountered into the output PCollection.
			for (String word : words) {
				if (!word.isEmpty()) {
					c.output(word);
				}
			}
		}
	}</long></string>
```

5. Count words function:

```
public static class CountWords extends PTransform<pcollection>, PCollection<string>&gt; {
		@Override
		public PCollection<string> apply(PCollection<string> lines) {

			// Convert lines of text into individual words.
			PCollection<string> words = lines.apply(
					ParDo.of(new ExtractWordsFn()));

			// Count the number of times each word occurs.
			PCollection<kv long>&gt; wordCounts =
					words.apply(Count.<string>perElement());

			// Format each word and count into a printable string.
			return wordCounts.apply(ParDo.of(new FormatCountsFn()));
		}

	}</string></kv></string></string></string></string></pcollection>
```

6. Format output:

```
private static class FormatCountsFn extends DoFn<kv long>, String&gt; {
		@Override
		public void processElement(ProcessContext c) {
			c.output(c.element().getKey() + ": " + c.element().getValue());
		}
	}</kv>
```

7. Driver Method:

```
public class WordCount { private static final String[] WORDS\_ARRAY = { "hi there", "hi", "hi sue bob", "hi sue", "", "bob hi"}; private static final List<string> WORDS = Arrays.asList(WORDS_ARRAY);
	private static final Set<string> EXPECTED_COUNT_SET =
			ImmutableSet.of("hi: 5", "there: 1", "sue: 2", "bob: 2");

	public static void main(String[] args) {
		SparkPipelineOptions options = SparkPipelineOptionsFactory.create();

		options.setRunner(SparkPipelineRunner.class);
		Pipeline p = Pipeline.create(options);
		PCollection<string> output=p.apply(Create.of(WORDS)).setCoder(StringUtf8Coder.of()).apply(new CountWords());
		SparkPipelineRunner runner = SparkPipelineRunner.create(options);
		EvaluationResult result = runner.run(p);
		DataflowAssert.that(output).containsInAnyOrder(EXPECTED_COUNT_SET);
			}}</string></string></string>
```

8. Full Driver class:

```
package com.ts.beam.spark; import com.cloudera.dataflow.spark.EvaluationResult; import com.cloudera.dataflow.spark.SparkPipelineOptions; import com.cloudera.dataflow.spark.SparkPipelineOptionsFactory; import com.cloudera.dataflow.spark.SparkPipelineRunner; import com.google.cloud.dataflow.sdk.Pipeline; import com.google.cloud.dataflow.sdk.coders.StringUtf8Coder; import com.google.cloud.dataflow.sdk.io.TextIO; import com.google.cloud.dataflow.sdk.options.PipelineOptions; import com.google.cloud.dataflow.sdk.repackaged.com.google.common.collect.ImmutableSet; import com.google.cloud.dataflow.sdk.testing.DataflowAssert; import com.google.cloud.dataflow.sdk.transforms.\*; import com.google.cloud.dataflow.sdk.util.SystemDoFnInternal; import com.google.cloud.dataflow.sdk.values.KV; import com.google.cloud.dataflow.sdk.values.PCollection; import java.nio.channels.Pipe; import java.util.Arrays; import java.util.List; import java.util.Set; public class WordCount { private static final String[] WORDS\_ARRAY = { "hi there", "hi", "hi sue bob", "hi sue", "", "bob hi"}; private static final List<string> WORDS = Arrays.asList(WORDS_ARRAY);
	private static final Set<string> EXPECTED_COUNT_SET =
			ImmutableSet.of("hi: 5", "there: 1", "sue: 2", "bob: 2");

	public static void main(String[] args) {
		SparkPipelineOptions options = SparkPipelineOptionsFactory.create();

		options.setRunner(SparkPipelineRunner.class);
		Pipeline p = Pipeline.create(options);
		PCollection<string> output=p.apply(Create.of(WORDS)).setCoder(StringUtf8Coder.of()).apply(new CountWords());
		SparkPipelineRunner runner = SparkPipelineRunner.create(options);
		EvaluationResult result = runner.run(p);
		DataflowAssert.that(output).containsInAnyOrder(EXPECTED_COUNT_SET);

	}

	static class ExtractWordsFn extends DoFn<string string> {
		private final Aggregator<long long> emptyLines =
				createAggregator("emptyLines", new Sum.SumLongFn());

		@Override
		public void processElement(ProcessContext c) {
			if (c.element().trim().isEmpty()) {
				emptyLines.addValue(1L);
			}

			// Split the line into words.
			String[] words = c.element().split("[^a-zA-Z']+");

			// Output each word encountered into the output PCollection.
			for (String word : words) {
				if (!word.isEmpty()) {
					c.output(word);
				}
			}
		}
	}
	public static class CountWords extends PTransform<pcollection>, PCollection<string>&gt; {
		@Override
		public PCollection<string> apply(PCollection<string> lines) {

			// Convert lines of text into individual words.
			PCollection<string> words = lines.apply(
					ParDo.of(new ExtractWordsFn()));

			// Count the number of times each word occurs.
			PCollection<kv long>&gt; wordCounts =
					words.apply(Count.<string>perElement());

			// Format each word and count into a printable string.
			return wordCounts.apply(ParDo.of(new FormatCountsFn()));
		}

	}
	private static class FormatCountsFn extends DoFn<kv long>, String&gt; {
		@Override
		public void processElement(ProcessContext c) {
			c.output(c.element().getKey() + ": " + c.element().getValue());
		}
	}

}
</kv></string></kv></string></string></string></string></pcollection></long></string></string></string></string>
```


### References
- (Beam setup wiki)[https://beam.apache.org/get-started/quickstart/java/]