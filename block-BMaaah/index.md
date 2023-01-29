writeCode

Write code to execute below expressions.

1. Create a database named `blog`.
<!-- use blog
switched to db blog -->
2. Create a collection called 'articles'.
<!-- db.createCollection("articles");
{ ok: 1 }
 -->
3. Insert multiple documents(at least 3) into articles. It should have fields

- title as string
- createdAt as date
- details as String
- author as nested object
  - author should have
    - name
    - email
    - age
    - example author: {name: 'abc', email: 'abc@gmail', age: 25}
- tags : Array of strings like ['html', 'css']

```js
// An article should look like in the database
{
  _id: 'some_random_id',
  title: '',
  details: '',
  author: {
    name: '',
    email: '',
    age: ''
  },
  tags: ['js', 'mongo']
}
```
<!-- db.articles.insertMany([
    {
      title: 'Articles 1',
      details: 'description1',
      author: {
        name: 'articles1',
        email: 'articles1@email.com',
        age: '20'
      },
      tags: ['div', 'p', 'h1']
    },{
      title: 'Articles 2',
      details: 'description2',
      author: {
        name: 'articles2',
        email: 'articles2@email.com',
        age: '21'
      },
      tags: ['html', 'css', 'mongo']
    },{
      title: 'Articles 3',
      details: 'description3',
      author: {
        name: 'articles3',
        email: 'articles3@email.com',
        age: '22'
      },
      tags: ['main', 'section', 'header']
    },{
        title: 'Articles 4',
        details: 'description4',
        author: {
          name: 'articles4',
          email: 'articles4@email.com',
          age: '28'
        },
        tags: ['b', 'marquee', 'node']
      },{
        title: 'Articles 5',
        details: 'description5',
        author: {
          name: 'description5',
          email: 'description5@email.com',
          age: '29'
        },
        tags: ['b', 'marquee', 'node']
      },
])

{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("634bf7ff18dec09d212c927c"),
    '1': ObjectId("634bf7ff18dec09d212c927d"),
    '2': ObjectId("634bf7ff18dec09d212c927e"),
    '3': ObjectId("634bf7ff18dec09d212c927f"),
    '4': ObjectId("634bf7ff18dec09d212c9280")
  }
}

 -->
4. Find all the articles using `db.COLLECTION_NAME.find()`
<!--  db.articles.find()
[
  {
    _id: ObjectId("634bf7ff18dec09d212c927c"),
    title: 'Articles 1',
    details: 'description1',
    author: { name: 'articles1', email: 'articles1@email.com', age: '20' },
    tags: [ 'div', 'p', 'h1' ]
  },
  {
    _id: ObjectId("634bf7ff18dec09d212c927d"),
    title: 'Articles 2',
    details: 'description2',
    author: { name: 'articles2', email: 'articles2@email.com', age: '21' },
    tags: [ 'html', 'css', 'mongo' ]
  },
  {
    _id: ObjectId("634bf7ff18dec09d212c927e"),
    title: 'Articles 3',
    details: 'description3',
    author: { name: 'articles3', email: 'articles3@email.com', age: '22' },
    tags: [ 'main', 'section', 'header']
  },
  {
    _id: ObjectId("634bf7ff18dec09d212c927f"),
    title: 'Articles 4',
    details: 'description4',
    author: { name: 'articles4', email: 'articles4@email.com', age: '28' },
    tags: [ 'b', 'marquee', 'node' ]
  },
  {
    _id: ObjectId("634bf7ff18dec09d212c9280"),
    title: 'Articles 5',
    details: 'description5',
    author: {
      name: 'description5',
      email: 'description5@email.com',
      age: '29'
    },
    tags: [ 'b', 'marquee', 'node' ]
  }
]
 -->
5. Find a document using \_id field.
<!-- db.articles.findOne({_id: ObjectId("634bf7ff18dec09d212c927f")}) 

db.articles.findOne({_id: ObjectId("634bf7ff18dec09d212c927f")}) 
{
  _id: ObjectId("634bf7ff18dec09d212c927f"),
  title: 'Articles 4',
  details: 'description4',
  author: { name: 'articles4', email: 'articles4@email.com', age: '28' },
  tags: [ 'b', 'marquee', 'node' ]
}

-->
6. 1. Find documents using title
<!-- db.articles.findOne({title: "Articles 4"}) 
db.articles.findOne({title: "Articles 4"})
{
  _id: ObjectId("634bf7ff18dec09d212c927f"),
  title: 'Articles 4',
  details: 'description4',
  author: { name: 'articles4', email: 'articles4@email.com', age: '28' },
  tags: [ 'b', 'marquee', 'node' ]
}


