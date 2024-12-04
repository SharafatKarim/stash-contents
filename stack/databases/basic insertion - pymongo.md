---
Owner: Sharafat Karim
Last edited time: 2023-01-15T16:13
---
```JavaScript
import pymongo

client = pymongo.MongoClient("mongodb+srv://openai:<password>@openai-database-telemet.rfzyl6k.mongodb.net/?retryWrites=true&w=majority")
db = client.test
mydb = client["database"]
mycol = mydb["users"]

mylist = [
  { "name": "Amy", "address": "Apple st 652"},
  { "name": "Hannah", "address": "Mountain 21"},
  { "name": "Michael", "address": "Valley 345"},
  { "name": "Sandy", "address": "Ocean blvd 2"},
  { "name": "Betty", "address": "Green Grass 1"},
  { "name": "Richard", "address": "Sky st 331"},
  { "name": "Susan", "address": "One way 98"},
  { "name": "Vicky", "address": "Yellow Garden 2"},
  { "name": "Ben", "address": "Park Lane 38"},
  { "name": "William", "address": "Central st 954"},
  { "name": "Chuck", "address": "Main Road 989"},
  { "name": "Viola", "address": "Sideway 1633"}
]

x = mycol.insert_many(mylist)

\#print list of the _id values of the inserted documents:
print(x.inserted_ids)

print(client.list_database_names())
print(mydb.list_collection_names())
```