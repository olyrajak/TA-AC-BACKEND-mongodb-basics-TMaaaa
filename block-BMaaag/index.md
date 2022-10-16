writeCode

Write code to:-

- create a database named `mountains`
<!-- use mountains
switched to db mountains -->
- a collection inside that database named `himalayas`
<!-- db.createCollection("himalayas");
{ ok: 1 } -->
- insert 1 document into that collection `{name: 'Dhauldhar range', height: '4000 mtrs'}`
<!-- db.himalayas.insert({name: 'Dhauldhar range', height: '4000 mtrs'})
DeprecationWarning: Collection.insert() is deprecated. Use insertOne, insertMany, or bulkWrite.
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("634b8b96ce240cd619c9d6ea") }
}
 -->
- insert multiple document using insertMany command
<!-- db.himalayas.insertMany([{name: 'Dhauldhar range', height: '4000 mtrs'},{name: 'Kangchenjunga', height: ' 28,169 mtrs'},{name: 'Denali', height: '20,310 mtrs'},{name: 'Kilimanjaro', height: '19,341 mtrs'}]) 

{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("634b97e8ce240cd619c9d6eb"),
    '1': ObjectId("634b97e8ce240cd619c9d6ec"),
    '2': ObjectId("634b97e8ce240cd619c9d6ed"),
    '3': ObjectId("634b97e8ce240cd619c9d6ee")
  }
}

-->
- find all documents from mountains

<!-- db.himalayas.find();
[
  {
    _id: ObjectId("634b8b96ce240cd619c9d6ea"),
    name: 'Dhauldhar range',
    height: '4000 mtrs'
  },
  {
    _id: ObjectId("634b97e8ce240cd619c9d6eb"),
    name: 'Dhauldhar range',
    height: '4000 mtrs'
  },
  {
    _id: ObjectId("634b97e8ce240cd619c9d6ec"),
    name: 'Kangchenjunga',
    height: ' 28,169 mtrs'
  },
  {
    _id: ObjectId("634b97e8ce240cd619c9d6ed"),
    name: 'Denali',
    height: '20,310 mtrs'
  },
  {
    _id: ObjectId("634b97e8ce240cd619c9d6ee"),
    name: 'Kilimanjaro',
    height: '19,341 mtrs'
  }
]
 -->
- find a single document using name
<!-- 
 db.himalayas.find({name:"Kilimanjaro"});
[
  {
    _id: ObjectId("634b97e8ce240cd619c9d6ee"),
    name: 'Kilimanjaro',
    height: '19,341 mtrs'
  }
] -->

