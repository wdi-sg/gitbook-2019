# React Components

We rendered some HTML with react, now we will see one of the main concepts of React, the Component Class.

In the last example we saw that we can use react to render things just like we did in express and rails- where the HTML template is a kind of code mad-lib- You fill in the data where it needs to go in the page.

React does this at the base level, but we can also sub-divide each part of a page into `Component`s.

These are the sepearate logical pieces of any page.


![https://github.com/wdi-sg/react-intro/raw/master/images/templates-page.png](https://github.com/wdi-sg/react-intro/raw/master/images/templates-page.png)


![https://github.com/wdi-sg/react-intro/blob/master/images/components-page.png](https://github.com/wdi-sg/react-intro/blob/master/images/components-page.png?raw=true)


![https://github.com/wdi-sg/react-intro/blob/master/images/wireframe.png](https://github.com/wdi-sg/react-intro/blob/master/images/wireframe.png?raw=true)


![https://github.com/wdi-sg/react-intro/blob/master/images/wireframe_deconstructed.png](https://github.com/wdi-sg/react-intro/blob/master/images/wireframe_deconstructed.png?raw=true)



### Properties of Components
- separation of concerns
- nested / pass data down from parent
- F focused
- I independant
- R resuable
- S small
- T testable



## Writing a component

Begin with `home.jsx` view file:

```
var React = require('react');

class Home extends React.Component {
  render() {

    return (
      <div>
        <h1>Hello, { this.props.name }!</h1>
        <div>
          <ul>
            <li>Hello world</li>
          </ul>
        </div>
      </div>
    );
  }
}

module.exports = Home;
```

We'll replace the `ul` with a component that represents the list:

```
class List extends React.Component {
    render() {
        return (
          <div>
            <ul>
              <li>Hello world</li>
            </ul>
          </div>
        );
    }
}
```

Now put it in place of the `ul` tag:

```
return (
  <div>
    <h1>Hello, { this.props.name }!</h1>
    <List/>
  </div>
);
```

### Props - Component Properties
In react, a component takes data in and renders itself based on that data.

The data is passed from above in the parent component and becomes `this.props`

Let's pass one piece of data to the `List` component.

```
<List title="my list"/>
```

Use it inside the component:

```
class List extends React.Component {
    render() {
        return (
          <div>
            <h4>{this.props.title}</h4>
            <ul>
              <li>Hello world</li>
            </ul>
          </div>
        );
    }
}
```

#### props variables and data

```
let titleVariable = "wow title";

return (
  <div>
    <h1>Hello, { this.props.name }!</h1>
    <List title={titleVariable}/>
  </div>
);
```

Let's start rendering a real list from data coming from outside the list itself.

Specify the list like this:
```
const listOfItems = [
  "apples",
  "bananas",
  "pineapple"
];
```

Pass it into `List`:

```
<List title="my list" items={listOfItems}/>
```

Use it in the component:
```
class List extends React.Component {

    render() {

        let itemsElements = this.props.items.map(item => {
          return <li>{item}</li>
        });

        return (
          <ul>
            {itemsElements}
          </ul>
        );
    }
}
```


### Nesting Components
We mentioned that it's the nested structure of components using components that really makes react special.

Let's put our `<li>` tag data in it's own component.
```
class ListItem extends React.Component {

    render() {
        return (
          <li>{this.props.item}</li>
        );
    }
}

class List extends React.Component {

    render() {
        let itemsElements = this.props.items.map( (item, index) => {
                              return <ListItem item={item}/>;
                            });
        return (
          <ul>
            {itemsElements}
          </ul>
        );
    }
}
```

### Separate Files with require

**views/components/header.jsx**
```
var React = require('react');

class Header extends React.Component {
  render() {
    return (
      <div class="header">
        <h1>This is the header</h1>
      </div>
    );
  }
}

module.exports = Header;
```

**views/hello-message.jsx**
```
var React = require('react');
var Header = require('./components/header');

class HelloMessage extends React.Component {
  render() {
    return (
      <Header/>
      <div>Hello {this.props.name}</div>
    );
  }
}

module.exports = HelloMessage;
```


### Exercise

Use components with one of your apps.

Create a new jsx file:

```bash
touch views/papaya.jsx
```

```html
var React = require('react');
class Papaya extends React.Component {
  render() {
    return (
      <html>
        <head>
          <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css" integrity="sha384-MCw98/SFnGE8fJT3GXwEOngsV7Zt27NXFoaoApmYm81iuXoPkFOJwJ8ERdknLPMO" crossorigin="anonymous"/>
        </head>
        <body>
          <div> 
            <h1>Hello, { this.props.name }!</h1>
          </div>
        </body>
      </html>
    );
  }
}

module.exports = Papaya;
```


```
Paste a new route into an express app:
```js
app.get('/papaya', (request, response) => {

  const data = {name: "Sterling Archer"};

  response.render('papaya', data);
});
```

### Further

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

Render a list of items with a separate `GoogleItem` component.

```
render() {
    let itemsElements = this.props.googleItems.map( (item, index) => {
                          return <GoogleItem item={item}/>;
                        });
    return (
      <div>
        {itemsElements}
      </div>
    );
}
```

#### Further

Inside the `GoogleItem` component create separate components for keys like: `product`, `inventory`, `author`, etc.
