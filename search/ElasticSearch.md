# What is ElasticSearch ?
* Its a nosql distributed full text database
* This database is documents based
* Build on Lucene engine and HTTP top of it
* Its Open Source, Scalable and Fast

# Why should I use it ?
* Speed: Index millions of documents.
* Relevancy & Score: Select post from blog where post like '%foo%';
* Statistics: Spot trends in your data

# Application examples:
* Blog
* Analytics
* Documents

# Installation and Configuration:

## Dependences:
* The only requirement for installing Elasticsearch is a recent version of Java.

### On Ubuntu:
1. Visit **Download Link** [https://www.elastic.co/downloads/elasticsearch](https://www.elastic.co/downloads/elasticsearch)
2. Download .deb & Install via Ubuntu Software Center
3. If you’ve installed the ```.deb``` package, then

  3.1 The ES data, plugins, bin and lib will get installed in ```/usr/share/elasticsearch```

  3.2 The ES configuration will get installed in ```/etc/elasticsearch```

  3.3 "logging.yml" provides configuration for basic logging. You can find the resulting logs in ```/var/log/elasticsearch```

4. ```sudo /etc/init.d/elasticsearch status | start | restart | stop```

### On Windows:
1. Visit **Download Link** [https://www.elastic.co/downloads/elasticsearch](https://www.elastic.co/downloads/elasticsearch)
2. Download .zip & Extract it.

## Structure
| Folder Name | Contents |
| ------------- | ------------- |
| ./bin | binary files of ES for execution |
| ./logs | Stores all the ES logs are store by default |
| ./config | Stores all the ES configuration files *.yml format |
| ./data | Stores data |

For more information visit: [https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-dir-layout.html#setup-dir-layout](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-dir-layout.html#setup-dir-layout)

## elasticsearch.yml
* cluster.name: esdemo
* node.name: esnode01

we can override either the cluster or node name. This can be done from the command line when starting Elasticsearch as follows:
```./elasticsearch --cluster.name my_cluster_name --node.name my_node_name```

Now its ready to run our ES => http://localhost:9200 => GET the response

# Plugins:
* Elastic HQ : Provides Web Interface for ES

### On Windows:
```
cd C:\elasticsearch\bin

plugin install/remove royrusso/elasticsearch-HQ

plugin install/remove mobz/elasticsearch-head

plugin install/remove elasticsearch/marvel/latest
```

### On Ubuntu
```
cd /usr/share/elasticsearch/bin/

sudo sh plugin -install/remove royrusso/elasticsearch-HQ

sudo sh plugin -install/remove mobz/elasticsearch-head

sudo sh plugin -install/remove elasticsearch/marvel/latest
```

### Run these installed plugins
```
Run http://localhost:9200/_plugin/HQ

Run http://localhost:9200/_plugin/head

Run http://localhost:9200/_plugin/marvel
```

# Concepts:

## Documents:
* ES does not stores data in rows and columns, it does not have any schema.
* It stores data in documents of JSON strings

## Data:
* Documents -> Index -> Shard1, Shard2, Shard3 ... -> Shard1 ---> nodes
* Index is like a database which are then stored across multiple shards - a logical way to divided the data in to chunks so that they can be stored across multiple servers more easily.
* Shards are then stored in 1 or more servers which are called nodes and is considers as a Cluster

## Clustering:
Simple clustering makes ES to scale horizontally, mean adding more servers to the custer so the shards can be distributed to help to balance out the load.

| Server Node  | Distribution Loading |
| ------------- | ------------- |
| 1  | L1, L2, L3, L4, L5, L6, L7, L8, L9, L10, L11, L12  |


If we add another node, the shards will automatically distributed thenself

| Server Node  | Distribution Loading |
| ------------- | ------------- |
| 1 | L1, L2, L3, L4, L5, L6 |
| 2 | L7, L8, L9, L10, L11, L12 |

If we add another node,

| Server Node  | Distribution Loading |
| ------------- | ------------- |
| 1 | L1, L2, L3, L4 |
| 2 | L5, L6, L7, L8 |
| 3 | L9, L10, L11, L12 |

## Schemas (Mapping):
Just as a relational database has schema which tells us the names of tables and columns and what datatypes they should content, ES has a schema called mapping

## Cluster Health:
GET [localhost:9200/_cat/health?v](http://localhost:9200/_cat/health?v)
GET [localhost:9200/_cat/nodes?v](http://localhost:9200/_cat/nodes?v)

[https://www.elastic.co/guide/en/elasticsearch/reference/current/_cluster_health.html](https://www.elastic.co/guide/en/elasticsearch/reference/current/_cluster_health.html)

## List all indices:

GET [localhost:9200/_cat/indices?v](http://localhost:9200/_cat/indices?v)

## Create an index (Use REST Client with PUT operation):
PUT [localhost:9200/customer?pretty](http://localhost:9200/customer?pretty) => [localhost:9200/_cat/indices?v](http://localhost:9200/_cat/indices?v)

Note: We simply append pretty to the end of the call to tell it to pretty-print the JSON response

## Index and Query a Document:
PUT [localhost:9200/customer/external/1?pretty](http://localhost:9200/customer/external/1?pretty)

```
{
  "name": "Ashwin Hegde"
}
```
Retrieve that document:

GET [localhost:9200/customer/external/1?pretty](http://localhost:9200/customer/external/1?pretty)

## Delete an index:

DELETE [localhost:9200/customer?pretty](http://localhost:9200/customer?pretty)

If we study the above commands carefully, we can actually see a pattern of how we access data in Elasticsearch. That pattern can be summarized as follows:

```
<REST Verb> <Node>:<Port>/<Index>/<Type>/<ID>
```

Note: When indexing, the ID part is optional. If not specified, Elasticsearch will generate a random ID and then use it to index the document.

## Modifying the Data:

[localhost:9200/customer/external/2?pretty](http://localhost:9200/customer/external/2?pretty)

```
{
  "name": "Kumar Kundan"
}
```

[localhost:9200/customer/external/3?pretty](http://localhost:9200/customer/external/3?pretty)

```
{
  "name": "Ajay Sajwan"
}
```

[localhost:9200/customer/external/4?pretty](http://localhost:9200/customer/external/4?pretty)

```
{
  "name": "Saju S"
}
```

## Updating Documents:

Note: Though that Elasticsearch does not actually do in-place updates under the hood. Whenever we do an update, Elasticsearch deletes the old document and then indexes a new document with the update applied to it in one shot.

POST [localhost:9200/customer/external/1/_update?pretty](http://localhost:9200/customer/external/1/_update?pretty)

```
{
  "doc": { "name": "Saju Sasidharan" }
}
```

## Deleting Documents:

DELETE [localhost:9200/customer/external/2?pretty](http://localhost:9200/customer/external/2?pretty)

## Batch Processing:

POST [localhost:9200/customer/external/_bulk?pretty](http://localhost:9200/customer/external/_bulk?pretty)

```
{"index":{"_id":"1"}}
{"name": "Ashwin Hegde" }
{"index":{"_id":"2"}}
{"name": "Kumar Kundan" }
{"index":{"_id":"3"}}
{"name": "Ajay Sajwan" }
{"index":{"_id":"4"}}
{"name": "Saju Sasidharan" }

```

This example updates the first document (ID of 1) and then deletes the second document (ID of 2) in one bulk operation:

POST [localhost:9200/customer/external/_bulk?pretty](http://localhost:9200/customer/external/_bulk?pretty)

```
{"update":{"_id":"1"}}
{"doc": { "name": "Ashwin Hegde becomes Ashwin M Hegde" } }
{"delete":{"_id":"3"}}
```
