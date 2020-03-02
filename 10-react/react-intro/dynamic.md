# React Render Timing / State

## props / render function

So far we have been able to manipulate the dom, getting things to render based on data.

Now, we will dynamically render react components **based on user action**.

## DOM Manipulation / State

In react the way to cause react to manipulate the dom is:

- put your data in a *different* object called `state`
- when your user has made an action / your data has changed, call `this.setState`
- this causes react to call the render function of the component again. the new `state` values are subsituted for the old ones.

### Click Handlers

```
clickHandler(){
  console.log("clicking");
}

render() {
    console.log("rendering");
    return (
      <div className="item">
        <button onClick={()=>{this.clickHandler()}}>YAY</button>
      </div>
    );
}
```

## React State
Now we have a button that can be clicked.

Let's change some attribute of the class, a counter that gets incremented.

```
clickHandler(){
  console.log("clicking", this.counter);
  if( this.counter === undefined ){
    this.counter = 1;
  }else{
    this.counter++;
  }
}

render() {
    console.log("rendering");
    return (
      <div className="item">
        <button onClick={()=>{this.clickHandler()}}>YAY</button>
      </div>
    );
}
```

This code increments the value, but what happens when we try to output it?

```
<p>{this.counter}</p>
```

We can see that the class attribute gets incremented, but the screen doesn't change.

### Dynamic React Rendering


```js
class Item extends React.Component {

    constructor(){
      super();

      console.log("constructor");

      // set the default value
      this.state = {
        counter:0
      };
    }

    // our click method
    handleClick(){

      var currentValue = this.state.counter + 1;
      console.log("clicking", currentValue);

      // set the state of this component
      this.setState( { counter: currentValue } );
    }

    // what happens when the component renders
    render() {
        console.log("rendering");
        return (
          <div>
            <span>{this.state.counter}</span>
            <button onClick={()=>{this.handleClick()}}>click me!</button>
          </div>
        );
    }
}

ReactDOM.render(
    <Item />,
    document.getElementById('root')
);
```

### Static React Rendering
We pass data into a component using props.

```
class Banana extends React.Component {
    render() {
        return (
          <div>
            <p>count: {this.props.count}</p>
          </div>
        );
    }
}

ReactDOM.render(
    <Banana count={0}/>,
    document.getElementById('root')
);
```

`props` can never be altered **inside** the component
```
class Banana extends React.Component {

    increment(){
      // makes an error
      this.props.counter++;
    }
    render() {
        return (
          <div>
            <p onClick={()=>{this.increment()}}>count: {this.props.counter}</p>
          </div>
        );
    }
}

ReactDOM.render(
    <Banana counter={0}/>,
    document.getElementById('root')
);
```
### Re-rendering with props

If `state` is passed into a component, it becomes `props`.

```
<Count counter={this.state.counter} />
```

If we have a sub component that takes in a changing prop, that component also gets rerendered:
Let's put our span inside it's own component:
```
<span>{this.state.counter}</span>
```
changes into:
```
<Count counter={this.state.counter}/>
```

When you pass new props to a component, it gets re-rendered.

```
class Count extends React.Component {

    render() {
        console.log("rendering count component");
        return (
          <div>
            <span>{this.props.counter}</span>
          </div>
        );
    }
}
```

### Default Data

```
//initialize the component
constructor(){
  super()
  console.log("constructing");

  this.state = {
    counter : 0
  }

  }
```

### Pairing Exercise

Clone the react repo into a named folder:

```bash
$ git clone https://github.com/wdi-sg/react-reference.git state
```

Check out the hot laoding branch:

```bash
$ git checkout 3-react-hotload
```

Build the above counter increment.

Watch the console to see when clicking and rendering happen.

#### Further
Build the counter display into it's own component.

#### Further
Make a second and third button that increments by 2 and 3. Send those props to the display component.

Display the current count and an array of previous values in the display component.
