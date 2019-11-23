# Mongoose

>It is a ODM helper which provide queries for **MongoDB**

Mongoose [models](https://mongoosejs.com/docs/models.html) provide several static helper functions for [CRUD operations](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete). Each of these functions returns a [mongoose `Query` object](http://mongoosejs.com/docs/api.html#Query).

### CRUD OPERATIONS

#### Model.deleteMany()

Deletes all the documents that matches the conditions from the collection.Behaves like `remove()`, but deletes all documents that match `conditions` regardless of the `single` option.

```mongoose
dBInstance.deleteMany({ name: /Stark/, age: { $gte: 18 } }).then().catch();
```

#### Model.deleteOne()

Deletes the first document that matches `conditions` from the collection. Behaves like `remove()`, but deletes at most one document regardless of the `single` option.

```mongoose
dbInstance.deleteOne({ name: 'Eddard Stark' }).then().catch();
```

#### Model.find()

`find()` methods will give / filter the document from the collection based on the conditions.

```mongoose
dbInstance.find({ name: '/test/', age: ${gte: 15 }}).then().catch();
```

```mongoose
dbInstance.find().then().catch();
```

#### Model.findById()

`findById()` is method is similar to `Model.findOne({ _id: id })`. This method will return the a record from the collection that matches with `id`.

```mongoose
dbInstance.findById(<id>).then().catch();
```

#### Model.findByIdAndDelete()

`findByIdAndDelete()` is similar to `Model.findOneAndDelete({ _id: id})`. This method will find the record from the collection by the `id` and `deletes` the record / document from the collection.

```mongoose
dbInstance.findByIdAndDelete(<id>).then().catch();
```

#### Model.findByIdAndRemove()

`findByIdAndRemove()` is similar to findAndModify. Finds a matching document, removes it, passing the found document (if any) to the callback / then block. This is equivalent to `Model.findOneAndRemove({ id: _id })

```mongoose
dbInstance.findByIdAndRemove(<id>).then().catch(); or
dbInstance.findByIdAndRemove(<id>, { select: {
  name 'balaji'
}}).then().catch()
```

> Always try to use `Model.findByIdAndDelete()`

#### Model.findByIdAndUpdate()

`findByIdAndUpdate()` is similar to `findOneAndUpdate({  _id: id })`. Finds the document by Id and updates it based on the conditions

```mongoose
dbInstance.findByIdAndUpdate(<id>, { name: 'test' }).then().catch();
```

#### Model.findOne()

`findOne()` will return the record based on the condition

```mongoose
dbInstance.findOne({ name: 'test' }).then().catch()
```

#### Model.findOneAndReplace()

`findOneAndReplace()` will replace the first matching document from the collection based on the condition

```mongoose
dbInstance.findOneAndReplace({ name: 'test' }, { name: 'Testing'} );
```

> This will replace the entire record. The `findOneAndReplace` searches the document, removes **everything** inside this document and sets the entrys of the given replacement document.

#### Model.findOneAndUpdate() 

`findOneAndReplace()` will update the first matching document from the collection based on the condition.

```mongoose
dbInstance.findOneAndReplace({ name: 'test' }, { name: 'Testing', age: 21 } );
```

>The `findOneAndUpdate` searches the document and updates just the entrys in the given update document. The other entrys in the found document will remain.

#### Model.updateOne()

`updateOne() `will find the record and updates it. This will update only the first matching document

```mongoose
dbInstance.updateOne({ _id: id }, { name: 'Testing', age: 21 } );
```

#### Model.updateMany()

updateMany() `will find the record and updates it. This will update all the  matching document

```mongoose
dbInstance.updateMany({ _id: id }, { name: 'Testing', age: 21 } );
```

#### Model.replaceOne()

replaceOne() `will find the record and replaces it. This will update the first matching document

```mongoose
dbInstance.replaceOne({ _id: id }, { name: 'Testing', age: 21 } );
```

