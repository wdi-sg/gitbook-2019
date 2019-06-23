# data operations
The most basic computation is an operation. These happend between 2 pieces of data, and you get another piece of data out.

Javascript defines certain specific *types* of data and the kinds of operations you can do on it.

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

##### operations on booleans
A boolean is `true` or `false`

```
&& || !
```

```
true == true
```

###### comparison operators on numbers
We can use comparison operators to get a boolean value:

```
< > =< =>
```

```
1 < 2 // evaluates to a boolean value: true
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

## Type Coercion

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

#### Non-Values
`null` is a value that indicates the lack of a meaningful value. There are no operations you can do *to* a `null` value.

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
