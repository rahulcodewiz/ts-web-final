---
layout: post
title: Apache NIFI Retry & wait in custom processor
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

**Apache NIFI** provides various options to retry and wait in processors and if you need to implement a custom processor with out-of-the-box Nifi solutions for waiting on specific conditions or external-resource, then it would be a complex workflow.

Alternatively, you can implement a processor with native **Thread.sleep** and loop until the expected condition is satisfied, but I wouldn't recommend doing this as it blocks entire flow file execution.

There's another option that I am going to cover in this post using a custom Processor. It leverages the Nifi internal features to wait in asynchrounous mode without blocking processor resources. It waits until certain resource condition is met e.g. file, if the file is not available then it penalizes flow file and then transfers it on the RETRY relationship. The RETRY relationship point to self. And, this keeps running until it finds the file then it sends the incoming flow file to success.

![Nifi Retry Processor Group](/assets/images/ts/app-ex.png)

### Sample Processor :

This processor has `location of file` property and two relationships, `retry` and `success`. The `retry` is used for wait in asynchronous until file is available and then transfer to `success` relationship to next task. You can moidfy the file descriptor to any other resource. 

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
