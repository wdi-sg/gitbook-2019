# Views and Templates

We cannot keep using `response.send` to send a response. Ultimately, we'll want to send HTML files back to the client.

We want to have this page's HTML be different for each request. How do we do this??


## Templating with React

If we want to customize what's on the page? We're going to set up a template engine with **[React](http://reactjs.org)** and use that instead.

React is used on the front end of lots of sites, but it's __JSX__ component can also be used to simply create HTML.

#### Note: the server-side react is not the same as browser-side react. Be careful when googling. If a resouce makes reference to DOM or browser events then it is discussing browser react, and may or may not be helpful.

We need to do a couple steps to get the template engine working:

First, install [`express-react-views`](https://github.com/reactjs/express-react-views)

````
npm install express-react-views react react-dom
```

Then, prepare this directory structure on your `node` project:

Run these two commands: `mkdir views` `touch views/home.jsx` to create this structure:

```
.
├── app.js
└── views
    ├── home.jsx

1 directories, 2 files
```



Once structure is setup, you can setup the `express` view engine to `jsx` in this manner.

```javascript
const express = require('express')
const app = express();


// this line below, sets a layout look to your express project
const reactEngine = require('express-react-views').createEngine();
app.engine('jsx', reactEngine);

// this tells express where to look for the view files
app.set('views', __dirname + '/views');

// this line sets react to be the default view engine
app.set('view engine', 'jsx');

app.get('/', (req, res) => {
  // running this will let express to run home.handlebars file in your views folder
  res.render('home')
})
```


### JSX

JSX is javascript and HTML.

Start by using it to simply render an HTML page.
```
var React = require('react');

class Home extends React.Component {
  render() {
    return (
      <html>
        <body>
          <div>
            <h1>Hello</h1>
          </div>
        </body>
      </html>
    );
  }
}

module.exports = Home;
```

At first it just seems like a javascript syntax error, but what we are doing is running this file through a parser that will create HTML for us.

Everything between the `return` parentheses is going to be rendered into HTML.

### Templating

Templating with variables means we can pass in an object to the `.render` function and access those variables inside the `jsx` template. These variables are also called `context`

**index.js**

```js
const express = require('express')
const app = express();


// this line below, sets a layout look to your express project
const reactEngine = require('express-react-views').createEngine();
app.engine('jsx', reactEngine);

// this tells express where to look for the view files
app.set('views', __dirname + '/views');

// this line sets react to be the default view engine
app.set('view engine', 'jsx');

app.get('/', (req, res) => {
  // giving home.jsx file an object/context with `name` as a property
  const data = {name: "Sterling Archer"};
  res.render('home', data);
});

app.listen(3000);
```

then we need to update our `home.jsx` to use a templating variable.

**views/home.jsx**
```html
var React = require('react');
class Home extends React.Component {
  render() {
    return (
      <html>
        <body>
          <div>
            <h1>Hello, { this.props.name }!</h1>
          </div>
        </body>
      </html>
    );
  }
}

module.exports = Home;
```

The JavaScript being embedded is enclosed by the `{ }` tags.


## Pairing Exercise:

Start from scratch.

### Create your app

```
mkdir react-v
cd react-v
npm init
npm install express
npm install express-react-views react react-dom
touch index.js
mkdir views
touch views/home.jsx
```

Follow the examples above to get some HTML to render.

Use `this.props` to render some dynamic data in the HTML. (the `Sterling Archer` example)

Change the name value in the object to see the changes: `{name: "Sterling Archer"}` to `{name: "Susan Chan"}`

Add more keys into the object: `weight: 12324`.

Output the name as well as the weight.

### Further: With Google Data

#### Import some practice data

```
touch google.json
```

Paste the google shopping object into the json file: [https://raw.githubusercontent.com/wdi-sg/gitbook-2019/master/05-express/express-intro/views-data.json](https://raw.githubusercontent.com/wdi-sg/gitbook-2019/master/05-express/express-intro/views-data.json)

Make sure it worked ok, put this in your app.get:
```
jsonfile.readFile('google.json', (err, obj) => {
  console.log("OBJ ITEM ID~~: "+ obj.items[0].id );
  // put render here
})
```

Which should log an item id for you out to the terminal. This ensures you have proper access to the products.

#### Render a single product object in react

Implement an express route `/first` - it creates an HTML page with the first product in the array `obj.items[0]`.

This template should display at least 2 data fields for this item.

#### further
Implement a route with params:  `/items/:id`

Use `:id` to get the user according to it's index in the array

#### further
Change your code so that the param will be used to get the item by it's `googleId`.

For example: (127.0.0.1/items/11180453840663864493)[127.0.0.1/items/11180453840663864493]



