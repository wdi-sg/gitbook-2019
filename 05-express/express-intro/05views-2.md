# React Views With Data

### Conditional Rendering
Sometimes we want to decide to render something based on a variable.

We can put this code directly above the return statement, or we could also write it in another function.
```
var React = require('react');

class Home extends React.Component {
  render() {

    let message = "welcome!";

    if( name.length > 5 ){
      messgae = "welcome! What a long name you have!";
    }

    return (
      <div>
        <h1>Hello, { this.props.name }!</h1>
        <h1>{ message }</h1>
      </div>
    );
  }
}

module.exports = Home;
```

### Map
The ES6 array method `map` allows us to return an array.

We can use `map` to create HTML in a loop.

Say we have the following `context` given to our `jsx` template.
```js
var context = {
  people: [
    "Yehuda Katz",
    "Alan Johnson",
    "Charles Jolley"
  ]
}
```

```
var React = require('react');

class Home extends React.Component {

  render() {

    const people = this.props.people.map( person => {
      return <li>{person}</li>
    });

    return (
      <div>
        <ul>
        {people}
        </ul>
      </div>
    );
  }
}

module.exports = Home;
```


### HTML Attributes

HTML attributes in react are written without the quotes by default:

```
<img src={pokemon.img} />
```

If you need to do string interpolation, create another variable:
```
let formAction = '/pokemon/' + pokemon.id;
```

```
<form action={formAction}>
```

CSS class names are set with `className` instead of `class`
```
<p className="banana">yes</p>
```

## Pairing Exercise

#### Create your app

```
mkdir react-views2
cd react-views2
npm init
npm install express
npm install express-react-views react react-dom
touch index.js
mkdir views
touch views/home.jsx
```

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

Implement an express route `/first` - it creates an HTML page with the first user in the array `products.items[0]`.

This template should display at least 2 data fields for this item.

##### Conditionals
Display the tax of the stock availablity:

```
<p>Tax: {tax}</p>
```

Some of the `inventories` records will not have a tax field. If the inventory is missing the `tax` field, don't render the `p` tag at all.

#### Render Multiple Items in a Loop

Implement an express route `/items` - it creates an HTML page with all of the items.

This will be a `<ul>` with an `<li>` for each item.

Use the `map` syntax above to render the list.

This template should display the title for each item.

#### Render More Data
Display the title, description and the inventory stock availability.

#### further
Render the rest of the data in the object.



