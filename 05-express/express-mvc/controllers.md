# Controller

From `index.js` the routes are required.

The routes require the controller file.

For each route, pass in the controller function as the callback.

When the controller is included in the routes, db is passed in at that time.

```js
module.exports = (db) => {

  /**
   * ===========================================
   * Controller logic
   * ===========================================
   */
  const get = (request, response) => {
      // use pokemon model method `get` to retrieve pokemon data
      db.pokemon.get(request.params.id, (error, queryResult) => {
        // queryResult contains pokemon data returned from the pokemon model
        if (error) {
          console.error('error getting pokemon:', error);
          response.sendStatus(500);
        } else {
          // render pokemon view in the pokemon folder
          response.render('pokemon/Pokemon', { pokemon: queryResult.rows[0] });
        }
      });
  };

  const updateForm = (request, response) => {
      // TODO: Add logic here
  };

  const update = (request, response) => {
      // TODO: Add logic here
  };

  const createForm = (request, response) => {
    response.render('pokemon/new');
  };

  const create = (request, response) => {
      // use pokemon model method `create` to create new pokemon entry in db
      db.pokemon.create(request.body, (error, queryResult) => {
        // queryResult of creation is not useful to us, so we ignore it
        // (console log it to see for yourself)
        // (you can choose to omit it completely from the function parameters)

        if (error) {
          console.error('error getting pokemon:', error);
          response.sendStatus(500);
        }

        if (queryResult.rowCount >= 1) {
          console.log('Pokemon created successfully');
        } else {
          console.log('Pokemon could not be created');
        }
        // redirect to home page after creation
        response.redirect('/');
      });
  };

   // Export controller functions as a module
  return {
    get,
    updateForm,
    update,
    createForm,
    create
  };

}
```


## Timeline

#### Note that it is *not* neccesarry to follow the code flow of this MVC template in order to use it. Start by simply plugging in the functionality that you need in each different file to connect them together.

##### It may or may not be helpful for you to understand the execution order of each file in order to understand how the code works.

#### App Startup
For our express MVC setup this happen in this order.

1. execute `index.js`
1. `db.js` is included
  1. `db.js` sets up the db connection pool
  1. `db.js` includes the model files
  1. the model file include is a function- it gets executed so that the models themselves get an instance of the pool connection.
  1. the connection pool and the model instances get returned to index.js
1.  the routes file gets included in index.js
  1. the routes file is a function, it is called with the express app instance and the db object
  1. every controller function gets included at the top of the routes file.
    1. the complete controller is a function. it gets executed so that it has access to the db object.
  1. each matching string route is in this file. for every route it gets a controller function
  1. (that controller function has already been passed the db instance


#### On request
1. Express responds to the callback set to that route.
1. The controller function has an instance of db pool to make a query with
1. The callback of the db query is written in the controller.
1. The response get sent back


