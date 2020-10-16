# MongoDB Cheatsheet

### General Commands
#### Opens the monogDB shell

```mongo
$ mongo
```

## Commands
### Basics
#### Create and Use Database
```mongo
use <db-name>;
```

#### See Default database
```mongo
db;
```

#### Create Collection
```mongo
db.createCollection("<create-collection>");
```

#### Inserting One Document
```mongo
db.<collection-name>.insert({name: "Bob", age: 20, desg: "Analytics"});         // Inserting One Document
```

#### Inserting Many Documents
```mongo
db.<collection-name>.insertMany([{name: "Alice", age: 30, desg: "Devops"}, {name: "Sue", age: 35, desg: "Full stack"}]);
```

#### Display all Documents
```mongo
db.<collection-name>.find();
```

#### Display Documents in JSON Format
```mongo
db.<collection-name>.find().pretty();
```

#### Display Distinct
```mongo
db.<collection-name>.distinct("name");
```

#### Update Collection
```mongo
db.<collection-name>.update({ refKey : "refValue" }, { $set : { changeKey : "changeValue"}})
```
`refKey` and `refValue` refers to the key and value pair from the document which needs to be updated.
`changeKey` and `changeValue` refers to the actual content which needs to be updated.

#### Drop Collection
```mongo
db.<collection-name>.drop();
```

### Operations 
#### Projection
When we want to retrieve only specific number of fields from a set of documents, this method is used. 
The fields(keys) we wish to retrieve are passed in find method with true Boolean condition.
If we don’t want to retrieve _id we can hide it by giving false Boolean value to it.
```
db.<collection-name>.find({}, key:1, _id:0)
```
#### Limit
If we want to retrieve first specific number of document from a collection this method is used.
The number of elements we wish to retrieve is passed in the limit method.
```
db.<collection-name>.find({}, key:1, _id:0).limit(number)
```

#### Skip
Imagine skipping a particular number of documents from a collection while retrieving data.
In such cases, skip method is useful.
```
Query:  db.<collection-name>.find({}, key:1, _id:0).skip(number)
```

#### Sort
As the name suggests this method is useful when we wish to retrieve data in a particular manner.
If we want to retrieve data an ascending order, 1 is passed or -1 if descending order. 
```
db.<collection-name>.find().sort(refKey:num)
```

### Projection Methods
#### Aggregation :
Aggregations operations process data records and return computed results.
Aggregation operations group values from multiple documents together, and can perform a variety of operations on the grouped data to return a single result.
For the aggregation in MongoDB, you should use `aggregate()` method. 
```
db.<collection-name>.aggregate(Aggregate_operation)
```

#### `$project` method :
Passes along the documents with only the specified fields to the next stage in the pipeline. This may be the existing fields from the input documents or newly computed fields.
 
```
{ “$project”: { <specification> } }
```

#### `$match` method :
Filters the documents to pass only the documents that match the specified condition(s) to the next pipeline stage.
```
{ “$match” : { <query> } }
```

#### `$group` method :
$group is used to group the documents by some specified expression.
```
{ $group: { _id: <expression>, <field1>: { <accumulator1> : <expression1> } } }
```

### Indexing
An index in MongoDB is a special data structure that holds the data of few fields of documents on which the index is created.
####  Apply a new indexing
```
db.collection_name.createIndex({key: 1 or -1})
```
Here, '1' represents ascending order of indexing whereas '-1' descending.

#### Retrieve the index
```
db.<collection-name>.getIndexes()
```
####  Drop the existing index
```
db.<collection-name>.dropIndexes()
```
### Replication
Replication is the process of synchronizing data across multiple servers. Replication provides redundancy and increases data availability with multiple copies of data on different database servers.
#### Set Up a Replica Set
```
mongod --port "PORT" --dbpath "YOUR_DB_DATA_PATH" --replSet "REPLICA_SET_INSTANCE_NAME"
```
#### Add Members to Replica Set
```
>rs.add(HOST_NAME:PORT)
```
