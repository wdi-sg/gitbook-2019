# React Forms

Taking form input works much like the button in react. An event is set to an element and we render changes based on those events.

Let's change the button to a form input.

```
constructor(){
  super()

  this.state = {
    word : ""
  }
}

changeHandler(event){
  this.setState({word:event.target.value});
  console.log("change", event.target.value);
}

render() {
    console.log("rendering");
    return (
      <div className="item">
        {this.state.word}
        <input onChange={(event)=>{this.changeHandler(event);}}/>
      </div>
    );
}
```

Now what if we want to control what the user sees in the input when they type?

We can update the input using `value`.

```
<input onChange={(event)=>{this.changeHandler(event);}} value={this.state.word.toUpperCase()}/>
```

This is using a pattern called [Controlled Components](https://reactjs.org/docs/forms.html).

We control what comes out of the form and what goes into `state`.

We listen to the value coming out of the form with `onChange` and we control the current value of the form with `value`.

We can also use it to validate an input.

```
// this form input will set state on anything except 'a'
changeHandler(event){
  if( event.target.value != 'a' ){
    this.setState({word:event.target.value});
  }
  console.log("change", event.target.value);
}
```

### Exercise
Implement the above form in react.

Clone the react repo into a named folder:

```bash
$ git clone https://github.com/wdi-sg/react-reference.git forms
```

Check out the hot loading branch:

```bash
$ git checkout 4-react-sass
```

#### further
Create validation on the form. Use the react `className` to set a css class on the form that tells the user that their input is invalid.

Example: User's input can't be longer than 6 characters. After 6 characters, apply the `warning` class to the input.

```
.warning{
  border: 1px solid red;
}
```

#### further
When the form input reaches 5 characters, change the input value to all capital letters.

#### further
Change the form to never display the letters the user types in the input. Instead, display them in an `h1` tag.
