# Mongoose

- ## Mongoose `find()` and `findOne()` function

  - Mongoose `find()` and `findOne()` is used to find data from any specific table. `find()` is used to find all data from any table on the other hand `findOne()` is used to find single data with specific key

  - Example for `find()` function

  ```code
  db.test.find()
  ```

  - In this code `db` is the mongoose IDatabase and `test` is the table name and `find()` is the function to get all data from the `test` table. We can pass some `find()` function paramerter. We can select field filtering by passing data inside the function

  - Example for field filter by passing parameter

  ```code
  db.test.find({name: 1, email: 1})
  ```

  - In this example we only get data from the test table that field name is name and email other filed name data will not get. If we want other field data the we need to follow same process as name, email.We can also do same for `findOne()` function.

  - For field filtering we can use another process but the process is only work with the `find()` function. We can use `project()` function that take the field name that filed we want to get.

  - Example

  ```code
    db.test.find().project({name: 1, email: 1})
  ```

  - Example of `findOne()` function

  ```code
    db.test.findOne({email: 'example@gmail.com'})
  ```

  - In this given code the we will get data from the test table where the email is `example@gmail.com`. For field filtering we can pass the second parameter that field we want
