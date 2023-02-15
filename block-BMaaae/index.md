writeCode

Write code to:-

- create a database named `sports`.
<!--   use sports
switched to db sports
-->
- list all databases present in local mongod server.

<!--  show dbs
admin    40.00 KiB
config  108.00 KiB
local    40.00 KiB
test      8.00 KiB
 -->
- create 3 collections named `cricket`, `football`, `TT` in sports databse.
<!-- db.createCollection("cricket");
{ ok: 1 } -->
<!-- db.createCollection("football");
{ ok: 1 } -->
<!-- db.createCollection("TT");
{ ok: 1 } -->
- add multiple players in those collections which should have fields like `name`, `age` and `email` and `bid_price`.


<!-- 
For Cricket 

db.cricket.insert({"name": "Player 1","age": 26,"email": "player1@email.com","bid_price": "3cr"})
DeprecationWarning: Collection.insert() is deprecated. Use insertOne, insertMany, or bulkWrite.
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("634ad7b466f378b70db1faa6") }
}
db.cricket.insert({"name": "Player 2","age": 27,"email": "player12@email.com","bid_price": "4cr"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("634ad7f566f378b70db1faa7") }
}
db.cricket.insert({"name": "Player 3","age": 37,"email": "player123@email.com","bid_price": "6cr"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("634ad81766f378b70db1faa8") }
}


For football


db.football.insert({"name": "Player 3","age": 37,"email": "player123@email.com","bid_price": "6cr"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("634ad8d766f378b70db1faa9") }
}

db.football.insert({"name": "Player 2","age": 38,"email": "player13@email.com","bid_price": "6cr"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("634ad8f766f378b70db1faaa") }
}
sports> db.football.insert({"name": "Player 1","age": 28,"email": "player3@email.com","bid_price": "5cr"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("634ad90f66f378b70db1faab") }
}

For TT 



db.TT.insert({"name": "Player 1","age": 28,"email": "player3@email.com","bid_price": "5cr"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("634ad93f66f378b70db1faac") }
}
sports> db.TT.insert({"name": "Player 2","age": 29,"email": "player2@email.com","bid_price": "2cr"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("634ad96f66f378b70db1faad") }
}
sports> db.TT.insert({"name": "Player 3","age": 24,"email": "player1@email.com","bid_price": "5cr"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("634ad98766f378b70db1faae") }
}

 -->

- list all collections in sports database.

<!-- show collections
cricket
football
TT
 -->
- rename `TT` collection to `tennis`.
 <!-- db.TT.renameCollection("tennis")
{ ok: 1 } -->
- create a capped collection called `khokho` which should have max 3 documents.
<!-- 
db.createCollection("khokho", {capped: true,size:2048, max: 3})
{ ok: 1 }

 -->

  Try inserting more than 3 and see what happens?
<!-- db.khokho.insert({"name": "Player 14","age": 15,"email": "player14@email.com","bid_price": "1.3cr"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("634ada7166f378b70db1faaf") }
}
sports> {
...   acknowledged: true,
...   insertedIds: { '0': ObjectId("62e686c74411f58825fd4b29") }
... }
... }
sports>  db.khokho.insert({"name": "Player 14","age": 15,"email": "player14@email.com","bid_price": "1.3cr"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("634adaa166f378b70db1fab0") }
}
sports>  db.khokho.insert({"name": "Player 14","age": 15,"email": "player14@email.com","bid_price": "1.3cr"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("634adaa666f378b70db1fab1") }
}
sports>  db.khokho.insert({"name": "Player 14","age": 15,"email": "player14@email.com","bid_price": "1.3cr"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("634adaa966f378b70db1fab2") }
}
sports>  db.khokho.insert({"name": "Player 14","age": 15,"email": "player14@email.com","bid_price": "1.3cr"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("634adaab66f378b70db1fab3") }
}
db.khokho.insert({"name": "Player 7","age": 15,"email": "player17@email.com","bid_price": "1.3cr"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("634adb3066f378b70db1fab4") }
}
sports>  db.khokho.insert({"name": "Player 8","age": 15,"email": "player17@email.com","bid_price": "1.3cr"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("634adb3a66f378b70db1fab5") }
}
spor -->
  <!--  db.khokho.find()
[
  {
    _id: ObjectId("634adb3066f378b70db1fab4"),
    name: 'Player 7',
    age: 15,
    email: 'player17@email.com',
    bid_price: '1.3cr'
  },
  {
    _id: ObjectId("634adb3a66f378b70db1fab5"),
    name: 'Player 8',
    age: 15,
    email: 'player17@email.com',
    bid_price: '1.3cr'
  }
]


delete Old data -->
- check whether a collection is capped or not?

<!--  
db.khokho.isCapped()
db.tennis.isCapped()
db.football.stats()
db.tennis.stats()

 -->
- drop all documents from `football` collection.
<!-- db.football.remove({})
{ acknowledged: true, deletedCount: 3 } -->

- delete cricket collection completely.
<!-- db.cricket.drop()
true
 -->
- delete sports database.
<!-- db.dropDatabase()
{ ok: 1, dropped: 'sports' }

 -->
- check which database you are connected to ?
 <!-- db
sports -->

- connect to test database
<!-- use test
switched to db test
 -->
