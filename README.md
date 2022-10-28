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

To see contents of a collection , filtering by name

`db.students.find({name:'Chris'})

---------------------------------------


To EDIT A Field NAME In A Table:

`db.students.updateMany({},{$rename:{"number_of_belts":"belts_earned"}})`

---------------------------------------

To Insert An Item In A Table:

`db.users.insertOne({name: 'Chris', location: 'TN'})`

---------------------------------------

Add a new field called 'number_of_belts' to ALL students with a starting value of 0

`db.students.updateMany({},{$set:{number_of_belts:0}})`
`db.students.updateMany({},{$set:{updated_on:'Oct28th,2022'}})`

---------------------------------------

Delete An Item In A Table:

`db.users.deleteOne({name: 'Chris'})`

---------------------------------------

Delete all students with a home_state of 'California'

`db.students.deleteMany({home_state:'California'})`

---------------------------------------

Delete a student by name

`db.students.deleteOne({name:'Mary'})`

---------------------------------------


Delete the FIRST student with a lucky_number that is GREATER THAN 5

`db.students.deleteOne({lucky_number:{$gte:5}})`

---------------------------------------

Delete an item from an existing array

`db.students.updateOne({name:'Britt'},{$pull:{interests: "Gardening"}})`

---------------------------------------


Delete a field from a table

`db.students.updateMany({},{$unset:{lucky_number:1}},{multi:true})`

---------------------------------------
---------------------------------------
---------------------------------------

updateOne = Update very first thing or the specified item
updateMany = Update everything that matches the query

---------------------------------------
To Update An Item In A Table:


---------------------------------------

`db.users.updateOne({name:'Chris'}, {$set:{favoriteFood: 'Italian'}})`

---------------------------------------

updateMany = Update everything that matches the query

example: Add interests: "coding", "brunch", "MongoDB" to all students

`db.students.updateMany({},{$push:{interests:["coding","brunch","MongoDB"]}})`

Add another interest into the existing interests array

`db.students.updateOne({name:'Britt'},{$push:{interests: "Gardening"}})`

Update the number_of_belts for ALL students to add 1
inc=increment

`db.students.updateMany({},{$inc:{number_of_belts:1}})`

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



