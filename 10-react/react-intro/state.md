# React Render Timing / State

### React Rendering

Now we can talk about the real differentiation of the react library.

When we render something in react, the library is actually keeping track of something called a virtual DOM. When it sees changes it will call the appropriate `render` methods to output HTML.

The problem this is solving is that it turns out to be much faster to keep track of the DOM in javascript than it is *within the real DOM*.

The real work of building a react app is understanding this rendering cycle.

![https://docs.google.com/drawings/d/11ugBTwDkqn6p2n5Fkps1p3Elp8ZToIRzXzvM4LJMYaU/pub?w=543&h=229](https://docs.google.com/drawings/d/11ugBTwDkqn6p2n5Fkps1p3Elp8ZToIRzXzvM4LJMYaU/pub?w=543&h=229)

![https://calendar.perfplanet.com/wp-content/uploads/2013/12/vjeux/4.png](https://calendar.perfplanet.com/wp-content/uploads/2013/12/vjeux/4.png)

So we know about React properties, and how they relate to our component's data.
* The thing is, `props` represent data that will be the same every time our component is rendered. What about data in our application that may change depending on user action?
* That's where `state` comes in..

Values stored in a component's state are mutable attributes.
* Like properties, we can access state values using `this.state.val`
* Setting up and modifying state is not as straightforward as properties. It involves explicitly declaring the mutation, and then defining methods to define how to update our state...

If we want to trigger a rerender in our component then we have to keep track of an attribute in a specially named attribute called state.

Specifically if we want to trigger a rerender then we need to mutate that state with the method `setState`.

```js
class Item extends React.Component {

    //initialize the component
    constructor(){
      super()
      console.log("constructing");

      this.state = {
        counter : 0
      }

    }

    // our click method
    handleClick(){
      let currentValue = this.state.counter + 1;

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

### Immutability
When we give values to `setState`, look carefully- these are actually new values.

React calls the render function of each component again in order to recieve the current "DOM" of each component.

When we are mutating an array we use spread operators so that the thing we pass to `setState` is a new thing. We do not use push, which would transofrm the array in place.

```js
class Item extends React.Component {

    //initialize the component
    constructor(){
      super()
      console.log("constructing");

      this.state = {
        numbers : []
      }

    }

    // our click method
    handleClick(){
      let currentValue = Math.random();

      console.log("clicking", currentValue);

      // set the state of this component
      this.setState( { numbers: [currentValue, ...this.state.numbers] } );
    }

    // what happens when the component renders
    render() {

        const numbers = this.state.numbers.map((number)=>{
          return <p>{number}</p>;
        });

        console.log("rendering");
        return (
          <div>
            <button onClick={()=>{this.handleClick()}}>click me!</button>
            {numbers}
          </div>
        );
    }
}

ReactDOM.render(
    <Item />,
    document.getElementById('root')
);
```

### Virtual DOM
Under the hood, react keeps track of which elements have changed and which have not.

Even though it seems like *every* DOM element is re-rendered using the `render` function, actually react is smart enough to figure out which elements are being changed.


Assume this component gets props from it's parent:
```
<Display item={this.state.counter}/>
```

When a new piece of data is passed, we can see if the whole component changes on the screen, or just the appropriate parts:

(inside of `Display`)
```
<div>
  <p>{this.props.item}</p>
  <p>
    <input/>
  </p>
</div>
```

If we type in the input, the users value should get refreshed by react, and go away.

### Exercise
Run the above code. See the virtual dom leave certain parts of the page alone as it changes others.

### further
Build some regular javascript code that manipulates the dom in a loop.

How long does it take?

How long does it take if you build the equivalent code in react?

```
for( var i=0; i<1000; i++ ){

  var p = document.createElement('p');
  p.innerHTML = Math.random();
  document.body.append(p);
}

// manipulate the dom
var ps = document.querySelectorAll('p');
ps.map((paragraph)=>{
  paragraph.innerHTML = Math.random();
});
```
