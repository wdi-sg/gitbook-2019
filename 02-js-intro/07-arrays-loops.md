# Loops

## Framing
- after conditionals loops are the other piece of control flow in any basic program. Every language you will write in the future will have some kind of loop in it.
- many times in our programs we need to specify a task to happen more than once. Loops help us do that.

![control flow wd40](https://i.imgur.com/v4W1xwD.png)


### Arrays

Arrays are ordered collection of related data types and are organized by index.
- Indexing begins at 0 (e.g., first element in an array has an index of 0, the second has an index of 1, and so on).


We instantiate an array like this...

```js
// Instantiate with an array literal.
var mountRushmore = [ "Washington", "Jefferson", "Roosevelt" ]
```

And access its values like so...

```js
mountRushmore[0]
// => "Washington"

mountRushmore[1]
// => "Jefferson"

mountRushmore[2]
// => "Roosevelt"

mountRushmore.push("Lincoln")
// mountRushmore = [ "Washington", "Jefferson", "Roosevelt", "Lincoln" ]

mountRushmore[3]
// => "Lincoln"

// You can also place arrays within arrays.
var letters = [ ["a","b","c"], ["d","e","f"], ["g","h","i"] ]

// How would we go about accessing the letter "f" in the above array?
letters[1][2]
// => "f"
```

### Array Methods

There are a lot of useful methods that come with Javascript we can use to inspect and modify arrays. To learn what some of them are...
* `.length`
* `.push`
* `.indexOf`

> There are many more, but these are the most widely-used.

#### `while`

A **while loop** repeatedly executes a code block as long as a specified condition is true.

```js
var i = 0;
while (i < 5) {
  console.log("i is " + i);
  i++;
}

// Will print out:
// >i is 0
// >i is 1
// >i is 2
// >i is 3
// >i is 4
```

---

**The parts of a while loop**

```
while (CONDITION) {
  //CODE
}
```

```
var i=0;

while (i < 5) {

  console.log("i is " + i);

  i++;
}
```

---

Loop that runs forever
```
while(true){
  //CODE
}
```

### arrays and loops

```
var i=0;

var a = [1,2,3];

while (i < 5) {

  console.log("i is " + a[i]);

  i++;
}
```



## Backwards Loops

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


### Exercise: Run some loops (10 mins)

- Setup Your Files (html / script)
- Copy the above code examples
- Change the value of i to something bigger
- Change the condition from *less than* to *less than or equal to* - what happens?
- Change the starting value of i to something else. What happens?
- Make a while loop that runs 1000 times and console.logs out `i`.
- Make a while loop that runs 1000 times and console.logs out `hello`
- Make a backwards loop
- Make a loop that increments more than one (counting forwards and backwards) 
- Make a loop that runs a random amount of times (up to a reasonable number) - just google how to create a random integer in javascript if you don't know how.
- Crash your chrome browser tab by running a while loop that console.logs something and goes on forever.
