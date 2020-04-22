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

Inside of `controllers/pokemon.js` add one method to the pokemon controller file for this route.

Don't forget to make a key for the method at the bottom of the file.

Use `response.send('banana')` to test it.

##### models

Inside of `models/pokemon.js` create a new method `getStudent` in the pokemon model file that queries for a single student by name.

```
const getStudent = (name) => {
```

It runs this query (change the below to be dynamic)

```
SELECT * FROM students WHERE name='kevin';
```

- the method has to take the student name as a parameter to put in the WHERE clause
- console.log the result in the model

*Note:* don't forget to make a key for the method at the bottom of the file.

##### call model from controller

Call your model method from your controller

```
db.pokemon.getStudent(name)
```

Watch for the console.log

##### pass callback to model

Inside of `conroller/pokemon.js` change your controller method to define and pass a callback to the model.

```
const whenDoneInModel = (err, result)=>{
  console.log("wow, done");
};

db.pokemon.getStudent(name, whenDoneInModel);
```

##### Run the callback


In `models/pokemon.js` change the function signature in the model to use this new parameter. (i.e., the thing you pass in in the controller must match what you have in the model)

```
const getStudent = (name, callback) => {
  // run the query
  ...
    // when the query is done, call the callback

    // pass the result of the query
    callback(err, results.rows)
```

##### respond with the model result

Inside of `conroller/pokemon.js` move the `response.send` into the callback.

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

Now add a new model, `dogs`.

You must add the `require` of this model file in `db.js`

You must require the file and call it, passing in the variable `pool`.

You must export it at the bottom of `db.js`

```js
const dogsModelFunc = require('./models/dogs.js');
const dogsModel = dogsModelFunc( pool );

...
module.exports = {

  ...
  dogsModel: dogsModel
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
const dogs = require('./controllers/dogs')(allModels);
app.get('/dogs', something.getAllDogs);
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

Add a get route to render a form to create a single class (`GET /dogs/new`)

Add a model method to take in the `POST` request this form creates. This is a new controller file.

#### Further

Add owners model and controller to this app. Don't create any view (jsx) files yet.

Create:

GET `/owners/new`
POST `/owners`
GET `/owners/:id`

#### Further

Add the `/dogs/:id` route.

Show the dog's owner by making a nested query in the model using this syntax:

```js
db.dogs.getDog(request.params.id, (dogError, dog)=>{

  let ownerId = dog.owner_id;

  db.owners.getOwner(ownerId, (ownerError, owner)=>{
    // response send goes here
  })
});
```


#### Further

In the model, check `result.rows`. If it's empty, don't give back `result.rows`, instead give back an error and check for it in the controller.

#### Further

Fill in the rest of the `restful` routes for dogs and owners.
