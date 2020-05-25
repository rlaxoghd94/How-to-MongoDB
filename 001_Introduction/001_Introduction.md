# Introduction

## What is a MongoDB

> Mongo DB is a document database designed for ease of development and scaling

### Document Database

A record in MongoDB is a document, which is a data structure compose dof field and value pairs. MongoDB documents are similar to JSON objects. The values of fileds may include other documents, arrays, and arrays of documents.

```mongo
{
    name: "sue",                                <-- field:value
    age: 26,                                    <-- field:value
    status: "A",                                <-- field:value
    groups: [ "news", "sports" ]                <-- field:value
}
```

The advantages of using documents are:

- Documents correspond to native data types in many programming languages

- Embedded documents and arrays reduce need for expensive joins

- Dynamic schema supports fluent polymorphism

#### Collections/Views/On-Demand Materialized Views

MongoDB stores documents in collections. Collections are analogous to tables in relational databases.

### Key Features

#### High Performance

- Support for embedded data models reduces I/O activity on database system

- Indexes support faster queries and can include keys from embedded documents and arrays

#### Rich Query Language

- MongoDB supports a rich query language to support CRUD as well as:

  - Data Aggregation

  - Text Search and Geospatial Queries

#### High Availability

MongoDB's replication facility, called `replica set`, provides:

- *automatic* failover

- data redundancy

A `replica set` is a group of MongoDB servers that maintain the same data set, providing redundancy and increase data availability.

#### Horizontal Scalability

MongoDBB provides horizontal scalability as part of its *core* functionality:

- Sharding distributes data across a cluster of machines.

- Starting in 3.4, MongoDB supports creating ***zones*** of data based on the ***shard key***. In a balanced cluster, MongoDB directs reads and writes covered by a zone only to those shards inside the zone.s