# Arrays - Arbitrary Length Data

## Arbitrary Sized Data

So far our programs have dealt with a single set of data that we control completely.

Real-life data usually isn't like that.

Most data has an arbitrary length.

Arrays are collections of the **same** kind of data, in a list format.


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


### More Array Structures

Simply given a new *structure* we can store different kinds of data- like coordinates.

```
// You can also place arrays within arrays.
var bingo = [
  [null,true,null],
  [null,null,null],
  [true,null,null]
];

// How would we go about accessing the letter "f" in the above array?
bingo[1][2]
// => null
```


### Array Methods

* `.length`

* `.push` put something on the end of the array
* `.pop` take something off the end of the array


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

* `.unshift` put something on the beggining of the array
* `.shift` take off the first thing in the array

### Pairing Exercise
Use the unit 1 template starter code.


###### Part 0
Copy and try out the code examples above.

###### Part 1

Put this array at the top of your script.js file.
```
var mountRushmore = [ "Washington", "Jefferson", "Roosevelt", "Lincoln" ];
```

When the user enters *anything*, take one item out of the array (`pop`) and display it.

###### Part 2

Start back with the default starter code.

Put this array at the top of your script.js file.
```
var alphabet = ['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z'];
```

When the user enters in *any* number between 0-25, show them the corresponding letter of the alphabet.

### further
When the user enters anything in the input, put it into the array.

`console.log` the array to see the current set of values inside.

### further

Use `shift`

```js
var numbers = [12,23,12,45,32,43];
```
When the user enters a number into the input, put it into the beggining of the array. (`shift`)

Take the last thing out of the array (`pop`). Add this number to the number that was entered into the input. Show that number to the user.

### further

Alter the program above.

The first number the user enters, do a multiplication instead of addition.

The second time, do an addition.

The third time, switch back to multiplication and so on.
