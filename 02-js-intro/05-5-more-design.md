## helper functions
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

  if( isNaN( parseInput ) ){
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
