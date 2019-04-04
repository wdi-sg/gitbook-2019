## Routes

We started by talking about the files for dealing with the DB.

Now we need to talk about the part of the app that specifies the route matching.

### index.js

Require the db file
```js
const db = require('./db');
```

Pass all of that stuff into routes
```js
require('./routes')(app, db);
```

### routes.js

Pass the db from routes into the controllers so that we can use them

```js
module.exports = (app, db) => {

  const pokemons = require('./controllers/pokemon')(db);

  app.get('/pokemon/:id', pokemons.get);
  app.get('/pokemons/:id/edit', pokemons.updateForm);
  app.post('/pokemons/:id/edit', pokemons.update);
  app.get('/pokemons/new', pokemons.createForm);
  app.post('/pokemons', pokemons.create);
  app.get('/pokemons/:id', pokemons.get);
};
```
