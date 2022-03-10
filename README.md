<h1 align="center"> MongoDb CheatSheet</h1>

<h2 align="center"> MongoDb Database Commands

### Show databases

```ruby  
show dbs
```

### Create or switch databases 

```ruby
use databaseName
```

### Show in which database I am currently in 

```ruby
db
```

### Delete a database

```ruby
db.dropDatabase()
```


<h2 align="center"> MongoDb Collections Commands

### Show collections

```ruby
show collections
```

### Create or switch collections

```ruby
db.createCollection('CollectionName')
```

### Drop a collection

```ruby
db.CollectionName.drop()
```


<h2 align="center">MongoDB Commands for Rows

### Insert a row 

```ruby
db.CollectionName.insert({
    'name':'Kushal',
    'language':'C++',
    'learning_since':5
})
```

### Insert many rows

```ruby
db.CollectionName.insertMany([
    {
        'name':'Kushal',
        'language':'C++',
        'learning_since':5
    },
    {
        'name':'Kuntal',
        'language':'Java',
        'learning_since':2
    },
    {
        'name':'Amit',
        'language':'Python',
        'learning_since':7
    },
    {
        'name':'Arslan',
        'language':'Python',
        'learning_since':20
    },
])
```

### To see all the rows in the Collections

```ruby
db.CollectionName.find()
```

### To see the rows in the Collection in a pretty format

```ruby
db.CollectionName.find().pretty()
```

### To limit the number of rows we want to see

<p>For Example : 2 rows</p>
```ruby
db.CollectionName.find().pretty().limit(2)
```


### Search in a MongoDb database

```ruby
db.CollectionName.find({language:'Python'})
```

### Count the number of rows in the collection

```ruby
db.CollectionName.find().count()
```

#### Count only limits the number of rows shown in the output but does  not reduce the original number of rows

```ruby
db.CollectionName.find().pretty().limit(2).count()
```

### To get the specific count with any parameter

<p>This gives 2 as answer</p>

```ruby
db.CollectionName.find({language:'Python'}).count()
```

### To sort the collection based on a specific parameter

###### Ascending order
```ruby
db.CollectionName.find().sort({learning_since:1}).pretty()
```
###### Descending order
```ruby
db.CollectionName.find().sort({learning_since:-1}).pretty()
```

### To find the 1st row matching the object

```ruby
db.CollectionName.findOne({language:'Python'})
```

### To update a row

```ruby
db.CollectionName.update({language:'Python'},
    {
        'name':'Amit',
        'language':'Python',
        'learning_since':1
    })
```

### To update a row and insert a new row if the object does not match

```ruby
db.CollectionName.update({language:'C'},
    {
        'name':'Amit',
        'language':'Python',
        'learning_since':1
    },{upsert:true})
```

## MongoDb Operators

### MongoDb increment operator

```ruby
db.CollectionName.update({language:'Python'},
{$inc:{
        learning_since:2
    }})
```
<p font-family="">The learning_since parameter of the rows with language Python will be incremented by 2</p>


### MongoDb rename operator

```ruby
db.CollectionName.update({language:'Python'},
{$rename:{
        learning_since:'learning'
    }})
```

### Delete a row

```ruby
db.CollectionName.remove({language:'Python'})
```

### MongoDb less than operator

<p>Displays the rows in which the learning_since is less than 2 years</p>

```ruby
db.CollectionName.find({learning_since:{$lt:2}})
```



