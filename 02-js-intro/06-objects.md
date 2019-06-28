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
var myKey = 'firstName';
friend[myKey]

// friend.myKey *will not* work
```
Objects represent another "secondary" kind of data- an object, with its myriad kinds of data inside can itself represent one data point (a friend for example).


### More complicated structures
Objects can be inside of other objects. This will be determined by the structure of data you want.

```
var employee = {
  name : "Chee Kean",
  wages : {
    scheduledWeeklyHours : 40,
    rate: 15
  },
  contact : {
    phone : "87665434",
    address : {
      street : "259 Cantonment",
      unit : "12-12",
      zipcode : "2345566"
    }
  }
};

// Chee Keans phone number
employee["contact"]["phone"]

// Chee Keans house unit
employee["contact"]["address"]["unit"]
```

### pairing exercise
Run the above examples.

What other kinds of data would be well represented by an object? List them.

### further
Write the lines of code to access each piece of data about the employee.

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

### further
Use the employee object above to calculate their monthly wage.

### further
```
var employeePayScales = {
  junior : {
    basePay : 15,
    bonus : 10
  },
  midLevel : {
    basePay : 25,
    bonus : 30
  },
  executive : {
    basePay : 55,
    bonus : 50
  }
};

var employee = {
  name : "Chee Kean",
  wages : {
    scheduledWeeklyHours : 40,
    level : "midLevel"
  },
  contact : {
    phone : "87665434",
    address : {
      street : "259 Cantonment",
      unit : "12-12",
      zipcode : "2345566"
    }
  }
};
```

Use these two objects to calculate Chee Kean's pay.
