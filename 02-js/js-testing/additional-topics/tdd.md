# Test Driven Development

## Objectives
* Define Test Driven Development (TDD)
* Understand the benefits of TDD
* Convert requirements and specifications into tests.
* Write code to cover all tests.
* See an example of how to do TDD
* Do your own TDD

**Test Driven Development** (TDD) describes one way to to develop software.
The philosophy of Test Driven Development says tests should be written
**before** any other code. Instead of writing code and then writing tests
to make sure the code words, you should write tests and then write code until
the tests work.

There are many potential benefits to Test Driven Development:

* Writing tests first guarantees that you have tests written when you're done! :D
* Writing tests first can help specify project requirements
* Writing tests first can help you think about the intricacies of the problem at
  hand.
* Writing tests first can help you reason about how your code should behave in
  special edge cases.
* Writing tests first can help clarify how code will interact with itself.
* Writing tests first may make you more likely to write harder, more robust
  tests. If you write tests second you may be more likely to only write simple,
  easy-path tests.

Let's dive in and see what Test Driven Development is all about.

# What's the Big Idea?
Often times as developers we'll have some idea of what we want to make and dive
right into writing code. With small projects it's easy to make a simple HTML
page, create a server, add some JavaScript and be on our way. As programs get
more complex it's not always a good idea to jump in blindly and start hacking
away. Test Driven Development is one way to guide our development process and
help make sure we end up where we're trying to go.


# Example: ROT13 Cipher
Let's write a small program that will let us send secret messages to each other.
We'll use what's called a substitution cipher, which is a fancy way of saying
that we'll replace each letter in our original message with a different letter.
One popular substitution cipher is called "ROT13." It stands for "rotated by
13 places." It means we take the Alphabet and rotate it by 13 places so each
letter is replaced with the letter that comes 13 places after it. It's like a
decoder ring from a serial box.

```js
original: ABCDEFGHIJKLMNOPQRSTUVWXYZ
   final: NOPQRSTUVWXYZABCDEFGHIJKLM
```

If we want to write `"hello"` it becomes `"uryyb"`. `"H"` is replaced with
`"u"`, `"e"` is replaced by `"r"` and so on. The cool thing about ROT13 is that
the process of encrypting a secret message is the same process as decrypting
a message. If you shift `"A"` 13 letters to the right you get `"N"`. If you
shift `"N"` 13 letters to the right you get back to `"A"`. If you run a
plain message through ROT13 you get a secret message. If you run the secret
message back through ROT13 again you get back the plain message.

Let's write a function called `rot13(str)` that accepts a string as a parameter
and returns a secret message.

But, wait. How will we know when this works? Let's use Test Driven Development!

## Testing ROT13
When we're doing Test Driven Development we need to look at our requirements
and convert them into test cases. Once we've decided what we need to test we
need to write the actual tests. Only after the tests are written is when we
begin writing our actual program. As the program is being written we can check
it against the tests and make sure we're programming it correctly.

1. First, we'll describe test cases in English.
2. Second, we'll code the test cases into a test suite.
3. Third, we'll implement our actual code and run it against the tests.

## Describing Tests
How should our program behave? Let's gather some simple test requirements:

* It should convert `"a"` into `"n"`.
* It should convert `"n"` into `"a"`.
* It should convert `"z"` into `"m"`.
* It should convert `"m"` into `"z"`.
* It should convert `"hello"` into `"uryyb"`.

## Creating Tests

```js
var assert = require("assert");

describe("ROT13 tests", function() {
  describe("simple substitutions", function() {
    it("should convert A into N", function() {
      assert.equal("n", rot13("a"));
    });
    it("should convert N into A", function() {
      assert.equal("a", rot13("n"));
    });
    it("should convert Z into M", function() {
      assert.equal("m", rot13("z"));
    });
    it("should convert M into Z", function() {
      assert.equal("z", rot13("m"));
    });

    it("should convert 'hello' into 'uryyb'", function() {
      assert.equal("uryyb", rot13("hello"));
    });
    it("should convert 'uryyb' into 'hello'", function() {
      assert.equal("hello", rot13("uryyb"));
    });
  });
  
  describe("preserving capitalization", function() {
    it("should convert A into N", function() {
      assert.equal("N", rot13("A"));
    });
    it("should convert N into A", function() {
      assert.equal("A", rot13("N"));
    });
    it("should convert Z into M", function() {
      assert.equal("M", rot13("Z"));
    });
    it("should convert M into Z", function() {
      assert.equal("Z", rot13("M"));
    });
    
    it("should convert 'urYYB' into 'heLLO'", function() {
      assert.equal("urYYB", rot13("heLLO"));
    });
    it("should convert 'heLLO' into 'urYYB'", function() {
      assert.equal("heLLO", rot13("urYYB"));
    });
  });
  
  describe("preserve whitespace and punctuation", function() {
    it("should ignore whitespace", function() {
      it("should convert 'hello' into 'uryyb'", function() {
        assert.equal(rot13("Today I went to the store"), "Gbqnl V jrag gb gur fgber");
      });
    });
    
    it("should ignore punctuation", function() {
        assert.equal(rot13("I'm telling you, \"go away!\" Can you hear me?"), "V'z gryyvat lbh, \"tb njnl!\" Pna lbh urne zr?");
    });
  });
});

```


