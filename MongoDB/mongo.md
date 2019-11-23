# MongoDB

> MongoDB is a **No SQL**(Not Only SQL) database.  It is a non-relational database with collections / documents with data-type as **BSON** ( Binary  Script Object Notation )

* Compass - GUI for creating databases
* Atlas - Cloud database service

#### INSTALLATION

* Visit [MongoDB For Mac](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-os-x/)  to download ( This is bit difficult ) so follow the steps from below,
* Visit [Brew](https://brew.sh/)
* Copy the link( /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" ) run on the terminal
* brew tap mongodb/brew
* brew install mongodb-community@4.2
* brew services start mongodb-community
* mongo

#### CORE

* Open terminal and run mongo for mongo shell

**Show Database**

```mariadb
show dbs;
```

**Use Databases**

```mariadb
use <db-name>;
```

**Create database**

```mariadb
use <db-name>
```

**use  <db-name>** will create a new database and use it, if there is no such db created before. If it already create it will use it

**Drop Database**

```mariadb
db.dropDatabase();
```

**Create Collections**

```mariadb
db.createCollection(<collection-name>);
```

**Show Collections**

```mariadb
show collections
```

> Note: Collections refers to Tables

 Inserting one Documents / records / rows

```mariadb
db.<collection>.insert({
   title: 'name',
   body: 'body',
   date: new Date()
});
```

**Insert Multiple records**

```mariadb
db.<collection>.insertMany([
  {
   title: 'name1',
   body: 'body1',
   date: new Date()
  },
  {
   title: 'name2',
   body: 'body2',
   date: new Date()
  },
  {
   title: 'name3',
   body: 'body3',
   date: new Date()
  }
]);
```

**Find the Data**

```mariadb
 db.<collection>.find();
```

**Query Data with Pretty**

```mariadb
db.<collection>.find().pretty();
```

**Find the Particular. Record**

```mariadb
db.<collection>.find({
     record_key: 'value' // title: 'name1'                
}).pretty( ); 
```

**Sorting the records**

```mariadb
db.<collection>.find().sort({
  record_to_sorted: 1                           
}).pretty();
```

> 1 - Ascending
>
> -1 - Descending

**Find the Length of the records**

```mariadb
db.<collection>.find().count();
```

**Limit the records**

```mariadb
db.collection.find().limit(2);
```

> Returns only first two records

**Method Chaining**

```mariadb
db.<collection>.find().sort({
  record_to_be_sorted: -1
}).limit(2).pretty();
```

**For Each**

```mariadb
 db.<collection>.find().forEach(function(doc){
    print('Blog Post: ' + doc.<key>)                            
 });
```

> doc holds each record

**Find One specific row**

```mariadb
 db.<collection>.findOne({
    key: 'value'                     
 });
```

> returns the first match

**Update**

 ```mariadb
db.<collection>.update({ record_to_be_updated: 'value' }, { updated_record: 'new value', body: 'new body', date: Date()} { upsert: true});
 ```

> Arg1 - Record to be update
>
> Arg2 - Updated record
>
> Arg3 - Upsert (true / false)
>
> * True - if the record to be updated is not found, then it will insert it
> * False - if the record to be updated is found, then it will update it

>update() method will replace th entire record

**Update with Set Operator**

```mariadb
db.<collection>.update({ record_to_be_updated: 'value' }, { 
    $set: {
       new_field_key: 'new_value',
       new_field_key: 'new_value'           
    }
 });
```

> This will modify only the updating data and the rest will remain untouched.

**INC Operator**

```mariadb
db.<collection>.update({ record_to_be_updated: 'value' }, {
   $inc: { field_to_be_updated: <inc_value> }                       
});
```

**Rename  field**

```mariadb
db.<collection>.update({ record_to_be_updated: 'value' }, {
     $rename: { old_field_name: 'new_field_name'}                  
 });
```

**Delete record**

```mariadb
db.<collection>.remove({ to_be_removed_record: 'value' });
```

**Sub Records**

```mariadb
db.collection.update({ record_to_be_updated: 'value' }, {
   $set: {
      <new_field>: [
        {
          key: 'value',
          key2: 'value2'
        }
      ]             
   }                  
});
```

**Find the data in Sub Records**

```mariadb
db.<collection>.find({
   <field_name>: {
      $elemMatch: {
         key: 'value'         
      }               
   }                  
});
```

**Add Index / Search**

Add Index

```mariadb
db.<collection>.createIndex({ <field_name>: 'index_name' });
```

Search ( Text Search )

```mariadb
db.<collection>.find({
   $text: {
			$search: "/"<search_text>"/"
   }                     
});
```

**Greater than and Less than**

```mariadb
db.<collection>.find({
   <field_name>: { $gt: <number> }                  
});
```

```mariadb
db.<collection>.find({
   <field_name>: { $gte: <number> }                  
});
```

```mariadb
db.<collection>.find({
   <field_name>: { $lt: <number> }                  
});
```

```mariadb
db.<collection>.find({
   <field_name>: { $lte: <number> }                  
});
```

| Relational  | Non-Relational    |
| ----------- | ----------------- |
| Database    | Database          |
| Table       | Collection        |
| Row         | Record / Document |
| Index       | Index             |
| Join        | $lookup           |
| Foreign Key | Reference         |

## Object Id

>Object id is generated by Mongo db driver. It should be unique 

