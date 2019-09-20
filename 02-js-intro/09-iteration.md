# Arrays and Iteration

## Arbitrary Sized Data

Most data has an arbitrary length.

How do we tell our programs how to process this data?

We use the data collection type `array`. Then we look at each item using a `loop`.

## What is iterating over an array?

If an array is data that is of different possible lengths, we need syntax that will look at *every* value in the array.

We can combine a loop with an array to get this syntax.

## Looking at one element at a time

This is the simplest way of iterating over an array. We write a for loop
that starts at `0` and goes while the value of `i` is less than the length
of the array.

Notice that this for loop correctly won't print anything out for an empty array.

```js
var a = [1,4,2,3,6];

var i = 0;
while( i < a.length ){

  console.log( a[i] )

  i = i + 1;
}
```

### For Loop

For loop is a syntax that takes a while loop condition and combines it with iteration into one structure.

```
for( var i=0; i<10; i++ ){

  console.log( i + " times" );
}
```

### Exercise 1:

Create an `index.html` file and `script.js` file.
Run each example one at a time, .
Create a `console.log` for each interation of the array.

Make sure to format the output well so it is clear what is happening.

e.g. `console.log('iteration: '+i)` instead of `console.log(i)`.

### Further:

Investigate different ways go get values out of an array:
- what if you start `i` at different values?
- what if you change the condition to `<=`?
- what if you change the iteration? i.e., `i = i + 2;`


### Further:

Use a loop to iterate over this array:

```
var numbers = [4,2,3,1,2,3,4,5];
```

Write code that sums all the numbers and `console.log`s them.

Write code that sums all the *even* numbers in the array and `console.log`s them.

### Further:

```
var singaporeTemperaturesThisMonth = [30,31,38,37,35,28];
```

Write code that averages the numbers.

### Further:

Look at the above array in the reverse order.

### Further:

Use the interactive template. When the user enters a number, put it into an array.
Average the numbers in the array and show the number to the user.

### Further:

Using the code above, make some changes:

Show all the values in the array to the user.

The user will enter in a number corresponding to the index of the array. They have selected this value from in the array.

Then the user will enter in a number. Add together the number and the value they selected and show it to the user.
