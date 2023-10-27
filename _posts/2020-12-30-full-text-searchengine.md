---
layout: post
title: Full Text Search Engine App
date: 2020-12-30 00:00:02.000000000 -08:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Big Data
- java
- ElasticSearch
- Python
tags:
- bigdata
- java
- ElasticSearch
- Python
author:
  login: ts_ad167web
  email: rahul86s@gmail.com
  name: Rahul
  display_name: Rahul
  first_name: Rahul
  last_name: Sharma
permalink: "/bd/search-engine-elasticsearch-python/"
---

![Python Elastic](/assets/images/python_es.png)

# Building a Full-Text Search Engine with Python and ElasticSearch

In today's digital age, information retrieval is crucial, and search engines have become an integral part of our lives. Whether it's looking up information on the web or searching for specific items within a database, search engines are at the core of these operations. In this article, I will guide you through the step-by-step process of building a full-text search engine using Python and ElasticSearch.

## The "Food Recipes Search Engine" Project

This project features several advanced search functionalities, including:

1. Auto-Complete, Spell Correction, and Auto-Suggestion: Enhancing the user experience with intelligent search suggestions.
2. Full Text Search on N-Grams: Utilizing N-Grams for improved search accuracy.
3. Index Configuration: A guide to defining index configuration, including Analyzer, Filter, Tokenizer, and more.
4. Data Ingestion: A Python module to index documents into ElasticSearch.
5. Dataset for Exploration: Providing a dataset to explore the search engine's features.
6. Classification Module: Using SparkNLP+BERT for a classification module.


<iframe width="560" height="315" src="https://www.youtube.com/embed/8MrQOFWIooo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### ElasticSearch Index Configuration

The heart of any search engine application lies in its index configuration. Configuring the index depends on the specific use case and requirements. Here's an example of an ElasticSearch index configuration:

```json
curl -X PUT "localhost:9200/recipes_idx1?pretty" -H 'Content-Type: application/json' -d'
{
  "settings": {
    "index": {
      "analysis": {
        "filter": {
          "shingle": {
            "type": "shingle",
            "min_shingle_size": 2,
            "max_shingle_size": 3
          }
        },
        "analyzer": {
          "keyword_analyzer": {
            "filter": [
              "lowercase",
              "asciifolding",
              "trim", "title_ngram"
            ],
            "char_filter": [],
            "type": "custom",
            "tokenizer": "keyword"
          },
          "edge_ngram_analyzer": {
            "filter": [
              "lowercase"
            ],
            "tokenizer": "edge_ngram_tokenizer"
          },
          "edge_ngram_search_analyzer": {
            "tokenizer": "lowercase"
          },
          "trigram": {
            "type": "custom",
            "tokenizer": "standard",
            "filter": ["lowercase","shingle"]
          },
          "reverse": {
            "type": "custom",
            "tokenizer": "standard",
            "filter": ["lowercase","reverse"]
          }
        },
        "tokenizer": {
          "edge_ngram_tokenizer": {
            "type": "edge_ngram",
            "min_gram": 2,
            "max_gram": 5,
            "token_chars": [
              "letter"
            ]
          }
        }
      }
    }
  },
  "mappings": {
      "properties": {
        "title": {
          "type": "text",
          "fields": {
            "keywordstring": {
              "type": "text",
              "analyzer": "keyword_analyzer"
            },
            "edgengram": {
              "type": "text",
              "analyzer": "edge_ngram_analyzer",
              "search_analyzer": "edge_ngram_search_analyzer"
            },
            "completion": {
              "type": "completion"
            }
          },
          "analyzer": "standard"
        }
      }
    }
}'

```

