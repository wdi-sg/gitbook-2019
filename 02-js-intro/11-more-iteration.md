## Other Array Iteration Patterns:

### Counting One Item in an Array

Write a function called `inventory` that accepts an array of strings representing
a store inventory and accepts a string representing a product. Return the total
number of times the product occurs in the array.

```js
  var inventory = ["toothbrush","cap","shampoo","mars bar","banana"];

  var product = "toothbrush";

  var tally = 0;

  var i = 0;

  while( i < inventory.length ){

    if (inventory[i] === product) {
      tally++;
    }
    i = i + 1;
  }

  console.log( tally );
```

### Double For Loops / Nested For Loops

If you have a piece of data that is structured as a grid, you might want to visit every value.

```js

  var a = [
    [2,3,5],
    [6,3,4],
    [7,6,5]
  ];

  // look in every index
  for (var i = 0; i < a.length; i++) {

    for (var j = 0; j < a[i].length; j++) {
      console.log(a[i][j]);

    }
  }
```

### Array of Objects

Accessing each nested value whether it's an array or an object works similarly.

```js

var cats = [
  {
    name: 'fluffy',
    weight: 12,
    allergies : ['feathers', 'chocolate']
  },
  {
    name: 'susan chan',
    weight: 13,
    allergies : ['tea', 'dust']
  },
  {
    name: 'chee kean',
    weight: 8,
    allergies : ['dairy']
  }
];

var i = 0;

while( i < cats.length ){

  var saying = cats[i].name + ' is ' + cats[i].weight + ' kilos.'
  console.log( saying );

  // use a nested for loop to print out the allergies

  var allergies = cats[i].allergies;

  var j = 0;

  while( j < allergies.length ){
    console.log( cats[i].name + ' has an allergy to: ' + allergies[j] );
    j = j + 1;
  }

  i = i + 1;
}
```

### Pairing Exercise:

Create an index.html and script.js file.

Run the above code.

### Further
Try this exercise: [https://github.com/wdi-sg/google-shopping-conditionals-loops](https://github.com/wdi-sg/google-shopping-conditionals-loops)


### Extra: Other Array Patterns

## Backwards Array Access

It's totally possible to run the loop backwards. We need to do three things:

1. Instead of starting i at zero
simply start it at `var i = a.length`. We have to subtract one from the length
of the array to access the index of the last element to account for zero-based
indexing.
2. Change the test condition to run the for loop while `i > 0`
3. Change the step instruction to `i--`

```
var a = [1,2,3];

var i=a.length;

while (i > 0) {

  i--;

  console.log("i is " + a[i]);
}
```

### Reversing an Array
The same idea can be applied to reverse an array. Create a new empty array
and push elements into it.

```
var a = [7,8,9,10,11];

var result = [];

var a = [1,2,3];

var i=a.length;

while (i > 0) {

  i--;

  result.push(a[i]);

  console.log("i is " + a[i]);
}

console.log( result );
```

### Fencepost Problems

Sometimes we need to do special things at the beginning or end of when we're
iterating over an array.

Imagine a fence. A fence looks like this: `|=|=|=|=|'. This fence has five
fence posts and four, uh, pieces of fence.

There's a discrepency there! If we were writing a for loop to build a fence should
it run five times to place each fence post, or should it run four times to place
each piece of fence?

Consider this psuedo code that tries to place four pieces of fence:

```js
var i = 0;

while( i < 4 ){

  console.log("=");
  console.log("|");

  i = i + 1;
}
```

The output of this code would build a fence like this: `=|=|=|=|`. There are
correctly four pieces of fence, but we're missing a fence post at the beginning!

If we switch the order of calling the `placeFence` and `placePost` methods then
we end up missing a fence post at the end of the fence.

```js
var i = 0;

while( i < 4 ){

  console.log("|");
  console.log("=");

  i = i + 1;
}
```

This code produces a fence like this: `|=|=|=|=` without the last fence post at
the end.

The proper way to deal with a "fence post" scenario is to place one post before
or after the for loop.


```js
console.log("|");
console.log("=");

var i = 0;

while( i < 4 ){

  console.log("=");
  console.log("|");

  i = i + 1;
}
```

This code properly produces a fence with posts on each end, and fence pieces
between each post, like this: `|=|=|=|=|`.


### One-Way Gates

Write code that uses an array of integers and outputs the
largest value in the array.

This problem requires us to create varaibles to store extra information outside
the for loop. We'll use if statements inside the for loop to update these variables
when certain conditions are met.

```js
  var a = [3,4,5,6,1,2];
  var largest = 0;
  var i = 0;

  while( i < a.length ){

    if (a[i] > largest) {
      largest = a[i];
    }

    i = i + 1;
  }

  console.log( largest );
```

Notice that we initialize `largest` outside of the for loop and output it at the
end. We compare each value in the array to the value and rewrite
the value of `largest` if we ever see something in the array larger than it.

There's a problem with initlializing `largest` to zero. Imagine passing an array
of negative numbers to this function. If the largest number in the collection
were `-12` this function would incorrectly return zero!

## String Builders

Some problems require building up a final result. A Classic example is traversing over
a string backwards to produce a reversed string.

Set up a variable outside the for loop to keep track of the final result.

```js
  var s = "hello";

  var result = "";


  var i = 0;

  while( i < a.length ){
    result += s.charAt(i);


    i = i + 1;
  }

  console.log( result );

```

### Double For Loops / Nested For Loops

Sometimes it's useful to nest a for loop inside a for loop. This code tests to
see if an array contains unique elements by comparing each item in the array
to every other item.

Use another variable name other than `i` for the second for loop. `i, j, k, n`
are common for loop variable names.

```js

  // let's see if there are duplicate values in the array
  var a = [2,3,4,5,1,2,3,9];

  // look in every index
  for (var i = 0; i < a.length; i++) {

    // compare this index against every other index
    for (var j = 0; j < a.length; j++) {

      // make sure we are not comparing to itself
      if (j !== i) {

        // do the comparison
        if (a[i] === a[j]) {
          console.log("double!: "+a[i]);
        }
      }
    }
  }
```



