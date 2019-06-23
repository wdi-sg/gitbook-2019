# template
This template isolates your running code to this one function. It takes in a user input parameter and at the end calls `display`, passing the output value.

This design is how we will setup all of our programs in unit 1.

Now we'll make some changes to this file:

1. Change the function to output the `input` parameter instead of "WOW SOMETHING HAPPENED" - that is, pass somethin different into the `display` function.

2. Use `toUpperCase` to change what was typed in to all upper case in the output.

3. Write a conditional for the input. If the input is "ducks", output "quack". Otherwise the program should run as it was before.

#### input types

Now, we'll talk about input types.

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

  // output something
  display( "Bob got paid "+monthlyWage);
}
```

### complete wage example

Let's change our wage example so that we write our own function.

What we want to be able to accomplish with out program is a complete example that accounts for different inputs (what if the user types in `*&^*#`) and handles output for those cases.

#### helper functions
Some of the ways we want to compartmentalize the tasks within our function is the way we check input data.

#### wish list
As our programs get bigger we will want to be keeping track of all the ways that we want to deal with the cases of things like input types.

Keep a wish list of the functions that we'll want to write as we flush out the function template. For example `inputValid`. Our program worked without it, but was vunerable to errors. If we want to concentrate on the main program we can just write down that we will create the function later.

```
/*
 * input - a string of what the user entered
 *
 * input = "23"
 *
 * input (string) --> valid (boolean)
 *
 * see if the input is parsable into an integer number
 *
 * inputValid( input )
 *
 * var isValid = inputValid( "hello" ); // will be false
 *
 */
var inputValid = function( input ){

  var parsedInput = parseInt( input );

  if( parsedInput === NaN ){
    return false
  }else{

    return true;
  }
};

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
    var monthlyWage = wagePerHour * hoursWorked;

    var output = "Bob got paid "+monthlyWage;

    return output;
};

var inputHappened = function(input){

  if( inputValid(input) ){

    var output = calculateWage( input );

  }else{

    var output = "sorry couldnt calculate";
  }

  // output something
  display( output );

}
```

### pairing exercise
Repeat all of the above steps.

### further
Make a new set of files. Write a program that greets the user. When the user types in hello, have your program respond with a greeting. Make other greeting for other things the user could type. Have a default message if the program doesn't recognize anything the user entered.


