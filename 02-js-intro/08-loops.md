## Loops

#### `while`

A **while loop** repeatedly executes a code block as long as a specified condition is true.

Some condition inside the code block will change, making the condition true.

```js
var i = 0;
while (i < 5) {
  console.log("i is " + i);
  i++;
}

// Will print out:
// >i is 0
// >i is 1
// >i is 2
// >i is 3
// >i is 4
```

---

**The parts of a while loop**

```
while (CONDITION) {
  //CODE
}
```

```
var i=0;

while (i < 5) {

  console.log("i is " + i);

  i++;
}
```

---

Loop that runs forever
```
while(true){
  //CODE
}
```

### Backwards Loops

It's totally possible to run the loop backwards. We need to do three things:

1. Instead of starting i at zero. We have to subtract one each iteration of the loop.
2. Change the test condition to run the for loop while `i > 0`
3. Change the step instruction to `i--`

```
var i=9;

while (i > 0) {

  i--;

  console.log("i is " i);
}
```

### Exercise: Run some loops (10 mins)

- Setup Your Files (html / script)
- Copy the above code examples
- Change the value of i to something bigger
- Change the condition from *less than* to *less than or equal to* - what happens?
- Change the starting value of i to something else. What happens?
- Make a while loop that runs 1000 times and console.logs out `i`.
- Make a while loop that runs 1000 times and console.logs out `hello`
- Make a backwards loop
- Make a loop that increments more than one (counting forwards and backwards) 
- Make a loop that runs a random amount of times (up to a reasonable number) - just google how to create a random integer in javascript if you don't know how.
- Crash your chrome browser tab by running a while loop that console.logs something and goes on forever.
