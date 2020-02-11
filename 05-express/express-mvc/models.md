# Model

### db.js
Configs for your db and the model files:

```js
const pg = require('pg');

// require every single model file in your app
const pokemon = require('./models/pokemon');

configs = {
  user: 'akira',
  host: '127.0.0.1',
  database: 'pokemons',
  port: 5432
};


const pool = new pg.Pool(configs);

pool.on('error', function (err) {
  console.log('idle client error', err.message, err.stack);
});

// export an object with every single model in it

// give the model the DB handler pool
const pokemonForExport = pokemon(pool);

// send this back out
module.exports = {
  /*
   * ADD APP MODELS HERE
   */
  pokemon: pokemonForExport,

  // get a reference to end the connection pool at server end
  pool:pool
};
```

### models/pokemon.js

Export model functions as a module
```js
module.exports = (dbPoolInstance) => {

  // `dbPoolInstance` is accessible within this function scope
  const create = (pokemon, callback) => {
    // set up query
    const queryString = `INSERT INTO pokemons (name, num, img, weight, height)
      VALUES ($1, $2, $3, $4, $5)`;
    const values = [
      pokemon.name,
      pokemon.num,
      pokemon.img,
      pokemon.weight,
      pokemon.height
    ];

    // execute query
    dbPoolInstance.query(queryString, values, (err, queryResult) => {
      // invoke callback function with results after query has executed
      callback(err, queryResult);
    });
  };

  const get = (id, callback) => {
    const values = [id];

    dbPoolInstance.query('SELECT * from pokemons WHERE id=$1', values, (error, queryResult) => {
      callback(error, queryResult);
    });
  };

  return {
    create:create,
    get:get
  };
};
```



### index.js

Where do we actually integrate this back into our app? In the index.js file.

Require the db file
```js
const db = require('./db');
```

Pass all of that stuff into routes
```js
require('./routes')(app, db);
```
