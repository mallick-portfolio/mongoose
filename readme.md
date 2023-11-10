# Mongoose 


- ## Mongoose  `find()` and `findone()` function
  - Mongoose `find()` and `findone()` is used to find data from any specific table. `find()` is used to find all data from any table on the other hand `findone()` is used to find single data with specific key

  - Example for `find()` function
  ```code
  db.test.find() 
  ```
  - In this code `db` is the mongoose IDatabase and `test` is the table name and `find()` is the function to get all data from the `test` table. We can pass some `find()` function paramerter. We can select field filtering by passing data inside the function 

  - Example for field filter by passing parameter
  ```code
  db.test.find({name: 1, email: 1}) 
  ```