## CSS Classes and Dynamic Styles

Acessing, getting, setting CSS classes is slightly different than other properties.

Using a series of classes is the most efficient way to style an element using the DOM.

## className

First you can directly access the class attribute by using the `className` property of a DOM element. This works fine, but since elements can have multiple classes (separated by spaces) this often leads to needing to do some string parsing.


## classList

To solve the problem of not wanting to do string parsing of the `className` property browsers support the `classList` attribute which gives us an array of classes.

Additionally, the classList attribute has some special methods attached to it.

* add - add a class
* remove - removes a class
* contains - checks if an item has a class



**Usage**

```js
//list classes
item.classList

//add a class
item.classList.add('my-new-class');

//remove a class
item.classList.remove('my-new-class');

//check if an item has a class (returns true or false)
item.classList.contains('my-new-class');
```

### Changing Element State

Classes can be used to set/unset an unlimited number of CSS styles on a single element, by putting those styles in a class and putting the class on the element.

```css
.exciting{
  background-color:yellow;
  color:red;
  font-size:20px;
}

.normal{
  background-color:white;
  color:black;
  font-size:10px;
}
```

Make an item exciting
```js
//add a class
item.classList.remove('normal');
item.classList.add('exciting');
```

Make an item normal
```js
item.classList.remove('exciting');
item.classList.add('normal');
```

### Add / Remove Elements

```css
.hide{
  display:none;
}

.normal{
  display:block;
}
```

Hide something
```js
item.classList.remove('normal');
item.classList.add('hide');
```

Show something
```js
item.classList.remove('hide');
item.classList.add('normal');
```

### Pairing Exercise
Begin with an empty `index.html` `script.js` and `style.css`

Create a button and a display div

```HTML
<div class="display normal">wow</div>
<button id="my-button">click here</button>
```

When the button gets clicked, make the display div exciting by adding the class above.

When it is clicked again, make the display div normal. (use a world state value to keep track of the current state)

### Further

Add another div
```HTML
<div id="message" class="display message">
  exciting mode
</div>
```

When the button is clicked, also make this div appear. When you click again, make it dissapear.

### Further

Add a third state, `very-exciting`. When the button is clicked for a 3rd time, change to this state. On the next click, turn it normal again.
