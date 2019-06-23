# Objects
Objects use "keys" instead of indexes to store data.

Why use objects to store `key` and `value` pairs? They are like arrays except that data is not stored in any sorted order and keys do not have to numbered indexes.

Objects are useful because we can specify/name the keys to represent the data we want to hold.

```js
var person = {
  name: 'Chee Kean',
  weight: 231,
  height: 1.7
};
```

Thus we are most likely saying that a second person will contain the same types of data, (the same keys) but with different values (a different name)

#### Creating

```js
var friend = {firstName: "Jane", lastName: "Doe"}
```

#### Accessing

```js
friend.firstName
friend.lastName

friend['firstName']
friend['lastName']
```

```js
var myKey = 'firsdtName';
friend[myKey]

// friend.myKey *will not* work
```
Objects represent another "secondary" kind of data- an object, with its myriad kinds of data inside can itself represent one data point (a friend for example).

### pairing exercise
Run the above examples.

What other kinds of data would be well represented by an object? List them.

### further
Change the wage example to take an object instead:

Each employee makes a different wage per hour.

```
var employeePay = {
  wage: 15,
  hours: 40
};
```

Use this object as the input value to calculate the monthly salary.
