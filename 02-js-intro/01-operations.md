# data operations
The most basic computation is an operation. These happen between 2 pieces of data and then you get another piece of data out.

Javascript defines certain specific *types* of data and the kinds of operations you can do on it.

#### Types of data:
- numbers
- booleans
- strings

##### operations on numbers
Numbers are: 1,2,3,45.6, -6.7 etc.

```
+ - * /
```

```
2 + 2
```

Like normal math, Javascript follows the traditional order of operations: P.E.M.D.A.S. or "Please Excuse My Dear Aunt Sally." Mathematical operations are executed in the following order...
  1. Parenthetical expressions
  2. Exponentiation
  3. Multiplication
  4. Division
  5. Addition
  6. Subtraction

```js
(4 + 2) * (12 / 3)
// => 6 * 4
// => 24

(8 / 4 * 2) + 1
// => (2 * 2) + 1
// => 5
```

##### operations on booleans
A boolean is `true` or `false`

```
var userCreated = true;
```

A boolean operation produces a **new** boolean value.

```
true === true // results in a new boolean value: true
```

##### operations on strings

```
+
```

```
"hello" + "world"
```
You can't, however, use other math operators on strings...

```js
"hamburger" - "ham"
// => NaN

"hamburger" * 3
// => NaN
```

### NaN ("Not a number")

A special number...that's not a number?

```js
typeof NaN
// => Number
```

You usually get `NaN` when the result of a math operation is not real (e.g., dividing 0 by 0, multiplying strings together).

```js
0/0
// => NaN
```

#### Non-Values
`null` is a value that indicates the lack of a meaningful value. There are no operations you can do *to* a `null` value.


#### Variables

We can assign values to variables using the assignment operator `=`.

```javascript
var phrase = 'In my room is a chair and a table';
```

we can use that variable as a stand-in for the original value:

```javascript
console.log(phrase);
```

**phrase** can be anything we want (with some syntactical caveats), **sentence** for example, whatever makes semantic sense.

```javascript
var phrase = 'In my room is a chair and a table';
var sum = 99 + 1;
```

```javascript
console.log(phrase);
console.log(phrase);
console.log(phrase);
console.log(phrase);
```

```javascript
console.log(sum);
console.log(sum);
console.log(sum);
console.log(sum);
```

>x4 => "In my room is a chair and a table"

>x4 => 100

##### Variable names

- cannot begin with a number or include special character
- camelCase
	- `thisVariable` NOT `this_variable`
- case sensitive
	- `thisVariable` is not the same as `ThisVariable`

##### Semicolons

- The interpreter needs the semicolons.  **DO NOT FORGET THEM!**

##### Variable re-assignment

```javascript
var item = 'chair';

item = 'eclair';

console.log(item);
```

> => "eclair"

#### Variables as Data

The *purpose* of a variable is:

###### to represent it's **literal** value in a name that defines what it means.
###### contain dynamic data that changes but always represents the same thing. ex. `var temperatureToday = 34;`

Naming a variable for what it represents is a very hard problem.

###### One of your main tasks as a programmer is to come up with the most accurate, succinct name possible.

#### Operations on variables

```
var number = 3;
var square = number * number;
var cube = square *  number;
```

```
var distance = 100;
var startTime = 0;
var endTime = 100;
var totalTime = endTime = startTime;
var speed = distance / totalTime;
```

```
var pi = 3.14;
var radius = 3;
var area = pi * radius * radius;
```

## Read error messages

Error messages are good. They are not adversarial! They are there to help you.

Error messages are **clues** that you learn to read. You should be able to read these clues on your own.

Create a new html file: `touch error.html`

Create a new js file: `touch error.js`

Link them together in your HTML file: `<script src="error.js"></script>`

Put this example in:
```
console.log('hello world);
```

The error that is created is typical. It looks intimidating and weird, but if you pry, you will find valuable clues. For example:

Error messages will tell you a **specific line number** where in the code the error occurred. This tells me the error is on line 1: `script.js:1`

Errors will often tell you what **type** of error. `SyntaxError: Unexpected token ILLEGAL`

You have to learn to sort the 'wheat from the chaff' so to speak. This will come with practice.

Errors are a **growth opportunity**. When you receive an error, yes it is an obstacle, but with a little patience it will turn you into a more informed, better developer.

### pairing exercises
Open the chrome console.

Try the examples above. Combine the operators and see what values you get.

#### further

##### % (Modulus)

The modulus operator - `%` - returns the remainder of a division operation.

```js
12 % 5
// => 2, which is the remainder of 12 / 5
```

Modulus has a pretty handy use case: to check if a number is even. We can do this by running `NUMBER % 2`. If a number is even, the result should be 0 (i.e., there should be no remainder).

```js
4 % 2
// => 0, because 4 is even

5 % 2
// => , because 5 is odd. When 5 is divided by 2, the remainder is 1.
```
