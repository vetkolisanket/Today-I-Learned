# Code Snippets

To start mongo server

```
mongod
```

To start mongo client

```
mongo
```

To show available databases

```
show dbs
```

To use a database

```
use <db name>
```

To show collections within a DB, you first need to switch to a database using `use <db name>` command

```
show collections
```

To show documents within a collection

```
db.<collection name>.find()
```

To show documents containing a particular field (in the below example the field is "type")

```
db.<collection name>.find({"type":{$exists:true}})
```

To show documents containing a particular field having values in a particular set of values

```
db.<collection name>.find({"type":{"$in":["a","b","c"]}})
```