-->
7. 2. Find documents using author's name field.
<!-- db.articles.find({"author.name" : "articles3"})
[
  {
    _id: ObjectId("634bf7ff18dec09d212c927e"),
    title: 'Articles 3',
    details: 'description3',
    author: { name: 'articles3', email: 'articles3@email.com', age: '22' },
    tags: [ 'main', 'section', 'header' ]
  }
]
 -->
8. Find document using a specific tag.
<!-- db.articles.find({tags : "marquee"})
[
  {
    _id: ObjectId("634bf7ff18dec09d212c927f"),
    title: 'Articles 4',
    details: 'description4',
    author: { name: 'articles4', email: 'articles4@email.com', age: '28' },
    tags: [ 'b', 'marquee', 'node' ]
  },
  {
    _id: ObjectId("634bf7ff18dec09d212c9280"),
    title: 'Articles 5',
    details: 'description5',
    author: {
      name: 'description5',
      email: 'description5@email.com',
      age: '29'
    },
    tags: [ 'b', 'marquee', 'node' ]
  }
]
-->
9. Update title of a document using its \_id field.
<!-- db.articles.update({_id: ObjectId("634bf7ff18dec09d212c927e")}, {$set: {title: 'Articles 7'}}) 
db.articles.update({_id: ObjectId("634bf7ff18dec09d212c927e")}, {$set: {ttitle: 'Articles 7'}})
DeprecationWarning: Collection.update() is deprecated. Use updateOne, updateMany, or bulkWrite.
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
db.articles.findOne({title: "Articles 7"}) 
{
  _id: ObjectId("634bf7ff18dec09d212c927e"),
  title: 'Articles 7',
  details: 'description3',
  author: { name: 'articles3', email: 'articles3@email.com', age: '22' },
  tags: [ 'main', 'section', 'header' ]
}

-->
10. Update a author's name using article's title.
<!--  db.articles.update({title: "Articles 7"}, {$set: {"author.name" : "Oly Rajak"}}) 

{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
blog> db.articles.findOne({title: "Articles 7"}) 
{
  _id: ObjectId("634bf7ff18dec09d212c927e"),
  title: 'Articles 7',
  details: 'description3',
  author: { name: 'Oly Rajak', email: 'articles3@email.com', age: '22' },
  tags: [ 'main', 'section', 'header' ]
}


-->
11. rename details field to description from all articles in articles collection.
<!-- 
 db.articles.updateMany({}, {$rename: {"details": "description"}}, {multi: true})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 5,
  modifiedCount: 5,
  upsertedCount: 0
}

 -->
12. Add additional tag in a specific document.
<!--  db.articles.update({title: "Articles 7"}, {$push: {"tags": "jquery"}}) 

{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}


-->
13. Update an article's title using $set and without $set.
- Write the differences here ?

13. find an article using title and increment it's auhtor's age by 5.
<!-- db.articles.update({title: "Articles 7"}, {$inc: {"author.age": 5}}) -->
14. Delete a document using \_id field with `db.COLLECTION_NAME.remove()`.
<!-- db.articles.remove({_id: ObjectId("634bf7ff18dec09d212c927e")}) 

DeprecationWarning: Collection.remove() is deprecated. Use deleteOne, deleteMany, findOneAndDelete, or bulkWrite.
{ acknowledged: true, deletedCount: 1 }

-->
// Sample data

```js
db.users.insertMany([
  {
    age: 49,
    name: "Maurice Brock",
    email: "wuk@hibpiz.ch",
    gender: "Female",
    sports: ["cricket", "football"],
    scores: [24, 35, 18, 16],
    weight: 45,
  },
  {
    age: 37,
    birthday: "7/15/1986",
    name: "Virgie Cunningham",
    email: "ezogafa@de.gm",
    gender: "Male",
    sports: ["football"],
    scores: [17, 35, 43],
    weight: 52,
  },
  {
    age: 48,
    birthday: "5/14/1961",
    name: "Alexander Holt",
    email: "han@mu.pe",
    gender: "Male",
    sports: ["cricket", "football", "TT"],
    scores: [24, 30, 16],
    weight: 55,
  },
  {
    age: 53,
    birthday: "11/15/1963",
    name: "Derek Dawson",
    email: "polril@now.de",
    gender: "Male",
    sports: ["cricket", "hockey"],
    scores: [20, 15, 38, 23],
    weight: 49,
  },
  {
    age: 34,
    birthday: "7/24/1964",
    name: "Cynthia Cobb",
    email: "wujjarpob@jecimpar.gu",
    gender: "Female",
    sports: ["cricket"],
    scores: [41, 17, 28],
    weight: 51,
  },
  {
    age: 33,
    birthday: "10/26/1982",
    name: "Isabella Atkins",
    email: "ononuzas@givhoz.ca",
    gender: "Female",
    sports: ["cricket", "football", "hockey", "TT"],
    scores: [14, 38, 29, 45, 20],
    weight: 49,
  },
  {
    age: 47,
    birthday: "10/12/1978",
    name: "Katharine Bryan",
    email: "zo@pebi.sa",
    gender: "Male",
    sports: ["TT", "hockey", "khokho"],
    scores: [27, 20, 34],
    weight: 58,
  },
  {
    age: 41,
    birthday: "1/28/1991",
    name: "Beatrice Fleming",
    email: "ufufsa@pujizren.tk",
    gender: "Female",
    sports: ["football", "khokho"],
    scores: [30, 20, 15, 29, 43],
    weight: 47,
  },
  {
    age: 26,
    birthday: "3/23/1998",
    name: "Tom Fields",
    email: "wasodjow@ofaba.gf",
    gender: "Female",
    sports: ["khokho"],
    scores: [37, 29, 18, 43, 49],
    weight: 50,
  },
  {
    age: 33,
    birthday: "11/14/1960",
    name: "Steve Ortega",
    email: "dupus@ca.ls",
    gender: "Female",
    sports: ["cricket", "football", "hockey"],
    scores: [12, 15, 20],
    weight: 51,
  },
  {
    age: 24,
    birthday: "1/5/1994",
    name: "Suraj Kumar",
    weight: 50,
    gender: "Male",
    sports: ["football", "cricket", "TT"],
  },
]);
```

