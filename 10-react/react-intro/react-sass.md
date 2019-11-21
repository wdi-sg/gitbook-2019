# React CSS

### Getting started
We will implement css and dynamic classes

Use this branch: [https://github.com/wdi-sg/react-reference/tree/4-react-sass](https://github.com/wdi-sg/react-reference/tree/4-react-sass)

Look at what we added: [https://github.com/wdi-sg/react-reference/compare/3-react-hotload..4-react-sass](https://github.com/wdi-sg/react-reference/compare/3-react-hotload..4-react-sass)

- sass
- state that changes element classes


Run the example app: `npm run dev` `node index.js`

Visit [http://localhost:3000](http://localhost:3000)

Inspect the elements and see what styles are applied. What classes are on the elements?

### classnames

We are using `classnames` to manage the list of classes we set on an element.

In this case whether or not we do that depends on `state`, specifically a boolean value.

`classnames` will take the boolean and produce the class string with the class name in it when it recieves a true value.

### Pairing Exercise

Clone the react repo into a named folder:

```bash
$ git clone https://github.com/wdi-sg/react-reference.git sass
```

Check out the hot laoding branch:

```bash
$ git checkout 4-react-sass
```


