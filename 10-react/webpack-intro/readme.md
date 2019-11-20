# Webpack

Asset pipeline, but in javascript.

### Webpack Benefits

- use npm / package.json to manage app dependencies
- installable browser code libraries with dependencies
- use import to manage multiple application files

## Getting started
We will implement the webpack asset pipeline for the code we need to write in this unit.

Run the example app: `npm run build` `node index.js` Visit [http://localhost:3000](http://localhost:3000) Open the generated `main.js` file. Scroll to the bottom. What do you see?

### Import an npm library

```
npm install cat-ascii-faces
```

Look inside the `package.json` file:
```
sublime package.json
```

Look inside the npm library storage directory to see the actual library:
```
ls -la node_modules
```

Browse the code:
```
sublime node_modules/cat-ascii-faces/.
```

Put code in `src/client/index.js` that runs the library.
```
import cats from 'cat-ascii-faces'

console.log(cats()) // returns a random cat
```

Build the file:

```
npm run build
```

Look inside the `main.js` file. What's changed?

### import vs require

Basically `require` was invented with `nodejs` and expanded from there. `import` is meant to be agnostic.

### Pairing Exercise

Clone the react repo into a named folder:

```bash
$ git clone https://github.com/wdi-sg/react-reference.git webpack-intro
```

Repeat the above.


#### Further
Just like in unit 2, create a `module` and `import` it in the `src/client/index.js` file.

(look up how to make a module here: [https://wdi-sg.github.io/gitbook-2019/04-server/01modules.html](https://wdi-sg.github.io/gitbook-2019/04-server/01modules.html) )

#### Further

Look here: [https://wdi-sg.github.io/gitbook-2019/04-server/01npm.html](https://wdi-sg.github.io/gitbook-2019/04-server/01npm.html) for more npm packages to install. Not all of them will work.

