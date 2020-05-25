# Databases and Collections

MongoDB stores BSON documents, i.e. data records, in collections; the collections in databases.

## Databases

In MongoDB, databases hold collections of documents.

```
use myDB
```

### Create a Database

If a database does not exist, MongoDB creates the database when you first store data for that database. As such you can switch to a non-existent database and perform the following operation in the mongo shell:

```
use myNewDB

db.myNewCollection1.insertOne( { x: 1 } )
```

The `insertOne()` operation creates both the databse **myNewDB** and the collection **myNewCollection1** if they do not already exist.

### Create a Collection

If a collection does not exist, MongoDB creates the collection when you first store data for that collection.

```
db.myNewCollection2.insertOne( { x: 1 } )
db.myNewCollection3.createIndex( { y: 1 } )
```

Both the `insertOne()` and the `createIndex()` operation create their respective collection if they do not already exist.

