# AJAX & express

Create an express app:


```
mkdir express-ajax
cd express-ajax
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
                  <h1>hello AJAX</h1>
                </body>
              </html>
    );
  }
}

module.exports = Hello;
```
app.use(express.static('public'))



#### Run the app

[http://127.0.0.1:3000/hello](http://127.0.0.1:3000/hello)

#### Create some javascript that runs in the browser

```shell
mkdir public
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

##### Open the chrome dev tools

##### Run the app again

[http://127.0.0.1:3000/hello](http://127.0.0.1:3000/hello)

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


##### AJAX
Change the `script.js` file to include the code below:

```
// what to do when we recieve the request
var responseHandler = function() {
  console.log("response text", this.responseText);
  console.log("status text", this.statusText);
  console.log("status code", this.status);
};

// make a new request
var request = new XMLHttpRequest();

// listen for the request response
request.addEventListener("load", responseHandler);

// ready the system by calling open, and specifying the url
var url = "https://swapi.co/api/people/1";
request.open("GET", url);

// send the request
request.send();
```

Note that this is from the [gitbook](/gitbook-2019/02-js/browser-js/ajax.html)

##### Run the app again

[http://127.0.0.1:3000/hello](http://127.0.0.1:3000/hello)



### AJAX to our own express server

Change the `url` variable in `script.js` to something else:

```
var url = "http://127.0.0.1:3000/banana";
```

Run the app again. [http://127.0.0.1:3000/hello](http://127.0.0.1:3000/hello)

What happens?

##### Create a route that accepts this request:

```
app.get('/banana', (request, response) => {

  console.log('waffles');

  const data = {
    cucumber : "bacon",
    rice : "mango"
  };

  response.send(data);
});
```