# Exercise: Write Your Own YearDate Class
Let's write our own `YearDate` class that encapsulates dates into a convenient
object. We'll be able to keep track of days, months, and years in each object.
We'll be able to use two of the objects together to calculate the number of
days between two `YearDate` objects. Our class should handle Leap Years
correctly.

* The `YearDate` constructor should accept a `day`, `month`, and `year`
* There should be a method called `.daysInMonth()` that returns the total
  number of days in the current month.
* There should be a method called `.nextDay()' that increments a `YearDate`
  object from one day to the next.
* Each `YearDate` object should have a method `prettyPrint()` that returns
  a string like `"January 1st, 1988"` or `"June 11th, 1992"` with correct
  "1st", "2nd", "3rd" and "th" suffixes.
* Each `YearDate` object should have a method called `.daysBetween(other)` that
  accepts another `YearDate` object as a parameter and returns the absolute value
  of numbers of days between one date and another. This method should never
  return a negative number.

## Write Down Test Descriptions With Your Neighbor
Before you write any code for the `YearDate` class you should write tests first.
Work with a partner to write down, in English, different test cases you can think
of. You should have at least ten different test cases written down.

<details>
  <summary>Here's a list of example test cases.</summary>
  <ul>
    <li>
      Test the constructor. Create a simple YearDate object and make sure
      the day, month and year are set correctly.
    </li>
    <li>
      Create a January date and make sure there's 31 days.
    </li>
    <li>
      Create a February date and make sure there's 28 days when it's not a
      leap year. Make another Febrary date during a Leap Year and make sure
      there's 29 days.
    </li>
    <li>
      Create several test cases to make sure the date suffixes are generated
      correctly. You should have a test for at least dates on the first,
      second, third, eleventh, twelfth, thirteenth and more to make sure
      it's implemented correctly.
    </li>
    <li>
      Create a test to make sure the .nextDay() method works correctly in a
      simple case in the middle of the month.
    </li>
    <li>
      Create a test to make sure the .nextDay() method works correctly when
      rolling from one month to another month.
    </li>
    <li>
      Create a test to make sure the .nextDay() method works correctly when
      rolling from one year to another year.
    </li>
    <li>
      Create a test to make sure the .nextDay() method works correctly when
      it rolls between February and March during a leap year, and when it's
      not a leap year.
    </li>
    <li>
      Create a simple test case to make sure the distance between two identical
      dates returns zero.
    </li>
    <li>
      Create a simple test case to make sure the distance between two days in
      the same month is correct.
    </li>
    <li>
      Create a test case to make sure the distance between two dates in the same
      year is correct.
    </li>
    <li>
      Create a test case to test the distance between two dates, depending on which
      order you've called the method from. Is the distance between "January 1st, 2000"
      and "December 25th 1999" the same as the distance between "December 25th, 1999"
      and "January 1st, 2000"?
    </li>
  </ul>
</details>

## Implement Your Tests
Convert each of your English test descriptions into an actual coded test. Run
the test suite and make sure all of the tests are currently failing. They'll
begin lighting up green and passing as you write your actual `YearDate` class.

## Implement the YearDate Class
Now that you've read and understood the project requirements, described your test cases,
and created code to implement each test case you're finally ready to begin writing
`YearDate` class code!

## Deliverable

Here is what your test suite should look like for a completed lab...

![](https://i.imgur.com/s5rv4PR.png)

## Bonus

Refactor your tests using a different [Chai assertion style](http://chaijs.com/).