Insert above data into database to perform below queries:-
<!-- {
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("634c0ae118dec09d212c9281"),
    '1': ObjectId("634c0ae118dec09d212c9282"),
    '2': ObjectId("634c0ae118dec09d212c9283"),
    '3': ObjectId("634c0ae118dec09d212c9284"),
    '4': ObjectId("634c0ae118dec09d212c9285"),
    '5': ObjectId("634c0ae118dec09d212c9286"),
    '6': ObjectId("634c0ae118dec09d212c9287"),
    '7': ObjectId("634c0ae118dec09d212c9288"),
    '8': ObjectId("634c0ae118dec09d212c9289"),
    '9': ObjectId("634c0ae118dec09d212c928a"),
    '10': ObjectId("634c0ae118dec09d212c928b")
  }
}
 -->

- Find all males who play cricket.

<!-- db.users.find({gender: "Male"})
[
  {
    _id: ObjectId("634c0ae118dec09d212c9282"),
    age: 37,
    birthday: '7/15/1986',
    name: 'Virgie Cunningham',
    email: 'ezogafa@de.gm',
    gender: 'Male',
    sports: [ 'football' ],
    scores: [ 17, 35, 43 ],
    weight: 52
  },
  {
    _id: ObjectId("634c0ae118dec09d212c9283"),
    age: 48,
    birthday: '5/14/1961',
    name: 'Alexander Holt',
    email: 'han@mu.pe',
    gender: 'Male',
    sports: [ 'cricket', 'football', 'TT' ],
    scores: [ 24, 30, 16 ],
    weight: 55
  },
  {
    _id: ObjectId("634c0ae118dec09d212c9284"),
    age: 53,
    birthday: '11/15/1963',
    name: 'Derek Dawson',
    email: 'polril@now.de',
    gender: 'Male',
    sports: [ 'cricket', 'hockey' ],
    scores: [ 20, 15, 38, 23 ],
    weight: 49
  },
  {
    _id: ObjectId("634c0ae118dec09d212c9287"),
    age: 47,
    birthday: '10/12/1978',
    name: 'Katharine Bryan',
    email: 'zo@pebi.sa',
    gender: 'Male',
    sports: [ 'TT', 'hockey', 'khokho' ],
    scores: [ 27, 20, 34 ],
    weight: 58
  },
  {
    _id: ObjectId("634c0ae118dec09d212c928b"),
    age: 24,
    birthday: '1/5/1994',
    name: 'Suraj Kumar',
    weight: 50,
    gender: 'Male',
    sports: [ 'football', 'cricket', 'TT' ]
  }
]
 -->
- Update user with extra golf field in sports array whose name is "Steve Ortega".
<!-- db.users.update({name: "Steve Ortega"}, {$push:{sports: "golf"} })
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
db.users.find({name: "Steve Ortega"})
[
  {
    _id: ObjectId("634c0ae118dec09d212c928a"),
    age: 33,
    birthday: '11/14/1960',
    name: 'Steve Ortega',
    email: 'dupus@ca.ls',
    gender: 'Female',
    sports: [ 'cricket', 'football', 'hockey', 'golf' ],
    scores: [ 12, 15, 20 ],
    weight: 51
  }
]
 -->
