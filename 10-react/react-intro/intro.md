# Browser Side React

We will use react library to manage the DOM in the browser without using the `document` variable in the javascript.

### React Benefits

- clear separation of data and 'presentation'
- cleaner than DOM manipulation
- split your page code up into 'components'
- installable components with npm


## JSX Transpile
`babel` is the tool that takes `jsx` and transforms it into `React.createElement`.


### Getting started
We will implement the webpack asset pipeline for the jsx code we need to write in this unit.

Use this branch: [https://github.com/wdi-sg/react-reference/tree/2-react-jsx-intro](https://github.com/wdi-sg/react-reference/tree/2-react-jsx-intro)

Look at what we added: [https://github.com/wdi-sg/react-reference/compare/2-react-jsx-intro..1-webpack-intro](https://github.com/wdi-sg/react-reference/compare/2-react-jsx-intro...1-webpack-intro)

- `@babel/plugin-transform-react-jsx` npm library that can transform jsx to javascript
- `.babelrc` file that tells babel to transform jsx using this library
- `react` added as a dependency to our project
- change the main file from `js` to `jsx`, and put a react component inside


### Jsx causes a browser error.

Open your chrome dev tools and paste this in. What do you see? What happens?
```js
class Banana extends React.Component {
    render() {
        return (
          <div>Hello world</div>
        );
    }
}
```

### Building index.jsx

Run the example app: `npm run build` `node index.js` Visit [http://localhost:3000](http://localhost:3000) Open the generated `main.js` file. Scroll to the bottom. What do you see?

Add one new element in the div: `<p>wow</p>`. Rerun the build command. How does that change the main.js file?

### Pairing Exercise

Clone the react repo into a named folder:

```bash
$ git clone https://github.com/wdi-sg/react-reference.git jsx-intro
```

Check out the jsx branch:

```bash
$ git checkout 2-react-jsx-intro
```


Add a root element to the page

```html
<div id="root"></div>
```

Render the component

```
ReactDOM.render(
    <Banana/>,
    document.getElementById('root')
);
```

Repeat the above.

#### Further

In the return, create more complicated elements by adding them one at a time:

```HTML
<div>
  <p>wow</p>
  <ul>
    <li>my item</li>
    <li>another item</li>
    <li>
      <a href="/hahah">click me</a>
    </li>
  </ul>
</div>
```

How does this affect main.js?


#### Further

```bash
touch form.jsx
```

Write an input component in `form.jsx`. Don't forget to export this component.

Import this file into `index.jsx` and use the component inside.

#### Further
Make more nested components and files for each component.
