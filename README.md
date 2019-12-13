# MongoDB Cheatsheet

### General Commands
#### Opens the monogDB shell

```mongo
$ mongo
```

## Commands

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

#### Drop Collection
```mongo
db.<collection-name>.drop();
```