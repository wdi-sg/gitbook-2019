# Intro to Conditionals

![control flow wd40](https://i.imgur.com/v4W1xwD.png)

### Lesson Objectives
_After this lesson, students will be able to:_

- explain why we would use 'control flow' in our programs
- use conditionals to create a boolean value
- Write a simple if statement
- Write an if / else statement

<br>
<hr>

A conditional is the first simplest way we can write programs that implement logic.

A set of conditionals takes data and acts on that data depending on logical conditions that you write.

### Control Flow

Control Flow is the order in which individual statements or instructions are executed. It lets you specify **when** and **which** lines of code get executed

Control flow consists of these 3 language structures:

- **Conditionals** - execute specific lines of code
- **Functions** - encapsulate one set of stuff to do, using inputs and outputs
- **Loops** - repeat lines of code

When writing a program, each of these three are the techniques we use to express how data is processed through our programs.

## Conditionals

We can set up a branching tree-like structure and control the flow of our code. Though, our code will look less like a tree and more like:
```
if (BOOLEAN EXPRESSION){
  // run this code
};
```
If the boolean expression within our condition is `true`, a branch will execute. If it is `false`, it will not execute. This is an example of `control flow`.

## IF Statements

Basic if statement

```
if (BOOLEAN EXPRESSION) {
  // run this code
}
```

The curly braces denote a `block`. The `block` will run if the `BOOLEAN EXPRESSION` evaluates to `true`.

**Example**

```
// number represents a value that's an input to our program
var number = 10;
```

```
// compare the value **in the variable** with the literal value
if (number === 10){
  console.log("The number is 10!")
}
```

#### Strings as conditionals

1) Make a variable called `name` and save a name to it.

3) Log the variable to confirm what you've stored.<br>
`console.log(name);`

4)Add a basic **if statement** to add control flow depending on the input.

```
if (name === "Kermit") {
  console.log("Hi ho! Kermit the frog here.");
}
```

- If the input name is `Kermit`, the code is run. Otherwise, the code never runs.

- Control flow with conditionals means that not every line is run. The code in front of us is separate from the process going on behind the scenes.

- Lines of code will be excluded during execution in order to take us on a particular 'branch'

- Which lines are excluded depends on Boolean values, and whether expressions evaluate to `true` or `false`

<br>
<hr>

## Numbers as conditionals

```
var age = 21;

if (age >= 21) {
    console.log ('You are allowed to buy beer');
}
```

### Comparison Operators

[Comparisons](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators) in JavaScript can be made using `<`, `>`, `<=` and `>=`. These work for both strings and numbers. This is both useful, and can be the source of frustration for some developers, since most languages do not implicitly convert strings to numbers the way that JavaScript does.

```javascript
"A" > "a"
//=> false

"b" > "a"
//=> true

12 > "12"
//=> false

12 >= "12"
//=> true
```

```
5 > 2;
=> true
```

```
5 <= 5;
=> true
```

- strings are compared by alphabetical precedence

```
`'a' > 'b'`;
=> false
```

```
`'z' > 'abc'`
=> true
```



## Conditions with several cases:

```
If the bag weighs over 8 kg, charge $20 per kilo. If the bag is over 50kg, it is unacceptable. Otherwise the bag is free.
```

### Logical operators

`&&`, `||`

- `&&` **and**: evaluates to `true` if both sides are true. It does not check for equality! Rather, **and** evaluates the truth of the statement, and will return the value of one of the operands.

```
true && true
=> true
```

```
false && false
=> false
```

In these examples, each side is the same (they are equivalent), but in this case, both sides do not both evaluate to `true`.
If an `&&` statement begins with `false`, it automatically evaluates to false.
Both sides must evaluate to true to && to result in true.

```
true && false
=> false
```

```
var a = true;
var b = false;

a && b
=> false
```

<br>

- `||` **or**: evaluates to true if _either_ side is true.

```
true || false
=> true
```

```
false || false
=> false
```

```
var x = false
var y = false

x || y
=> false
```

### If / else

```
if (5 % 2 ==0) {
    console.log('Number is even');
} else {
    console.log('Number is odd');
}
```
### else if

```
if (number >= 15) {
    console.log('Number is larger than 15');
} else if( number < 15 && number > 3 ){
    console.log('Number is between 15 and 3');
}else{
    console.log('Number is 3 or less');
}
```


### Pairing Exercise:

#### Conditional `if` `else` `if else` Statements

Create a new html file: `touch conditionals.html`

Create a new js file: `touch conditionals.js`

Link them together in your HTML file: `<script src="conditionals.js"></script>`

Paste the above conditional statement examples into your js file one at a time.

Use `console.log` to see what values you are getting.

#### further

Starting at the bottom of your js file, create a variable `speed`. write the contitional for a traffic stop. If speed is less than 10 `console.log` "I pulled you over because you were going too slow". If speed is more than 50 `console.log` "I pulled you over for going to fast".

Create a variable `tirePressure`. If tire pressure is less than 10 PSI `console.log` "I pulled you over because you are driving with a flat tire".


