#Low Level Pseudocode

---

###Objectives
- learn what low level pseudocode is
- learn how to use it to turn high level pseudo code into a non-syntax specific set of code

###Context
Our process for writing code begins with a user problem statement. After we understand each step we need to implement the solution to the problem we can begin thinking about the code level implementation of each step.

Low-level pseudocode will help us map out what each logical step will require.


---

#### Approaching a Coding Problem (15 minutes / 0:35)
Pseudocode isn't just about writing down the steps that you already know. It's a tool to help you work through the problem. Before we can write pseudocode to solve the problem, we need to know the problem.

The process of writing a program is first understanding the problem well, then expressing it in our code in an explicit and elegant way.

We write programs using these cognitive tools: decomposition, abstraction, encapsulation and modeling. Pseudocode helps us work with these techniques.

Decomposition: In what ways can we break the problem down into it's constituent parts?
  - Which parts of the sandwich making process are distinct and discreet?

Modeling: How do we represent our data?
  - do we use an array or an object? A string or a number?

Encapsulation: How do we package the concepts of the problem together in a way that makes sense?
  - Does the peanut butter belong with the jelly? Or does it belong with bread slice 1 & 2?

Abstraction: What do we use to generalize parts of our problem? How general do we make our program?
  - Can we generalize our system for all kinds of jelly? What about jam, or even mustard?

---

#### Review: Steps to get to low level pseudocode: or, how to program.
1.Identify the Problem

- What exactly are we trying to solve?
- What are we delivering?

2.Conceptualize

- Look at the big picture
- Avoid details
- Whiteboards and pen-and-paper can be useful tools here

3.Break It Down - high level pseudocode

- Break the conceptual models down into concrete steps / actionable items
- Identify risks (e.g., gaps in knowledge and technology)

4.Break It Down Again - low level pseudocode

- write out a logical step for each item you came up with

---

#### Start Small, Stay Small

Write code using those small steps
- Verify that each step achieves what we want before continuing on
- If we do too much at once and things break, which they always do, we won't know what is causing the problem
- Humans thrive on easy wins and forward progress. Use this to your advantage.

---


### Where Does Pseudocode Fit In?

---

#### "Break It Down"

This process is iterative.  We keep circling around and repeating the earlier steps, just at a different level.

When we first approach a problem, we see the big picture. "Break it down" first into big steps. Then we take one of those steps and "Break it down" again into smaller steps. We write pseudocode to help illustrate the problem.

Pseudocoding proves that we have *identified* the problem, understand it *conceptually*, and have *broken it down* into *small steps* that we can follow.



#### Example
We want to know if a number is even or odd:

High-level pseudo code:
1. write a function to do it
2. we can check if the number is divisible by 2
3. if its not then its odd

Low-level:
```
PROGRAM IsEvenOrOdd:
  IF (number divided by two has no remainder) // modulo
      THEN Print the number is even;
      ELSE Print the number is odd;
```

<details>
  <summary><strong>What do we think?</strong></summary>

  > We started with a problem statement. We turned it into a number of steps we thought we might need to complete. The last pseudo code step is to map out which specific code steps are needed to accomplish the problem.

</details>
#### Example
A driver drives through an ERP gantry. What is the amount charged?

High-level pseudo code:
1. Check if we are charging or not yes/no
2. Check what kind of vehicle it is
3. Check what the time is to determine the exact charge.

Low-level:
```
PROGRAM ERPCharge:
  IF charge on this day
      if car
        if time is before noon
          charge $1.00
        otherwise
          charge $0.50

      if truck
        if time is before noon
          charge $1.00
        otherwise
          charge $0.50
```

## You Do: Pseudocode (15 minutes / 0:50)

Lazada is having a big sale. Your task is to write the pseudo code logic for calculating the final price of an item after GST, shipping and the different discounts have been applied.

Note: You don't have to worry about where a particular piece of data is coming from. Any number or quantity mentioned can assumed to be assigned to a variable. This exercise is about logic.

Part 1:
Shipping is flat rate $10 except for people buying bulky items, or if it is being shipped to east coast. (both of these are a $10 extra fee)

When you buy over $40 of stuff, shipping is free.

Shipping is also taxed.

Any sofa is %10 off and free shipping.

Part 2:
iPhones come with a discount voucher of $20 off your entire purchase.

Part 3:
When you buy any nike product, you get a 15% discount (this special discount is inclusive of GST)

Part 4:
Current members of the Lazada frequent buyers club get an extra %5 off any clothing up to $50 in discounts.

Part 5:
When paying with Visa your order is tax free.

Part 6:
Change the pseudo code so that only the first 2 applicable discounts can be combined.


## Conclusion

1. What are some helpful steps for solving problems?
2. What does pseudocode help us do?
3. Do we only pseudocode at the start of a project?

---

## Resources

- [Introduction to Pseudocode](http://www.slideshare.net/DamianGordon1/pseudocode-10373156)

## Screencasts

- [Pseudocoding](https://www.youtube.com/playlist?list=PL-6bwUTtCRVTMUUSjqIYVXYyfZBzs8saD)
