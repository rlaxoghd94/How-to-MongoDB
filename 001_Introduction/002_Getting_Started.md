# Getting Started

## Examples

### Switch Database

Within the MongoDB shell, **db** refers to your current database. Type **db** to display the current database.

```
db
```

To switch database, type `use <db>`. For example, to switch to the `examples` database:

```
use examples
```

You don't need to create the databse before you siwtch. MongoDB createse the database when you first store data in that database.

### Populate a collection (Insert)

MongoDB stores documents in collections. Collections are analogous to tables in relational databases. If a collection does not exist, MongoDB creates the collection when you first store data for that collection.

The following example uses the `db.collection.insertMany()` method to insert new documents into the **inventory** collection.

```
db.inventory.insertMany([
   { item: "journal", qty: 25, status: "A", size: { h: 14, w: 21, uom: "cm" }, tags: [ "blank", "red" ] },
   { item: "notebook", qty: 50, status: "A", size: { h: 8.5, w: 11, uom: "in" }, tags: [ "red", "blank" ] },
   { item: "paper", qty: 10, status: "D", size: { h: 8.5, w: 11, uom: "in" }, tags: [ "red", "blank", "plain" ] },
   { item: "planner", qty: 0, status: "D", size: { h: 22.85, w: 30, uom: "cm" }, tags: [ "blank", "red" ] },
   { item: "postcard", qty: 45, status: "A", size: { h: 10, w: 15.25, uom: "cm" }, tags: [ "blue" ] }
]);

// MongoDB adds an _id field with an ObjectId value if the field is not present in the document
```

The operation returns a document that contains the acknowledgement indicator and an array that contains the `_id` of each successfully inserted documents.

To verify the insert, you can query the collection.

### Select All Documents

To select the documents from a collection, you can use the `db.collection.find()` method. To select all document sin the collection, pass an empty document as the *query filter document* to the method.

```
db.inventory.find({})

// db.inventory.find({}).pretty() for a formatted result
```

### Specify Equality Matches

For an equality match (i.e. `<field>` equals `<value>`), specify `<field>: <value>` in the *query filter document* and pass to the `db.collection.find()` method.

- Where `status` field equals `"D"`

```
db.inventory.find( { status: "D" } );
```

### Specify Fields to Return(Projection)

To specify fields to return, pass a projection document to the `db.collection.find(<query document>, <projection document>)` method. In the projection document, specify:

- `<field>`: **1** to include a field in the returned documents

- `<field>`: **0** to exclude a field in the returned documents

In order to return the `_id`, `item`, and the `status` fields from all documents in the `inventory` collection:

```
db.inventory.find( { }, { item: 1, status: 1 } );
```

You don't need to specify the `_id` field to return the field. It returns by default. To exclude the field, set it to 0 in the projection document.

```
db.inventory.find( {}, { _id: 0, item: 1, status: 1 } );
```