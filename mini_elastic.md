
# SimpleElastic
A simple elasticsearch like search engine of your own.

Before starting on this assignment you will need to do a little bit of reading.
Get a context on following things
-  full text search
-  indexing (inverted index)
-  term frequency (aka TF) 
-  inverse document frequency (aka IDF)
- REST

Follow the links below to give it a read. (You are free to explore on your own too)
- [quick elasticsearch tutorial](http://joelabrahamsson.com/elasticsearch-101/)
- [inverted index](https://www.elastic.co/guide/en/elasticsearch/guide/current/inverted-index.html)
- [TF & IDF](https://en.wikipedia.org/wiki/Tf%E2%80%93idf)
- [getting started with REST](http://www.andrewhavens.com/posts/20/beginners-guide-to-creating-a-rest-api/)


## The Assignment


Create a lightweight search engine which

- indexes documents into inverted index and saves them on disk for searching on them later
- allows searching on previously indexed items; search works as follows: 
        1) break every search query into different terms (words/token)
        2) look up every term on inverted index and build the result set
        3) modify the rank of results using TF (Extra points if you also implement IDF)
- exposes 2 REST API endpoints; one for indexing data and another for searching

### Example

An api endpoint for indexing

```
POST /index
{
"id": "1",
"title": "quick fox",
"data": "A fox is usually quick and brown."
}

200 OK

POST /index
{
"id": "2",
"title": "lazy dog"
"data": "A quick brown fox jumped over lazy dog. A fox is always jumping."
}

200 OK
```

An api endpoint for search
```
GET /search?q=quick%20fox

[
{
"id": "1",
"title": "quick fox",
"data": "A fox is usually quick and brown."
},
{
    "id": "2",
    "title": "lazy dog"
    "data": "A quick brown fox jumped over lazy dog. A fox is always jumping."
}]
```

### Directions

- you can use any programming language of your choice
- you should design your solution keeping scalability in mind, a search engine is usually scalable to terrabytes of data
- call us if you have any trouble understading anything

