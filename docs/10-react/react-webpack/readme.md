# webpack

Webpack is the *asset pipeline* like tool that transforms and packages our js in development mode and production.

We are going to be seeing a default configuration that includes an express app. (since you would never write a react app on it's own without some kind of backend)

We'll walk through all of the features provided to you by this setup.

### Starting app template:
[https://github.com/wdi-sg/react-express-webpack](https://github.com/wdi-sg/react-express-webpack)

## Parts of the system:

- nodejs - runs webpack and the express server

    - express

    - webpack
        - transforms things:
            - babel - transforms jsx to js
            - sass - transforms sass into css
            - html-webpack-plugin
        - runs the nodemon / live reload server in development environment
        - runs the code linter, gives you warnings and errors when your code breaks a rule



### Express
Any server application code you write goes in the `server` directory.

Uses `package.json` normally like the previous express apps. Dependencies are listed here. Scripts for starting the server live here.

##### src/server/index.js
Is the normal express main js file. This is also where you run your webpack development server from.

### webpack config
Is separated into common, production and development environments.

#### package.json
Lists all of the npm commands to start the dev server and run the production build on its own

#### Babel & React

Takes the code you write and transforms it before it gets to the browser.

- `babel-core`: Transforms your ES6 code into ES5
- `babel-loader`: Webpack helper to transform your JavaScript dependencies (for example, when you import your components into other components) with Babel
- `babel-preset-airbnb`: Determines which transformations/plugins to use and polyfills (provide modern functionality on older browsers that do not natively support it) based on the browser matrix you want to support
- `babel-preset-react`: Babel preset for all React plugins, for example turning JSX into functions

```
rules: [
  {
    test: /\.(js|jsx)$/,
    exclude: /node_modules/,
    use: {
      loader: "babel-loader"
    }
  }
```

Webpack uses a library `module` to do each type of code transform. Each rule runs a loader according to the `test`.
See [here](https://github.com/webpack/docs/wiki/list-of-loaders) for a definitive list.

This rule is telling webpack to run babel.

##### .babelrc
Create a file that tells babel how to transpile the code it is given.

`airbnb` refers to `babel-preset-airbnb`, which handles all of the ES6 syntax. (See details [here](
https://www.npmjs.com/package/babel-preset-airbnb)).

```js
{
  "presets": [
    [
      "airbnb",
      {
        "modules": false
      }
    ],
    "react"
    .
    .
    .
```

##### html-webpack-plugin
this plugin creates an index.html file that has all the correct script and link tags for us, and puts it in the static directory of the express app.

If you look inside the `src/client/index.html` you see what it looks like before it's transformed by webpack. Find the final version in `build/client/index.html`

##### webpack-dev-server

We can run the build and refresh the browser for each code change we make, or we can use the `nodemon` equivalent, `webpack-dev-server`.

We build upon webpack-dev-server to also include `react-hot-loader` for the complete react development environment.

Not only does the library know about any changes, but it will update your code on the fly- it doesn't require a refresh, and you don't lose the state of your app!

> Note that certain kinds of changes or situations require you to refresh anyways. If your code is behaving strangely, try a refresh first.

##### webpack-dev-server express
nodemon is enabled for the server. webpack-dev-server will stop working, though, and you will have to reload the page.

##### sass in react
We can use sass in react, with some added features that aren't in rails.

We can isolate the css for each component so that we don't have to worry about over-writing styles for the `button` class.

Also, it allows us to write CSS any apply it using `react-hot-loader`, without refreshing the browser, or losing application state. -This is especially helpful for error states.

The sass / react CSS compiler will automatically prefix the styles for us.
> See the settings for that [here.](https://github.com/wdi-sg/react-express-webpack/blob/master/config/webpack.config.common.js#L37)

This means we need to change 3 things about the way we write CSS.

1. styles for any component go in the directory for that component.
1. we have to import and then use styles as a js object.
1. naming anything has to change from hyphens to camel case, so that we can access it as js keys:
```
import styles from './style.scss';
```
```
return <p className={styles.titleName}>cheese and rice</p>;
```


### building for production
Create all the static files in `build`:
```
npm run build
```
Start the express server
```
npm run start
```

## webpack linting
Webpack allows us to setup a default environment that will also tell us if our code conforms to a styleguide.

### linting with airbnb presets
See the guide here: [https://github.com/airbnb/javascript](https://github.com/airbnb/javascript)

This requires us not to support some ES2017 functionality, like generators.

It also lints with [`prettier`](https://prettier.io/)

## propTypes
Airbnb js style requires us to specify the prop data types.

This is another safeguard to make sure that we don't put in any unexpected data types into our components. It's another workaround to the javascript falsy/truthy feature (`==` vs. `===`)

Note that `propTypes` is *NOT* form validation. This is more about surfacing subtle `==` vs. `===` errors to you, the programmer, than it is about user messaging, i.e., your password length is too short.

### Using propTypes
```
import PropTypes from 'prop-types';
class Monkey extends React.Component {
.
.
.
}
Monkey.propTypes ={
  message: PropTypes.string.isRequired
};

export default Monkey;
```

See a more complete list of types here: [https://www.fullstackreact.com/p/appendix-a-proptypes/](https://www.fullstackreact.com/p/appendix-a-proptypes/)

### More Resources:
Do you want asset pipeline-like controls over asset urls? Check out the webpack [`file-loader`](https://github.com/webpack-contrib/file-loader)

Webpack sass: [https://github.com/webpack-contrib/sass-loader](https://github.com/webpack-contrib/sass-loader)

#### react dev tools chrome extension
Find it [here.](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en)

### Starting app template:
[https://github.com/wdi-sg/react-express-webpack](https://github.com/wdi-sg/react-express-webpack)


### pairing exercise
Clone the starter code repo and add one component into the app:

  - create a folder in the app for the component in `/components`
  - add the component jsx file
  - import it in another component to use it

#### further
Add CSS to the component

