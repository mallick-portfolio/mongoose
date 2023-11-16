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

  - In this example we only get data from the test table that field name is name and email other field name data will not get. If we want other field data the we need to follow same process as name, email.We can also do same for `findOne()` function.

  - For field filtering we can use another process but the process is only work with the `find()` function. We can use `project()/projection` function that take the field name that field we want to get.

  - Example

  ```js
  db.test.find().project({ name: 1, email: 1 });


  db.test.find().projection({ name: 1, email: 1 });

  <!-- Both do same -->

  ```

  - Example of `findOne()` function

  ```js
  db.test.findOne({ email: "example@gmail.com" });
  ```

  - In this given code the we will get data from the test table where the email is `example@gmail.com`. For field filtering we can pass the second parameter that field we want

- ## Mongodb Comparison Query Operators

  - $eq
  - $neq
  - $gt
  - $gte
  - $lt
  - $lte
  - $in
  - $nin

  - `$eq` is equal operator. this operator check if the field value is equal to any condition then it show only that match data

  - Example

  ```js
  db.test
    .find({
      age: {
        $eq: 12,
      },
      gender: "Female",
    })
    .project({
      name: 1,
      gender: 1,
      age: 1,
    })
    .sort({ age: -1 });
  ```

  - `$neq` is not equal operator. this operator check if the field value is not equal to any condition then it show only that match data

  - Example

  ```js
  db.test
    .find({
      age: {
        $neq: 12,
      },
      gender: "Female",
    })
    .project({
      name: 1,
      gender: 1,
      age: 1,
    })
    .sort({ age: -1 });
  ```

  - `$gt` is greater than operator. this operator check if the field value is greater then the condition then it show only that match data

  - Example

  ```js
  db.test
    .find({
      age: {
        $gt: 12,
      },
      gender: "Female",
    })
    .project({
      name: 1,
      gender: 1,
      age: 1,
    })
    .sort({ age: -1 });
  ```

  - `$gte` is greater than equal operator. this operator check if the field value is greater then or equal the condition then it show only that match data

  - Example

  ```js
  db.test
    .find({
      age: {
        $gte: 12,
      },
      gender: "Female",
    })
    .project({
      name: 1,
      gender: 1,
      age: 1,
    })
    .sort({ age: -1 });
  ```

  - `$lt` is less than operator. this operator check if the field value is less then the condition then it show only that match data

  - Example

  ```js
  db.test
    .find({
      age: {
        $lt: 12,
      },
    })
    .project({
      name: 1,
      gender: 1,
      age: 1,
    })
    .sort({ age: -1 });
  ```

  - `$lte` is less than equal operator. this operator check if the field value is less then or equal the condition then it show only that match data

  - Example

  ```js
  db.test
    .find({
      age: {
        $lt: 12,
      },
    })
    .project({
      name: 1,
      gender: 1,
      age: 1,
    })
    .sort({ age: -1 });
  ```

  - `$in` in operator. this operator check if the field value is match with any condition then it show only that match data

  - Example

  ```js
  db.test
    .find({
      age: {
        $gte: 18,
        $lte: 30,
      },
      gender: "Female",
      interests: {
        $in: ["Cooking", "Gaming"],
      },
    })
    .project({
      name: 1,
      age: 1,
      gender: 1,
      interests: 1,
    })
    .sort({ age: -1 });
  ```

  - `$nin` not in operator. this operator check if the field value is not match with any condition then it show only that match data.

  - Example

  ```js
  db.test
    .find({
      age: {
        $gte: 18,
        $lte: 30,
      },
      gender: "Female",
      interests: {
        $nin: ["Cooking", "Gaming"],
      },
    })
    .project({
      name: 1,
      age: 1,
      gender: 1,
      interests: 1,
    })
    .sort({ age: -1 });
  ```

- ## Mongodb Logical Query Operators

  - $and
  - $or
  - $not
  - $nor

  - `$and` Explacit `And` operator. This operator check if all field value is match with the condition then it show that match data

  - Example

  ```js
  db.test
    .find({
      $and: [
        {
          age: {
            $gte: 18,
          },
        },
        {
          age: {
            $lte: 30,
          },
        },
        {
          gender: "Female",
        },
        {
          interests: {
            $in: ["Cooking", "Gaming"],
          },
        },
      ],
    })
    .projection({
      name: 1,
      age: 1,
      gender: 1,
      interests: 1,
    })
    .sort({ _id: -1 })
    .limit(100);
  ```

  - `$or` Explacit `Or` operator. This operator check if any field value is match with the condition then it show that match data

  - Example

  ```js
  db.test
    .find({
      $or: [
        {
          age: {
            $gte: 18,
          },
        },
        {
          age: {
            $lte: 30,
          },
        },
        {
          gender: "Female",
        },
        {
          interests: {
            $in: ["Cooking", "Gaming"],
          },
        },
      ],
    })
    .projection({
      name: 1,
      age: 1,
      gender: 1,
      interests: 1,
    })
    .sort({ _id: -1 })
    .limit(100);
  ```

  - `$nor` Explacit `nor` operator. This operator check if any field value is not match with the condition then it show that match data

  - Example

  ```js
  db.test
    .find({
      $nor: [
        {
          gender: "Female",
        },
        {
          interests: {
            $in: ["Cooking", "Gaming"],
          },
        },
        {
          "skills.name": {
            $in: ["PYTHON"],
          },
        },
      ],
    })
    .projection({
      name: 1,
      age: 1,
      gender: 1,
      interests: 1,
      skills: 1,
    })
    .sort({ _id: -1 })
    .limit(100);
  ```

- ## Mongodb Element Query Operators

  - $exists
  - $type


  

- ## Mongodb Array Query Operators

  - $size
  - $set
  - $addToSet
  - $push
  - $unset
  - $pop
  - $pull
  - $pullAll