#### further

  - create a variable `monkey` that creates a random number from 1 to 10 (just copy and paste this code): `var monkey = Math.floor(Math.random() * Math.floor(10));`
  - for each conditional you write, also console.log the word `chocolate` after the conditional statement (closing curly brace).

Example:

```
if( 3 == 4 ){

}
console.log("chocolate");
```

  - write a conditional that will `console.log` `hello` if `monkey` is less than 6
  - write a conditional that will `console.log` `goodbye` if `monkey` is 6 or is more than six.
  - write a conditional with an else statement- `console.log` `cats` if `monkey` is less than 3, otherwise `console.log` `goats`
  - write a conditional with an else statement- `console.log` `almonds` if `monkey` is less than 9, otherwise `console.log` `jelly`

  - create another variable `johnathan` that creates a random number from 1 to 10 (just copy and paste this code): `var johnathan = Math.floor(Math.random() * Math.floor(10));`

  - write a conditional that will `console.log` `dollars` if `monkey` is 6 or less than 6 and `johnathan` is less than 5
  - write a conditional with an else statement- `console.log` `dogs` if `monkey` is 3 and `johnathan` is less than 5, otherwise `console.log` `submarine`
  - write a conditional with an else statement- `console.log` `puppies` if `monkey` is more than 7 or `johnathan` is less than 3, otherwise `console.log` `godzilla`

  - write a conditional that will `console.log` `halifax` if `monkey` is 6 or less than 6 and `johnathan` is less than 5 and `johnathan` is not 3
  - write a conditional that will `console.log` `halifax` if `monkey` is 6 or less than 6 and `johnathan` is less than 5 and `johnathan` is not 3

  - write a conditional with an if else statement- `console.log` `electric` if `monkey` is less than 3, but, if `monkey` is equal to 5, `console.log` `camper van`
  - write a conditional with an if else statement- `console.log` `toes` if `monkey` is more than 3, but, if `monkey` is equal to 1, `console.log` `shoelace`
  - write a conditional with an if else statement- `console.log` `curry` if `monkey` is more than 9, but, if `monkey` is equal to 4, `console.log` `future`. Otherwise `console.log` `orchid`.

  - write a conditional that will `console.log` `danube` if `monkey` is less than 6 or `johnathan` is less than 3, but, if `monkey` is more than 7 and `johnathan` is equal to 9, `console.log` `trumpet`. Otherwise `console.log` `brains`

## Extra: combining boolean statements together without parentheses:

### Boolean order of evaluation

0. `()`
1. `>, <, >=, <=`
2. `==, ===`
3. `&&`
4. `||`

<br>

* Check: `!false && true`
* Check: `false || true`

```
var a = true;
var b = false;
```

* Check: `a && a == b`
* Check: `!true || !false && !false`
* Check: `8 > 1 && true || false`

<br>
<hr>

## Extra: data type mismatches

### Truthiness

**All** values in JavaScript have an implicit 'truthiness'. They can be evaluated as either true or false. In effect, every value in Javascript is converted into a Boolean when it is checked as an expression of truth.

##### All of the following become false when converted to a Boolean

- `false`
- `0`
- `""` (empty string)
- `NaN`
- `null`
- `undefined`

<br>

JavaScript has a built-way to convert things to Booleans: `Boolean()`. Put the following inside the parenthesis of `console.log()` to see the result.

```
Boolean("");
Boolean(null);
Boolean(0);
```
<br>


##### All other values are implicitly true

```
Boolean("hi");
Boolean(1);
Boolean(true);
```

### Data Type Coercion

Types mean that each of the kinds of data described above is distinct. As far as the computer is concerned `2` and `"2"` are different and unrelated values. The programmer has to tell javascript to relate two values of different data types.

Javascript will try to make sense of any strange operations you throw at it.
- Examples of "strange": subtracting a number from a string, multiplying `null` by 100
- It does this by converting data types using a process called "type coercion"

You might encounter this when dealing with numerical values but for whatever reason some of them are in string form.

```js
// In some cases Javascript is helpful and converts strings to numbers in the correct way.
"3" - "2"
// => 1

// ...but sometimes it doesn't. In this example, the + operator acts as if it's concatenating two strings.
"3" + "2"
// => 32

// And this?
"five" * 5
// => NaN
```

When in doubt, convert data types that should be numbers using `parseInt()`.

```js
parseInt("3")
// => 3
// parseInt converts a string to a number value, if available.

parseInt("burrito")
// => NaN, because "burrito" cannot be converted into a number
```

There are other examples of type coercion, but the point here isn't to remember them all. Just be aware that sometimes Javascript will fire weird results back at you with no explanation. Sometimes, type coercion might be the culprit.


### Check for odd numbers
_Modulus as conditionals_

`%`

Check for odd numbers:
```
if (5 % 2 == 0) {
    console.log('number is even);
}
```

**Let's add an `else` to our `if` statement**










## Not

- `!` **not** sometimes called a 'bang': changes Boolean value to its opposite.

```
var score = 8;

if( score !== 10 ){
  alert( "imperfect!" );
}
```




