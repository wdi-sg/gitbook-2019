# View Layouts
Sometimes you want the same surrounding HTML for each template - for example your head or body tags don't change with each different page.

First, pass the relevant props to a layout component.

`views/layouts/default.jsx`:
```js
var React = require('react');

class DefaultLayout extends React.Component {
  render() {
    return (
      <html>
        <head><title>{this.props.title}</title></head>
        <body>{this.props.children}</body>
      </html>
    );
  }
}

module.exports = DefaultLayout;
```

We can use `this.props.children` to magically fill in things from our other file.

Then use that surrounding component inside your template.

`views/index.jsx`:
```js
var React = require('react');
var DefaultLayout = require('./layouts/default');

class HelloMessage extends React.Component {
  render() {
    return (
      <DefaultLayout title={this.props.title}>
        <div>Hello {this.props.name}</div>
      </DefaultLayout>
    );
  }
}

module.exports = HelloMessage;
```