- Find all users who play either 'football' or 'cricket'.
<!-- 
db.users.find({name: "Steve Ortega"})
[
  {
    _id: ObjectId("634c0ae118dec09d212c928a"),
    age: 33,
    birthday: '11/14/1960',
    name: 'Steve Ortega',
    email: 'dupus@ca.ls',
    gender: 'Female',
    sports: [ 'cricket', 'football', 'hockey', 'golf' ],
    scores: [ 12, 15, 20 ],
    weight: 51
  }
]
blog>  db.users.find({sports: {$in : ['cricket', 'football']}})
[
  {
    _id: ObjectId("634c0ae118dec09d212c9281"),
    age: 49,
    name: 'Maurice Brock',
    email: 'wuk@hibpiz.ch',
    gender: 'Female',
    sports: [ 'cricket', 'football' ],
    scores: [ 24, 35, 18, 16 ],
    weight: 45
  },
  {
    _id: ObjectId("634c0ae118dec09d212c9282"),
    age: 37,
    birthday: '7/15/1986',
    name: 'Virgie Cunningham',
    email: 'ezogafa@de.gm',
    gender: 'Male',
    sports: [ 'football' ],
    scores: [ 17, 35, 43 ],
    weight: 52
  },
  {
    _id: ObjectId("634c0ae118dec09d212c9283"),
    age: 48,
    birthday: '5/14/1961',
    name: 'Alexander Holt',
    email: 'han@mu.pe',
    gender: 'Male',
    sports: [ 'cricket', 'football', 'TT' ],
    scores: [ 24, 30, 16 ],
    weight: 55
  },
  {
    _id: ObjectId("634c0ae118dec09d212c9284"),
    age: 53,
    birthday: '11/15/1963',
    name: 'Derek Dawson',
    email: 'polril@now.de',
    gender: 'Male',
    sports: [ 'cricket', 'hockey' ],
    scores: [ 20, 15, 38, 23 ],
    weight: 49
  },
  {
    _id: ObjectId("634c0ae118dec09d212c9285"),
    age: 34,
    birthday: '7/24/1964',
    name: 'Cynthia Cobb',
    email: 'wujjarpob@jecimpar.gu',
    gender: 'Female',
    sports: [ 'cricket' ],
    scores: [ 41, 17, 28 ],
    weight: 51
  },
  {
    _id: ObjectId("634c0ae118dec09d212c9286"),
    age: 33,
    birthday: '10/26/1982',
    name: 'Isabella Atkins',
    email: 'ononuzas@givhoz.ca',
    gender: 'Female',
    sports: [ 'cricket', 'football', 'hockey', 'TT' ],
    scores: [ 14, 38, 29, 45, 20 ],
    weight: 49
  },
  {
    _id: ObjectId("634c0ae118dec09d212c9288"),
    age: 41,
    birthday: '1/28/1991',
    name: 'Beatrice Fleming',
    email: 'ufufsa@pujizren.tk',
    gender: 'Female',
    sports: [ 'football', 'khokho' ],
    scores: [ 30, 20, 15, 29, 43 ],
    weight: 47
  },
  {
    _id: ObjectId("634c0ae118dec09d212c928a"),
    age: 33,
    birthday: '11/14/1960',
    name: 'Steve Ortega',
    email: 'dupus@ca.ls',
    gender: 'Female',
    sports: [ 'cricket', 'football', 'hockey', 'golf' ],
    scores: [ 12, 15, 20 ],
    weight: 51
  },
  {
    _id: ObjectId("634c0ae118dec09d212c928b"),
    age: 24,
    birthday: '1/5/1994',
    name: 'Suraj Kumar',
    weight: 50,
    gender: 'Male',
    sports: [ 'football', 'cricket', 'TT' ]
  }
]

 -->
- Find all users whose name includes 'ri' in their name.
<!-- 
 db.users.find({ name: /ri/i })
[
  {
    _id: ObjectId("634c0ae118dec09d212c9281"),
    age: 49,
    name: 'Maurice Brock',
    email: 'wuk@hibpiz.ch',
    gender: 'Female',
    sports: [ 'cricket', 'football' ],
    scores: [ 24, 35, 18, 16 ],
    weight: 45
  },
  {
    _id: ObjectId("634c0ae118dec09d212c9287"),
    age: 47,
    birthday: '10/12/1978',
    name: 'Katharine Bryan',
    email: 'zo@pebi.sa',
    gender: 'Male',
    sports: [ 'TT', 'hockey', 'khokho' ],
    scores: [ 27, 20, 34 ],
    weight: 58
  },
  {
    _id: ObjectId("634c0ae118dec09d212c9288"),
    age: 41,
    birthday: '1/28/1991',
    name: 'Beatrice Fleming',
    email: 'ufufsa@pujizren.tk',
    gender: 'Female',
    sports: [ 'football', 'khokho' ],
    scores: [ 30, 20, 15, 29, 43 ],
    weight: 47
  }
] -->

