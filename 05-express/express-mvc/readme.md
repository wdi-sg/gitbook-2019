# MVC

MVC stands for Model View Controller

Each of these conceptual parts of the app will be broken up into different files.

This will give structure to our app and allow some code reuse.

We will be using this app as a reference:  [https://github.com/wdi-sg/mvc-template](https://github.com/wdi-sg/mvc-template)


## Pairing Exercise

Clone the MVC template repo.

##### db setup

Make sure `db.js` has the correct configuration for your DB (db name, user name).

Make sure you have a table called students:

```
CREATE TABLE IF NOT EXISTS students (
    id SERIAL PRIMARY KEY,
    name TEXT,
    phone TEXT,
    email TEXT
);
```

##### db seed

Add some students into your DB, if you don't have any:

```
INSERT INTO students
(name, phone, email)
VALUES
('William Smith', '(415)555-5555', 'bill@example.com');

INSERT INTO students
(name, phone, email)
VALUES
('Bob Jones', '(415)555-5555', 'bob@example.com');
```


##### routes

Add one route  to the routes file. `/students`

Assume you will have a new method in pokemon: `pokemons.students`

routes.js
```js
app.get('/students', pokemons.students);
```

##### controllers

Add one method to the pokemon controller file for this route.

Don't forget to make a key for the method at the bottom of the file.

Use `response.send('banana')` to test it.

##### models

Create a new method `getStudent` in the pokemon model file that queries for a single student by name.

```
const getStudent = (name) => {
```

It runs this query (change the below to be dynamic)

```
SELECT * FROM students WHERE name='kevin';
```

- the method has to take the student name as a parameter to put in the WHERE clause
- console.log the result in the model

Don't forget to make a key for the method at the bottom of the file.

##### call model from controller

Call your model method from your controller

```
db.pokemon.getStudent(name)
```

Watch for the console.log

##### pass callback to model

Change your controller to define and pass a callback to the model.

```
const whenDoneInModel = (err, result)=>{
  console.log("wow, done");
};

db.pokemon.getStudent(name, whenDoneInModel);
```

##### Run the callback

Change the function signature in the model.

models/pokemon.js

```
const getStudent = (name, callback) => {
  // run the query
  ...
    // when the query is done, call the callback

    // pass the result of the query
    callback(err, results.rows)
```

##### respond with the model result

```
const whenDoneInModel = (err, result)=>{
  console.log("wow, done");
  response.send( result )
};

db.pokemon.getStudent(name, whenDoneInModel);
```

#### Further

In the above exercise, you added methods to the files that already exist.

This is not how you would normally do it, because you will have **one** controller and model *for each* type of data. (most likely one for each table, excluding some join tables)

Now add a new model, `classes`.

You must add the `require` of this model file in `db.js`

You must require the file and call it, passing in the variable `pool`.

You must export it at the bottom of `db.js`

```js
const someModelFunc = require('./models/someModel');
const someModel = someModelFunc( pool );

...
module.exports = {

  ...
  someModel: someModel
};

```

An empty model looks like this:

```js
module.exports = (dbPoolInstance) => {

  let something = (callback)=>{
    //query
  };

  return {
    something:something,
  };
}
```

Add a controller file. It must be required in the `routes.js` file.

You must pass the variable called `allModels` to the require.

```js
const something = require('./controllers/something')(allModels);
app.get('/banana', something.stuff);
```

An empty controller looks like this:

```js
module.exports = (db) => {

  const index = (request, response) => {
  };

  return {
    index: index,
  };
}
```

Add a get route to render a form to create a single class (`GET /classes/new`)

Add a model method to take in the `POST` request this form creates. This is a new controller file.

#### Further

In the model, check `result.rows`. If it's empty, don't give back `result.rows`, instead give back an error and check for it in the controller.

#### Further

Fill in the rest of the `restful` routes for students and classes.

Make students files instead of pokemon.

