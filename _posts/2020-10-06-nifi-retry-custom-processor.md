---
layout: post
title: Apache NIFI Retry & Wait in custom processor
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
# Apache NIFI Retry & Wait in custom processor

**Apache NIFI** is a powerful data integration tool that offers a wide range of features to process, transform, and route data. One common requirement in data workflows is the ability to handle retries and wait for specific conditions to be met such as API response, DB state change or semaphore. While NiFi provides option for retrying and waiting within processors, there can be scenarios where you need a more customized approach to efficiently implement these features. In this blog post, we will explore how to implement a custom processor in NiFi to wait for specific conditions without blocking the entire flow execution.

### The Challenge of Custom Waiting

When you face a situation where you need to wait for specific conditions or external resources, a straightforward solution might be to implement a processor with a simple Thread.sleep and a loop until the expected condition is met. However, this approach can be problematic as it blocks the entire flow file execution, and system thread, leading to potential performance issues.

Solution for this is the **Custom Processors for Asynchronous Waiting** for specific conditions without blocking processor resources, we can leverage this custom processors. This processor can wait in asynchronous mode, ensuring processor cores free for other execution.


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
### Conclusion

When working with Apache NiFi, waiting for specific conditions or resources doesn't have to be a complex and resource-intensive task. Implementing a this custom processor that asynchronous waiting for any external resource. By penalizing and retrying flow files until the expected conditions are met, you can ensure that your data processing remains responsive and adaptive to changing conditions.