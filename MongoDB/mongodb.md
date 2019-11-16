# MongoDB Cheat Sheet

## Show All Databases

```
show dbs
```

## Show Current Database

```mariadb
db
```

## Create Or Switch Database

```mariadb
use acme
```

## Drop

```mariadb
db.dropDatabase()
```

## Create Collection

```mariadb
db.createCollection('posts')
```

## Show Collections

```mariadb
show collections
```

## Insert Row

```mariadb
db.posts.insert({
  title: 'Post One',
  body: 'Body of post one',
  category: 'News',
  tags: ['news', 'events'],
  user: {
    name: 'John Doe',
    status: 'author'
  },
  date: Date()
})
```

## Insert Multiple Rows

```mariadb
db.posts.insertMany([
  {
    title: 'Post Two',
    body: 'Body of post two',
    category: 'Technology',
    date: Date()
  },
  {
    title: 'Post Three',
    body: 'Body of post three',
    category: 'News',
    date: Date()
  },
  {
    title: 'Post Four',
    body: 'Body of post three',
    category: 'Entertainment',
    date: Date()
  }
])
```

## Get All Rows

```mariadb
db.posts.find()
```

## Get All Rows Formatted

```mariadb
db.find().pretty()
```

## Find Rows

```mariadb
db.posts.find({ category: 'News' })
```

## Sort Rows

```mariadb
# asc
db.posts.find().sort({ title: 1 }).pretty()
# desc
db.posts.find().sort({ title: -1 }).pretty()
```

## Count Rows

```mariadb
db.posts.find().count()
db.posts.find({ category: 'news' }).count()
```

## Limit Rows

```mariadb
db.posts.find().limit(2).pretty()
```

## Chaining

```mariadb
db.posts.find().limit(2).sort({ title: 1 }).pretty()
```

## Foreach

```mariadb
db.posts.find().forEach(function(doc) {
  print("Blog Post: " + doc.title)
})
```

## Find One Row

```mariadb
db.posts.findOne({ category: 'News' })
```

## Find Specific Fields

```mariadb
db.posts.find({ title: 'Post One' }, {
  title: 1,
  author: 1
})
```

## Update Row

```mariadb
db.posts.update({ title: 'Post Two' },
{
  title: 'Post Two',
  body: 'New body for post 2',
  date: Date()
},
{
  upsert: true
})
```

## Update Specific Field

```mariadb
db.posts.update({ title: 'Post Two' },
{
  $set: {
    body: 'Body for post 2',
    category: 'Technology'
  }
})
```

## Increment Field (\$inc)

```mariadb
db.posts.update({ title: 'Post Two' },
{
  $inc: {
    likes: 5
  }
})
```

## Rename Field

```mariadb
db.posts.update({ title: 'Post Two' },
{
  $rename: {
    likes: 'views'
  }
})
```

## Delete Row

```mariadb
db.posts.remove({ title: 'Post Four' })
```

## Sub-Documents

```mariadb
db.posts.update({ title: 'Post One' },
{
  $set: {
    comments: [
      {
        body: 'Comment One',
        user: 'Mary Williams',
        date: Date()
      },
      {
        body: 'Comment Two',
        user: 'Harry White',
        date: Date()
      }
    ]
  }
})
```

## Find By Element in Array (\$elemMatch)

```mariadb
db.posts.find({
  comments: {
     $elemMatch: {
       user: 'Mary Williams'
       }
    }
  }
)
```

## Add Index

```mariadb
db.posts.createIndex({ title: 'text' })
```

## Text Search

```mariadb
db.posts.find({
  $text: {
    $search: "\"Post O\""
    }
})
```

## Greater & Less Than

```mariadb
db.posts.find({ views: { $gt: 2 } })
db.posts.find({ views: { $gte: 7 } })
db.posts.find({ views: { $lt: 7 } })
db.posts.find({ views: { $lte: 7 } })
```
