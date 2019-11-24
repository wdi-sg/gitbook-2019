## React "Lifting" Functions

One very important descision every react developer has to make is how to structure the app and which component will be responsible for holding the data.

Because data can cause elements to re-render we should keep data as low down in the tree of elements as possible. This keeps each piece as separate and modular as possible.

There will be many cases in which the data that you use in one component in the tree is needed in a *sibling* component.

![https://github.com/wdi-sg/react-intro/blob/master/images/wireframe_deconstructed.png?raw=true](https://github.com/wdi-sg/react-intro/blob/master/images/wireframe_deconstructed.png?raw=true)

For this example let's take the `Line` component.

There could be many features that are implemented in this component:
  - conditional rendering of the drop down options
  - rendering the drop down options from an ajax call to get train line conditions
  - etc., etc.

However, from the wireframe it's most likely that the drop down affects the main `Predictions` component.

In this case, where the selected line affects another sibling component, where do you store that state?

The lowest place in the element tree with these two components in common is actually still at the top level of this page. (Which is fine, and mostly unavoidable)

In this case we have to store the actual state in the top level.

The technique for doing this is called "lifted" functions.

#### Lifted Functions
If we want state to be available for 2 sibling components, we have to store it in the closest parent.

In order to set state on a parent component we *must* call a method on the parent component.

When the state is set on the parent, it will pass back down the data set in the method.

```

class App extends React.Component{

	constructor(){
		super();
		this.state = {
			station : "banana"
		};

	}

  setCurrentStation(station){
    this.setState({station})
  }

  render(){
    return (
      <div>
        <Line setCurrentStation={(s)=>{this.setCurrentStation(s)}} station={this.state.station}/>
        <Trains station={this.state.station}/>
      </div>
    );
  }
}

class Line extends React.Component{

  render(){
    return (
      <div>
        <h1>{this.props.station}</h1>
        <button onClick={this.props.setCurrentStation}/>
      </div>
    );
  }
}

class Trains extends React.Component{

  render(){
    return (
      <div>
        <h1>{this.props.station}</h1>
      </div>
    );
  }
}
```

### Exercise
Implement a currency exchange form in react.

Clone the react repo into a named folder:

```bash
$ git clone https://github.com/wdi-sg/react-reference.git lifting
```

Check out the hot laoding branch:

```bash
$ git checkout 4-react-sass
```

##### Features

For a number of Singapore dollars it shows the amount of other denominations of another currency.

This form exists in a `Form` component.

Implement a sibling component that displays the number of yen you would get for the number entered in the `Form` component.

This sample shows the hierarchy of the components you should end up with: (this is not actual code)
```
  <Exchanger>
    <Form setSgd={this.setSgd}/>
    <Yen sgd={this.state.sgd} />
  </Exchanger>
```

The `sgd` state is stored inside the `Exchanger` component.

`sgd` is given as props to a `Yen` component.

This component contains the logic / formula to convert from `sgd` to yen.

`Form` component contains an input that the user enters an amount of sgd in.

##### further
Implement components for other currencies. (US Dollars, Ringet, Thai Baht, etc.)

##### further
Refactor the form so that you can select the currency in the form. Then the user enters the amount in that currency into the form.

Change each currency component to take 2 properties instead:
```
<Yen currency={this.state.currency} amount={this.state.amount} />
```
