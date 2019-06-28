# Loops and Arrays - Arbitrary Length Data

After conditionals and functions, loops are the other piece of control flow in any basic program. Every language you will write in the future will have some kind of loop in it.

### Arrays

An array is a list of data. If a variable is the simplest way to store a value, a bucket, an array is a bucket of buckets.

Each item in an array can be accessed individually by it's location, or *index*. Indexes start at zero.


```js
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

```

Further examples:
```
var numbers = [3,5,7,8,9];

numbers[0] // 3
numbers[4] // 9
```

```
var  = [true,false,false,true];

numbers[0] // true
numbers[3] // true
```

```
var height1 = 12;
var height2 = 2;
var height3 = 112;
var heights = [height1, height2, height3];

height[0] // 12
height[2] // 112
```

### Arrays as Data
Arrays represent lists of the same kind of data.

The also suggest an order of data, as in an ordered / ranked list.

They can be of "fixed" length, or they can be variable length.

```
var singaporeTemperaturesThisMonth = [30,31,38,37,35,28 ... ]
singaporeTemperatures[3] // last month on the 4th day the temp was: 37
```

```
var alphabet = ['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z'];

alphabet[3] // d
```

Again, the naming and format of that data determine what operations you want to do on the data.

### Array Methods

* `.length`

* `.push` put something on the end of the array
* `.pop` take something off the end of the array

* `.shift` put something on the beggining of the array
* `.unshift` take off the first thing in the array

> There are many more, but these are the essential ones

##### length

```
var alphabet = ['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z'];

alphabet.length // 26
```

##### push

Put something on the end of an array.

```
var singaporeTemperaturesThisMonth = [30,31,38,37,35,28];
// singaporeTemperaturesThisMonth[0] gets the temp for the first day of the month
singaporeTemperaturesThisMonth.push( 32 ); // add todays temp
```

##### pop

Take something off the end of the array.

```
var cardDeck = ['ace', 'one of clubs', 'two of clubs', ... ]
// deal a card
var topCard = cardDeck.pop();
```

##### shift and unshift
Are the opposites of push and pop.

## Loops

#### `while`

A **while loop** repeatedly executes a code block as long as a specified condition is true.

Some condition inside the code block will change, making the condition true.

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

Arrays suggest order of data, and also have a specific *integer* location for each piece of data in the list- the index.

We can use these ideas as complements to visit every location in the list.

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
