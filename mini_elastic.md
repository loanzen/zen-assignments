
# SimpleElastic
A simple elasticsearch like search engine of your own.

Before starting on this assignment you will need to do a little bit of reading (unless off course, if you are already familiar with these).

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

- indexes documents into inverted index and saves them on disk for searching on them later. You have to design your own algorithm and system to store and cannot use any existing database system
- allows searching on previously indexed items; search works as follows: 
        1) break every search query into different terms (words/token)
        2) look up every term on inverted index and build the result set
        3) modify the rank of results using TF (Extra points if you also implement IDF)
- exposes 2 REST API endpoints; one for indexing data and another for searching
- along with normal search, it should also have functionality to do `phrase queries`. A phrase query does a search based on the phrases instead of individual term based search. ie "fox brown" should match documents with fox and brown that appears together
- bonus point: Allow mentioning which field to be used for searching, ie if the document contains title and content, then you must be able to specify that query the string only in title field.
- bonus point: add caching for the phrase based queries

While designing this, you need to think about how would this search engine scale if you had million of documents to index and search. Think about how would you structure and store the document in file system, also think about how would you keep it in memory and access it at the time of querying. You might also need to think about how would you make this system distributed, ie  having multiple machines working together to index and search.

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


GET /search?q=dog

[
{
    "id": "2",
    "title": "lazy dog"
    "data": "A quick brown fox jumped over lazy dog. A fox is always jumping."
}]


GET /search?q=quick%20dog

[
{
    "id": "2",
    "title": "lazy dog"
    "data": "A quick brown fox jumped over lazy dog. A fox is always jumping."
},
{
    "id": "1",
    "title": "quick fox",
    "data": "A fox is usually quick and brown."
}]

```

### Directions

- you can use any programming language of your choice
- try and complete the assignment in given time. It's totally fine if it's not complete. We would love to see the assignment anyway.
- keeping above point in mind, attempt the tasks in the order that they are mentioned.
- you should design your solution keeping scalability in mind, a search engine is usually scalable to terrabytes of data
- call us if you have any trouble understading anything

