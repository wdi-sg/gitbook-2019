## CSS Classes

Acessing, getting, setting CSS classes is slightly different than other properties.



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

### Add / Remove Elements


### Pairing Exercise
