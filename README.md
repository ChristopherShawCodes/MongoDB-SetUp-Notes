# MongoDB-SetUp-Notes

Mongo DB is used in the command prompt 
---------------------------------------
Start Server:

`Mongosh`

---------------------------------------

Create Database:

`use new_db`

---------------------------------------

Delete Database:

`db.dropDatabase()`

---------------------------------------

Create Table / Collection:

`db.createCollection('collectionName')`

---------------------------------------

Drop Table / Collection:

`db.collectionName.drop()`

---------------------------------------

To See Contents Of A Collection:

`db.collectionName.find()`

---------------------------------------

To Insert An Item In A Table:

`db.users.insertOne({name: 'Chris', location: 'TN'})`

---------------------------------------

To Delete An Item In A Table:

`db.users.deleteOne({name: 'Chris'})`

---------------------------------------

To Update An Item In A Table:

`db.users.updateOne({name:'Chris'}, {$set:{favoriteFood: 'Italian'}})`

`db.users.updateMany({name:'Chris'}, {$set:{favoriteFood: 'Italian'}})`

---------------------------------------

*****Frequently Used Operators*****

`$gt (Greater Than, Used to query number fields)`
-----------------------------------------------------------------------------------

`$gte (Greater Than Or Equal To , Used to query number fields)`

-----------------------------------------------------------------------------------

`$lt (LessThan  , Used to query number fields)`

-----------------------------------------------------------------------------------

`$lte (LessThan Or Equal To  , Used to query number fields)`

-----------------------------------------------------------------------------------

Sort by number between 1 and 9 

`db.tableName.find({lucky_number: {$gte:1,$lte:9}})`

-----------------------------------------------------------------------------------


`$in (In Array , Used to find documents who have a particular value within an array)`

-----------------------------------------------------------------------------------


`$addToSet (like $push but only adds to the specified array if the value doesn't already exist, no duplicate entries)`

-----------------------------------------------------------------------------------


`$push (Push to an array contained within a document)`

-----------------------------------------------------------------------------------

`$pop (Removes the first or last element in an array)`

example: 

`db.COLLECTION.update({QUERY}, {$pop:{array_key:(1 or -1)}})`

1 = last item in array
-1 = first item in array

-----------------------------------------------------------------------------------

`$pull (Removes a specified value from an array , unlike $pop because POP removes by the location in the array)`

example: 

`db.COLLECTION.update({QUERY}, {$pull: {array_kay: VALUE}})`

This will remove ALL instances of VALUE from the documents with the array specified by the array_key that matches QUERY`


-------------------------------------------------------------------------------------------------------------------------------------------------------

Example Quiz:


1. You have an inventory management database. For each document inside your products collection, you have a field called 'inventory_count' that represents the total number of that product inside your warehouse. What would be the query to find all products with an inventory_count of 10 or less?

`db.products.find({inventory_count: {$lte: 10}})`

2. The $addToSet operator ...

`only adds to an array if the value doesn't exist yet.`

3. You have a users collection. For each document inside this collection, you have a field called 'interests', which is an array. What is the proper way to add a new interest to this array?

`db.users.update({QUERY}, {$push {interests: "cooking"}})`



