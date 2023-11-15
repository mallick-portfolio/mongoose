# Mongodb

- ## Mongodb `insertOne()` and `insertMany()` function

  - In Mongodb we can easily add new items/data into the collections. We use `insertOne()` and `insertMany()` to insert one or many data into the collections.

  - Example for `insertOne()` function

  ```js
  db.test.insertOne({ name: "Jhon" });
  ```

  - Here inside `insertOne()` function we pass the data as object

  - Example for `insertMany()` function

  ```js
  db.test.insertOne([{ name: "Jhon" }, { name: "Kamal" }]);
  ```

  - Here inside `insertMany()` function we pass the data as array of object

- ## Mongodb `find()` and `findOne()` function

  - Mongodb `find()` and `findOne()` is used to find data from any specific table. `find()` is used to find all data from any table on the other hand `findOne()` is used to find single data with specific key

  - Example for `find()` function

  ```js
  db.test.find();
  ```

  - In this code `db` is the Mongodb IDatabase and `test` is the table name and `find()` is the function to get all data from the `test` table. We can pass some `find()` function paramerter. We can select field filtering by passing data inside the function

  - Example for field filter by passing parameter

  ```js
  db.test.find({ name: 1, email: 1 });
  ```

  - In this example we only get data from the test table that field name is name and email other filed name data will not get. If we want other field data the we need to follow same process as name, email.We can also do same for `findOne()` function.

  - For field filtering we can use another process but the process is only work with the `find()` function. We can use `project()` function that take the field name that filed we want to get.

  - Example

  ```js
  db.test.find().project({ name: 1, email: 1 });
  ```

  - Example of `findOne()` function

  ```js
  db.test.findOne({ email: "example@gmail.com" });
  ```

  - In this given code the we will get data from the test table where the email is `example@gmail.com`. For field filtering we can pass the second parameter that field we want

- ## Mongodb operator
  -
