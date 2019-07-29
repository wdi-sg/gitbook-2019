## Full Stack

Create an express app:

```
mkdir express-fulls
cd express-fulls
mkdir views
npm init
npm install express
npm install express-react-views react react-dom
touch index.js
touch views/hello.jsx
```


index.js
```
console.log("about to require express");
const express = require('express');

const app = express();
console.log("done creating app");

// this line below, sets a layout look to your express project
const reactEngine = require('express-react-views').createEngine();
app.engine('jsx', reactEngine);

// this tells express where to look for the view files
app.set('views', __dirname + '/views');

// this line sets react to be the default view engine
app.set('view engine', 'jsx');


app.get('/hello', (request, response) => {
  console.log('waffles');
  response.render('hello');
})

const port = 3000;
console.log("start listening");
app.listen(port)
console.log("done listening");
```

hello.jsx
```
var React = require('react');

class Hello extends React.Component {

  render() {
    console.log('sushi');

    return (
              <html>
                <body>
                  <h1>hello Full Stack</h1>
                </body>
              </html>
    );
  }
}

module.exports = Hello;
```


#### Run the app

[http://127.0.0.1:3000/hello](http://127.0.0.1:3000/hello)

#### Create some javascript that runs in the browser

Allow express to serve static files from the `public` directory.

index.js
```
app.use(express.static('public'))
```

```shell
mkdir public
```

Make a js file:
```
cd public
touch script.js
```

script.js
```
console.log('chicken');
console.log("we are in the browser");
```

##### Change hello.jsx
```html
<script src="/script.js"></script>
```

#### pairing exercise

### Request from different perspectives:
What does the request look like:
  - leaving the browser, in the network tab of chrome
  - directly from the terminal
  - from outside your computer

##### Open the chrome dev tools

##### Run the app

[http://127.0.0.1:3000/hello](http://127.0.0.1:3000/hello)


##### run curl

On the terminal:

```bash
curl 127.0.0.1:3000/hello
```

##### request from another computer

On the terminal, find your pair's IP address:
```bash
ifconfig
```

Use that to make a request to their server, e.g.:

```
curl 143.21.2.1:3000/hello
```

#### WHERE DOES THIS RUN??

Note that is is *very* important to understand the order and context of the execution of all of this code.

Make sure that you can answer all of these questions.

- Where and when does the `waffles` `console.log` above happen?
- Where and when does the `sushi` `console.log` above happen?
- Where and when does the `chicken` `console.log` above happen?
- Where do you look for each `console.log` and why?
- What happens if you `console.log` `window` instead of `waffles`?
- What happens if you `console.log` `process` instead of `waffles`?
- What happens if you `console.log` `window` instead of `chicken`?
- What happens if you `console.log` `process` instead of `chicken`?
- How does the `script.js` file get from the `public` folder to the browser?
- When does it get there?
- Find all of the relevant requests in the chrome dev tools network tab.



#### further
Add to your `script.js`.

When the page loads, create a button. When the user clicks the button, wait 5 seconds. Get rid of all the content on the screen. Turn the background color black. Display a message (in white text) that says "Reversed!".

#### further

Add a new app.get
```
app.get('/dogs/:name', (request, response) => {
  console.log('yay dogs');

  response.render('dogs');
})
```

dog.jsx
```
var React = require('react');

class Dog extends React.Component {

  render() {
    console.log('rendering');

    return (
              <html>
                <body>
                  <h1>dog</h1>
                  <div id="data"></div>
                </body>
              </html>
    );
  }
}

module.exports = Dog;
```

Use or make a similar script to above.

Instead, this time, make the message include the name of the dog in the `request.params`.

To get the name of the dog from request params into your `script.js`, construct the value of the variable as a string in the jsx file:

add to dog.jsx:
```
<script>
  var name = {this.props.dog.name};
</script>
```

#### further
Add a database- pokemons, songs, etc.

Write an app.get show route, e.g., `/pokemon/:id` or `/songs/:id`, etc.

When the user clicks a button, 5 seconds later show the name of the pokemon/song.
