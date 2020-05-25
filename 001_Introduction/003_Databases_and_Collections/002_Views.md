# Views

A MongoDB view is a queryable object whose contents are defined by an *aggregation pipeline* on other collections or views. MongoDB does not persist the view contents to disk. A view's content is computed on-demand when a client queries the view. MongoDB can require clients to have permission to query the view. MongoDB does not support write operations against views.

For example, you can:

- Create a view on a collection of employee data to *exclude* any private or personal information.

- Create a view on a collection of collected sensor data to *add* computed fields and metrics.

- Create a view that *joins* two collections containing inventory and order history respectively.

When client query a view, MongoDB appends the client query to the underlying pipeline and returns the results of that combined pipeline to the client. MongoDB may apply aggregation pipeline optimization to the combined pipeline.

## Create view

To create or define a view:

- Use the `db.createCollection()` method or the `create` command:

```
db.createCollection(
  "<viewName>",
  {
    "viewOn" : "<source>",
    "pipeline" : [<pipeline>],
    "collation" : { <collation> }
  }
)
```

- Use the `db.createView()` method:

```
db.createView(
  "<viewName>",
  "<source>",
  [<pipeline>],
  {
    "collation" : { <collation> }
  }
)
```

> You must create views in the same database as the source collection