[Recipe Search Elastic Search notes](https://github.com/reethified/recipes-search-engine/blob/master/es-setup/es-notes.txt)

Also, I recommend using the Kibana for exploring Elastic index features. This is amazing tool for prototyping and analysing search behaviors.

### Data Ingestion to Elastic Search:

To load data into ElasticSearch, a Python script is used. This script reads data from a JSON file, iterates over each record, and loads it into ElasticSearch. Here is an example of a data ingestion script:


[es_data_loader.py](https://github.com/reethified/recipes-search-engine/blob/master/batch/es_data_loader.py)

### Dataset for Search:

Previous step read data from this directory and load to Elastic Search.

[Dataset](https://github.com/reethified/recipes-search-engine/tree/master/dataset)


### Search engine application:

The entire application is implemented using HTML, JavaScript, and Python Flask. To explore this project further, you can refer to the respective repository and documentation.

##### Autosuggest/ Spell-check/ Spell-correction:


These features are divided into frontend and backend components. The frontend is implemented in JavaScript for a smooth user interface, and it communicates with the Python backend.

In the backend, there are controller and service layers. The controller layer handles requests from the UI and invokes the relevant service modules. All ElasticSearch operations are performed within [python class](https://github.com/reethified/recipes-search-engine/blob/master/search-engine-webapp/app/search_service.py).


For example, here's how auto-suggestion is implemented in the title field:

```python
def autosuggestTerm(query):
    esquery = json.dumps({
                "suggest": {
                    "text": query,
                    "recipes": {
                        "term": {
                            "field": "title"
                            }
                    }
                }
            })
    print("Search Query:",esquery)
    suggestRes= es.search(index=INDEX_NAME, body=esquery)
    print(suggestRes)
    return suggestRes
````

Phrase Autosuggest

```python
def autosuggestPhrase(query):
    esQuery=json.dumps({
    "suggest": {
        "text": query,
        "recipes": {
        "phrase": {
            "field": "title.trigram",
            "size": 4,
            "gram_size": 3,
            "direct_generator": [ {
            "field": "title.trigram",
            "suggest_mode": "always"
            } ],
            "highlight": {
            "pre_tag": "<em>",
            "post_tag": "</em>"
            }
        }
        }
        }
        })
    print("Search Query:",esQuery)
    suggestRes= es.search(index=INDEX_NAME, body=esQuery)
    print(suggestRes)
    return suggestRes
```

##### Search Elasticsearch from Python:

Python service class parse text sent from UI and query Elastic. Text Highlight is achived using the [Elastic feature](https://www.elastic.co/guide/en/elasticsearch/reference/current/highlighting.html) and [highlight text](https://www.w3schools.com/tags/tag_mark.asp) html tag.

e.g. 

```python

def searchEs(query):

    queryStr = str(query,'utf-8')  
    formatQuery(queryStr) 
    esQuery = json.dumps({
            "query": {
                "match": {
                    "title": queryStr
                }
            },
                "highlight" : {
                        "pre_tags" : ["<mark>"],
    "post_tags" : ["</mark>"],
        "fields" : {
            "title" : {}
        }
            }
        })
    print("Search Query:",esQuery)
    res = es.search(index=INDEX_NAME, body=esQuery)
    print("Search result:",res)
    return res
```

##### Start the Search Engine app: 

There are two options to launch the app Docker and manual bash script. Refer the [README](https://github.com/reethified/recipes-search-engine) file for docker and for non docker use the [manual script](https://github.com/reethified/recipes-search-engine/blob/master/setup_without_docker.md). 


#### Troubleshoot and suggestions:

1. Make sure all python packages are installed correctly before you launch app.
2. Few browsers need below configurations to be added ElasticSearch config file:

```Properties
 http.cors.enabled : true
 http.cors.allow-origin: "*"
 http.cors.allow-methods: OPTIONS, HEAD, GET, POST, PUT, DELETE
 http.cors.allow-headers: X-Requested-With,X-Auth-Token,Content-Type,Content-Length
 http.cors.allow-credentials: true
```


Building a full-text search engine can be a complex but highly rewarding endeavor. The "Food Recipes Search Engine" project serves as a comprehensive example of what is possible when combining Python and ElasticSearch to deliver powerful search capabilities. With this guide, you're well on your way to creating your own customized search engine tailored to your specific needs. Happy searching!