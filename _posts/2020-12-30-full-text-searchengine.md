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

This article covers step by step guide to build a full text Search Engine using the Python and ElasticSearch. 
#### I use "Food Recipes Search Engine" project for this guide and this project features are:

- Auto-complete, Spell correction and Auto-suggestion in the search bar achieved
- Full Text Search on N-Grams
- Guide to define index configuration i.e. Analyzer, Filter, Tokenizer etc
- Module to index document using Python.
- Dataset to explore search feature
- A Classification module using the SparkNLP+BERT

<iframe width="560" height="315" src="https://www.youtube.com/embed/8MrQOFWIooo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



#### ElasticSearch Index Configuration:

The most crucial part of any Search Engine app is finding the suitable Index configuration and it largely depends on individual usecase need. It is difficult to generalize it. Primarily the configuration involves discovery of Analyzer, Filter, and Tokenizer for the index fields and here are what I implemented for this Search Engine:


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
#### Data Ingestion to Elastic Search:

I used python to build the data ingestion pipeline. Data ingestion script loads data from json file then iterate over each record and finally, it loads to Elastic Search.

[es_data_loader.py](https://github.com/reethified/recipes-search-engine/blob/master/batch/es_data_loader.py)

#### Dataset for Search:

Previous step read data from this directory and load to Elastic Search.

[Dataset](https://github.com/reethified/recipes-search-engine/tree/master/dataset)

#### Search engine application:

The overall application is implemented using html, javascript and Python flask. Explore further [repository](https://github.com/reethified/recipes-search-engine/tree/master/search-engine-webapp) and post in case of any queries.
1. ##### Autosuggest/ Spell-check/ Spell-correction:

This feature is devided into two features, frontend which is implemented in Javascript and backend is in Python. Frontend is primarily used for UI experience and each UI query is renderded using Javascript/AJAX to backend Python service.

The backend service has a controller and service layers. Controller layer accepts calls from UI and invoke respective service module. All ElasticSearch operations are implemented in [python class](https://github.com/reethified/recipes-search-engine/blob/master/search-engine-webapp/app/search_service.py)

E.g. Autosuggest implementation in <b>title</b> field:

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

2. ##### Search Elasticsearch from Python:

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

3. ##### Start the Search Engine app: 

There are two options to launch the app Docker and manual bash script. Refer the [README](https://github.com/reethified/recipes-search-engine) file for docker and for non docker use the [manual script](https://github.com/reethified/recipes-search-engine/blob/master/setup_without_docker.md). 


#### Troubleshoot and suggestions:

1. Make sure all python packages are installed correctly.
2. Few browsers need below configurations to be added ElasticSearch config file:

```Properties
 http.cors.enabled : true
 http.cors.allow-origin: "*"
 http.cors.allow-methods: OPTIONS, HEAD, GET, POST, PUT, DELETE
 http.cors.allow-headers: X-Requested-With,X-Auth-Token,Content-Type,Content-Length
 http.cors.allow-credentials: true
```