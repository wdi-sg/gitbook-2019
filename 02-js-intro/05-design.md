# how to design and write programs

In the first iteration of how to write a program we'll take the building blocks of `operations` and `functions` to translate a problem statement into a function we can give input to.

## kinds of programs

#### batch processing
Are given one set of input when they are run.

Give output when they are done.

Examples:
```
Google web crawler / search indexer
Movie special effects / pixar movies
Many CLI / Unix commands
Weather predictions
AIs like siri and alexa
```

#### interactive
Most programs you think of are interactive. They do different things depending on what the user does.

## additional data types:
In order to build programs that represent the real world like the problem statements above, we must have more tools than simply naming variables and assigning them numbers or strings.

We can be explicit about using `numbers`, `booleans` and `strings` to represent the data our programs capture and process. RThe simplest way to do this is by *naming*.

Once we are explicit about these things we can design our programs to deal with these underlying basic types while representing our data clearly. Simply by naming the data represented in our programs (variables, functions and parameters ) we are describing the kind of data these represent.


### state data reperesentation

Temperature could be a number type, but *represents* a temperature.

What kind of operations are suggested by this *TYPE* of data?

```
var temperature = 34;
```

- conversion from one standard to another
- operations to see if the temperature is boiling or freezing
- if this is the temperature of a human, to se if the human is healthy
- if this is the temperature of a material, determine it's properties at the current temperature (ice, liquid, metal, nuclear reactor)

Use a conditional to determine which state produces which data.

```
if( feeling === "ok" ){
  return "me too!";
}else if( feeling === "terrible" ){
  return "ouch, sorry bout that!";
}
```

### range data representation

Altitude could be a number type, but represents a height relative to the earth's surface.

What kind of operations are suggested by this kind of data?

- human breathable range
- locations inside the earth / earth's core / geoological locations
- sea conditions / submarine conditions
- flight conditions
- space flight conditions

Use a conditional to determine what data is produced from which range.

Example:
A program that recommends outdoor sports clothing.
```
if( temperature < 0 ){
  return "below freezing! we suggest 2 layers";
}else if(temperature >= 0 && temperature < 10 ){
  return "pretty cold. try our Warm Tech Fleece";
}else{
  return "try our warmer clothing sections";
}
```

## data outside these 2 types:
`null` is the representation of non-value in js. we can use this native type as a value that represents the non-value of data for either state data or range data.

Example:

A game of tic tac toe. How do you represent what's happened to a single square on the board?
```
var square1 = null;
// the game starts with each square being unmarked - neither X or O.
```

Note that this `null` type *is not* the same as the IDEA of a non-data data.

## other data

#### global constants
Sometimes we want to define data in a variable that will never change.

Use all caps for those variable names.

```
var PI = 3.1415;
```

#### global world state
Especially in a game there can be dynamic values that represent exactly what is being shown to the user.

If it's dynamic, we can assign the default value to it at the top of the program.

```
var clicks = 0;
```

### wage program

You are tasked with creating a program for a restaurant that will tell the owners how much an employee's wages are each month. The employees are paid by the hour.

We'll add another requirement to make this program more complicated:

If the employee has worked over 40 hours, they get overtime. Overtime pay is 50% more than their base wage.

## function writing process

Today, we'll add a new step, the `function template`.

When we have more complicated functions that contain other control structures or data, we need a way to keep track of what we want to compute.


 `1.` Function Purpose
An english description of what the entire function is for:

To calculate the monthly wage of a worker given a rate and the hours worked.

 `2.` Input Data Description

In english, describe what data your function deals with.

Name the parameters after what data they represent.

```
hourlyRate - the rate earned per hour
hoursWorked - number of hours worked
```

 `3.` Data Examples

Write actual examples for the input data.

You should think about a range of examples. What are the possible input values? Give examples.

```
var hoursWorked = 5;
```

 `4.` Function Signature

Describe the *javascript* language data types your function deals with.
```
hourlyRate (number), hoursWorked (number) --> monthlyWage (number)
```

## new step

`5.` Function Template / Pseudo code
Write the conditionals you might need into the body of the function.

Use a short hand to stand in for what you want:

```
if hoursWorked more than 40

  // take off the amount that represents the amount over 40 hours:

  // define new data here
  full week = 40

  overtime = hours worked - full week

  // do the normal calculation here

  pay = wage * full week

  overtime pay = overtime * wage * 1.5;

  pay = pay + overtime pay
```

<hr/>

`6.` Code
Make it work.

`7.` Functional Examples
```
var monthlyWage = calculateWage( 15, 40 ); // will equal 600
```

`8.` Test
Run the examples yourself.

`9.` Review & Refactor
If your code is sloppy or could be changed to be more abstract, make those changes. Have you repeated yourself? Is there a way to make your code more clear? Easier to read?

```

/*
 * hoursWorked - number of hours worked
 *
 * input = 23
 *
 * hoursWorked (number) --> monthlyWage (number)
 *
 * calculate a wage given the number of hours worked.
 * if it's over time, rate is time and a half.
 *
 * var monthlyWage = calculateWage( 40 ); // will equal 600
 * var monthlyWage = calculateWage( 41 ); // will equal 622.5
 *
 */

var calculateWage = function(hoursWorked){

    var wagePerHour = 15;

    if( hoursWorked > 40 ){

      // set a number of overtime hours
      var overtimeHours = hoursWorked - 40;

      var overtimePay = overtimeHours * ( wagePerHour * 1.5 );

      // make the mutiplication calculation
      var monthlyWage = wagePerHour * 40;

      monthlyWage = monthlyWage + overtimePay;

    }else{

      var monthlyWage = wagePerHour * hoursWorked;

    }

    var output = "Bob got paid "+monthlyWage;

    return output;
};
```

### pairing exercise
Implement the wage calculation example with overtime like in the example above.

### further
Create a program that adds numbers together.

Use a global world value to keep track of the running total of numbers added.

When the user enters in a number in the input, add that number to the total.

### further
Add the ability to do other operations to the current number.

When the user types in "multiply", "subtract" or "divide" and hits enter, the *next* number entered uses that operation on the number entered and the running total.

Use a global world value to keep track of which operation the user selected.

### further
Add features to the calculator.

Add the ability to calculate the volume of a rectangular shape. Add the command to tell the calculator to do this.

### further
Add the ability to calculate the volume of a pyramid.
