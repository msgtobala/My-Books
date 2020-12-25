**INSTALLATION**

sudo apt-get install mongodb

sudo service mongodb start

 

table - collection

entries - document

entry - record

 

**CMD COMMANDS**

start mongo shell by - mongo

show dbs;

use <dbName>; will create if not any or else will create it

db; - will show the current db;

 

**creating user -** 

db.createUser({

  user: '<name>',

  pwd: '<pwd>',

  roles: ['readWrite', dbAdmi]

});

 

**creating collection -** 

db.createCollection('<collectionName>');

**inserting document into the collection -** 

db.<collectionName>.insert({name: "test", age: 10});

**inserting multiple document into the collection -** 

db.<collectionName>.insert([{name: 'test', age: 20},{name: 'testing', age: 21}]);

**viewing inserted documents into collection**

db.<collectionName>.find(); 

 

**viewing documents in collection in JSON type**

db.<collectionName>.find().pretty();

**updating a field -** 

db.<collectionName>.update({match},{to_be_changed_field});

ex:

db.customers.update({name: "john"}, {name: "doe"});

***\* But this will update all the fields and removes it only updates the mentioned/included field.so use set**

**updating field with set operator**

db.<collectionName>.update({name: 'john'}, { $set: { gender: 'male' } });

**updating the field with inc operator**

db.<collectionName>.update({name: 'john'}, { $inc: { age: 5 } });

**removing a field from a document with unset operator**

db.<collectionName>.update({name: 'test'}, $unset: { age: 1} );

***\* Note including only age field gives error always include { fieldName: 1 }**

 

**when we try to update the field that does not have a match update command does nothing**

**To insert the update field** **even-though** **the match has not found -** 

db.<collectionName>.update({ name: 'test' },{ name: 'testing' },{ upsert: true });

**renaming a field -** 

db.<collectionName>.update({ name: 'test' }, {$rename: { 'gender' : 'sex' } });

**removing documents -** 

db.<collectionName>.remove( { name: 'test' } );

***\* This will delete all the documents of collection**

 

**removing documents of first match -** 

db.<collectionName>.remove({ name: 'test' }, { justOne: true });

**find only the particular record**

db.<collectionName>.find({ name: 'test' });

**using or operator in find();**

***\* This will return all the document of mentioned records**

db.<collectionName>.find({ $or: [ { name: 'test' }, { name: 'testing' } ] });

**getting all documents having particular field**

db.<collectionName>.find({ gender: 'male' });

**getting all documents with value gt / lt / gte / lte**

db.<collectionName>.find({age: { $gt: 40}});

db.<collectionName>.find({age: { $lt: 40}});

db.<collectionName>.find({age: { $gte: 40}});

db.<collectionName>.find({age: { $lte: 40}});

 

 

 

 

 

 

 

 **INSTALLATION**

 

 

 

 