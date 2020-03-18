# interactive template
This template isolates your running code to this one function. It takes in a user input parameter and at the end returns something, passing the output value.

This design is how we will setup all of our programs in unit 1.

Now we'll make some changes to this file:

1. Change the function to output the `input` parameter instead of "WOW SOMETHING HAPPENED" - that is, return something different.

2. Make the output display whatever the user typed in.

3. To every output, add the words "the best!" to then end.

4. Write a conditional for the input. If the input is "ducks", output "quack". Otherwise the program should run as it was before.

#### input types

Now, we'll talk about input types and type coercion.

We might want to do non-string operations on our input.

If we implement the wage calculation from before, how would we make sure our inputs are numbers? (Note that the parameter `input` will always be a string type)

`parseInt`

Parse int must be called on our input before we make a calculation.

```
var wagePerHour = 15;

var inputHappened = function(input){

  // change it to a number
  var hoursWorked = parseInt( input );

  // make the mutiplication calculation
  var monthlyWage = wagePerHour * hoursWorked;

  return monthlyWage;
}
```

### complete wage example

Let's change our wage example so that we write our own function.

What we want to be able to accomplish with out program is a complete example that accounts for different inputs (what if the user types in `*&^*#`) and handles output for those cases.
```
/*
 * input - a string of what the user entered
 *
 * input = "23"
 *
 * input (string) --> message (string)
 *
 * calculate a wage given the number of hours worked.
 *
 * calculateWage( input )
 *
 * var monthlyWage = calculateWage( 40 ); // will equal 600
 *
 */

var calculateWage = function(input){

    var wagePerHour = 15;

    // change it to a number
    var hoursWorked = parseInt( input );

    // make the mutiplication calculation
    var result = wagePerHour * hoursWorked;

    return result;
};

var inputHappened = function(input){

  //  inside of inpout happened, call some functions
  var output = calculateWage( input );

  // output something
  return output+" hours were worked";
}
```

### pairing exercise
Use the empty template here: [https://github.com/wdi-sg/unit1-template](https://github.com/wdi-sg/unit1-template)

Repeat all of the above steps.

### further
Make a new set of files. Write a program that greets the user. When the user types in hello, have your program respond with a greeting. Make other greeting for other things the user could type. Have a default message if the program doesn't recognize anything the user entered.

### further
Make another copy of the template code. Create a copy of the `index.html` - but name it `index2.html`. Same for the javascript file- `script2.js`. Change the name of the reference in `index2.html`: `<script src="script2.js"></script>`

The user will enter in an amount of SGD. Calulate it's value in USD and show it to the user.

### further
If the user enters in SGD below one dollar (cents) tell the user that the minimum is one dollar.

If the user enters in SGD over 10000, tell them the max amount is 10000 dollars.

### further
If the user enters in an amount over 100000 calculate the amount but take off a 25000 commission.

