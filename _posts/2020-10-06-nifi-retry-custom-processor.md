---
layout: post
title: NIFI Retry in custom processor
date: 2020-10-06 04:22:02.000000000 -08:00
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
- nifi
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/apache-nifi-retry-custom-processor/"
---
#### Apache Nifi Retry in Custom Processor

**Apache NIFI** provides several options for retry/wait until expected condition is satisfied. If you have a custom processor where you need to wait on certain condition by leveraging out of the box processors then overall implementation turnout complex solution. 

Alternatively, create native **Thread.sleep** and loop until expected condition is satisfied. I wouldn't recommend doing this as it blocks entire flowfile execution.

There's 3rd option which I am going to cover in this post using a custom Processor. This sample processor keep looping until it finds the file. If the file is not available then it penalize flow-file then transfer it on RETRY relartionship. The RETRY relationship point to self. And, this keep running until it finds the file then it sends incoming flow-file to success. 


```java

public class RetrySample
         extends AbstractProcessor {
 
     public static final PropertyDescriptor FILE_PATH = new PropertyDescriptor
             .Builder().name("File Path")
             .description("file path")
             .addValidator(StandardValidators.NON_EMPTY_VALIDATOR)
             .required(true)
             .build();
 
     public static final Relationship REL_SUCCESS = new Relationship.Builder()
             .name("success")
             .description("Operation completed successfully")
             .build();
 
     public static final Relationship REL_RETRY = new Relationship.Builder()
             .name("retry")
             .description("Retry relation")
             .build();
     public static final String RETRY = "retry";
 
     private Set<Relationship> relationships;
 
     private List<PropertyDescriptor> descriptors;
 
     @Override
     protected void init(ProcessorInitializationContext context) {
         final List<PropertyDescriptor> descriptors = new ArrayList<PropertyDescriptor>();
         descriptors.add(FILE_PATH);
         this.descriptors = Collections.unmodifiableList(descriptors);
 
         final Set<Relationship> relationships = new HashSet<Relationship>();
         relationships.add(REL_SUCCESS);
         relationships.add(REL_RETRY);
         this.relationships = Collections.unmodifiableSet(relationships);
     }
 
 
     @Override
     public void onTrigger(ProcessContext context, ProcessSession session) throws ProcessException {
         FlowFile ff = session.get();
         if(ff==null){
             return;
         }
         String path = context.getProperty(FILE_PATH).getValue();
 
         if(!new File(path).exists()){
             if (!ff.getAttributes().containsKey(RETRY)){
                 session.putAttribute(ff,RETRY,"yes");
             }
             session.penalize(ff);
             session.transfer(ff,REL_RETRY);
             return;
         }else {
             if (ff.getAttributes().containsKey(RETRY) ){
                 session.removeAttribute(ff, RETRY);
             }
             session.transfer(ff,REL_SUCCESS);
         }
 
     }
     @Override
     protected List<PropertyDescriptor> getSupportedPropertyDescriptors() {
         return descriptors;
     }
 
     @Override
     public Set<Relationship> getRelationships() {
         return relationships;
     }
 }
```