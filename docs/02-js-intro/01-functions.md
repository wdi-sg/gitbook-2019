day 1
(fixed size data)
command line, operations, conditionals, css box model

pokedex html

day 2

cli murder

git
functions
interactive template
float display positioning

temperature converted


day 3

ios

github
layout
program design


day 4

wendy bite


objects
virtual pet??

day 5

hippy portfolio

(arbitrary size data)
arrays
loops (while loop only)

choose your own adventure

???

w2 d1

w2 d2

w2 d3

w2 d4








##### operations
The most basic computation is an operation:

Open the chrome console:

##### operations on numbers

```
+ - * /
```

```
2 + 2
```

##### operations on booleans

```
&& || !
```

```
true == true
```

##### operations on strings

```
+
```

```
"hello" + "world"
```


### pairing exercises
Open the chrome console.

Try the examples above. Combine the operators and see what values you get.

# conditionals



# functions

In the next 12 weeks we will learn to write web applictation software.

As we build up to an example of a complete application, we'll be starting with the fundamental building blocks of that application (and of all software)

First we'll see functions as the fundamental building block of all programs.

Functions are the atomic computation structure of a program- something that takes input, computes and makes output.

As programmers the definition of functions is the first tool we'll define to begin the process of solving complex problems.

```js

var add = function(a,b){

  return a + b;
};
```

##### function definition

A function is a program definiton of at least one operation that gives back a value (the result of some operations)

The return keyword: gives data as output of the function


### functions as operations on data

A real world example is a function that calculates area of a disk:

```

var areaOfDisk = function( radius ){

  return 3.1415 * radius;
}
```

#### naming of parameters / variables

Design and writing of programs menas we must define the data we are operating on. We define this data firstly by naming what it represents.

### composition of operations

As the goal of our programs grows in complexity, the we want ot be able to slowly grow our programs and manage their complexity.

We need a method that has several attributes:

- modular / composed of parts
- easily verifiable
- easy to understand at each level

To do that, we will be trying to make a series of functions that rely upon each other to compute and trasform our inputs from start to finish.

We'll call this function composition.

Example:

We want to know the area of a ring instead of a disk.

We can define the area of a ring as the area of one disk minus the other. We can create a function that encapsulates this:

```
var areaOfRing = function(d1, d2){
  var ring = areaOfDisk(d1) - areaOfDisk(d2);
  return ring;
}

```

### pairing exercises

Write a function that takes the parameters width, length and height of a rectangluar shape and computes the volume.

Write a function that takes in those same three numbers and computes the total surface area of the shape.

Write a function that calculates the volume of a sphere.

Write a function that calculates the surface area of a sphere.



## how to write programs

In the first iteration of how to write a program we'll take the building blocks of `operations` and `functions` to translate a problem statement into a function we can give input to.

#### kinds of programs

batch processing

interactive

## word problems

Programmers are rarely handed mathematical expressions to turn into programs.

Instead they
typically receive informal problem descriptions that often contain irrelevant and sometimes
ambiguous information.

The programmers' first task is to extract the relevant information and
then to formulate appropriate expressions.

Here is a typical example:

Company XYZ & Co. pays all its employees $12 per hour. A typical employee works between 20 and 65 hours per week. Develop a program that determines the wage of an employee from the number of hours of work.

The last sentence is the first to mention the actual task: to write a program that determines one quantity based on some other quantity.

More specifically, the program consumes one quantity, the number of hours of work, and produces another one, the wage in dollars. The first sentence implies how to compute the result, but doesn't state it explicitly. In this particular example, though, this poses no problem. If an employee works h hours, the wage is:

(define (wage h)
(* 12 h))
The program is called wage ; its parameter h stands for the hours an employee works; and its
result is (* 12 h) , the corresponding wage.



## additional data types:
In order to build programs that represent the real world like the problem statements above, we must have more tools than simply naming variables and giving them numbers or strings.

We can be explicit about using `numbers`, `booleans` and `strings` to represent the data our programs capture and process.

Once we are explicit about these things we can design our programs to deal with these underlying basic types while representing our data clearly. Simply by naming the data represented in our programs (variables, functions and parameters ) we are describing the kind of data these represent.

## state data reperesentation
User types "right" or "left".

Temperature is a number type, but *represents* a temperature.

Question: what kind of operations are suggested by this *TYPE* of data?

Use a conditional to determine which state produces which data.

```
if( feeling === "ok" ){
  return "me too!";
}else if( feeling === "terrible" ){
  return "ouch, sorry bout that!";
}
```

## range data representation
User types number between 2 and 6.

Example:
Altitude. What kind of operations are suggested by this kind of data?
Human breathable range, negative numbers, max and min conditions.

Use a conditional to determine what data is produced from which range.

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

```
var square1 = null;
// the game starts with each square being unmarked - neither X or O.
```

Note that this `null` type *is not* the same as the IDEA of a non-data data.

## finite state programs

Finite state programs represent a set number of states of a given system.

![dog fsm]()

### traffic lights
A traffic light turns from one state to the other in a specific order.

- when its green, turn it yellow.
- when its yellow, turn it red
- when its red, turn it green

### pairing exercise
Implement a choose your own adventure game with HTML pages.

Suggestions:
```

                          You are in a red room.
                          Do you want to go left or right?
                                    /         \
                                left          right
          You are in a blue room.            You are in a greenhouse.
          Do you want to go left or right?   Do you want to go left or right?
            /               \                                 /     \
Goes to greenhouse.     You were eaten by a grue.         You win!    Goes to red room.
```

### pairing exercise
Implement a choose your own adventure. Let the user enter things as input.

1. Data Description

2. Data Examples

3. Function Signature

4. Function Purpose

5. Function Header

6. Functional Examples

7. Function Template

8. Code

9. Test

10. Review & Refactor
