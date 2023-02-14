---
layout: post
title: GraphQL SPQR- how to access  the native ServletRequest and Response
date: 2019-09-26 11:18:54.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- java
tags:
- graphql
- java
meta:
  _edit_last: '1'
  _ez-toc-disabled: ''
  _ez-toc-insert: ''
  _ez-toc-heading-levels: a:1:{i:4;i:4;}
  _ez-toc-alttext: ''
  _ez-toc-exclude: ''
  _yoast_wpseo_primary_category: '30'
  interface_sidebarlayout: default
  _yoast_wpseo_content_score: '60'
  _yoast_wpseo_focuskw: GraphQL-SPQR ServletRequest and Response
  _yoast_wpseo_linkdex: '27'
  _thumbnail_id: '693'
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/java/graphql-spqr-access-servletrequest-response/"
---

GraphQL SPQR is a powerful library to build graphql services using Springboot and aims to make it simple to develop GraphQL API from any Java project.


SPQR annotation directly allows us to access HTTP methods(GET/POST/DELETE/POST) and content but some times that's not enough and we need servelet object access to sprint API to customize actions e.g.

- Access all headers
- Populate new headers
- Access html Body content
- Custom renedering to Rest API handlers.


### Code snippet to access native ServletRequest object and populate header based on a condition-

<!-- /wp:paragraph -->

<!-- wp:preformatted {"className":"java"} -->

```
//GraphQL SPQR resolver
@Component
@GraphQLApi
public class SampleResolver{
    @GraphQLQuery
    public String helloworld(@GraphQLEnvironment ResolutionEnvironment env, 
@GraphQLArgument(name = "name") String name){

//If name is empty then set no data content HTTP Header   
if(name.equals("")){
    //GraphQL Global context
        DefaultGlobalContext dgc = env.dataFetchEnvironment().getContext();
       ServletWebRequest request = (ServletWebRequest) dgc.getNativeRequest();
      
       request.getResponse().setHeader(HttpStatus.NO_CONTENT.value()+"",HttpStatus.NO_CONTENT.getReasonPhrase());
        return ""; 
    }        
     return String.format("Hello: %s",name);    
        
    }
}
```


**References**


- [GraphQL SPQR](https://github.com/leangen/graphql-spqr)
- [Spring Boot](https://spring.io/projects/spring-boot)