# Testing Node with Mocha/Chai

### Objectives
*After this lesson, students will be able to:*

- Describe the importance of testing your code programmatically
- Use describe and assertion functions to do basic testing
- Write integration tests that test our express server, it's routes, and implicitly the data coming from our database.

## Intro to Testing

## Framing

We've now created a number of applications.  All these apps cover a single topic, so most of the time, they are quite small.  But when you create a larger application, the codebase will become bigger and more complex every time you add some features. At some point, adding code in file A will break features in file B, and to avoid these "side-effects" or at least recognize immediately when they happen, we need to write tests our app and run them on each change. In a production-level application, providing a high level of [test coverage](http://www.softwaretestingclass.com/test-coverage-in-software-testing/) for an application is usually required in order to guarantee that code is bug-free and functions as intended.

## You Do (5 min)

[Types of Software Testing](http://www.softwaretestinghelp.com/types-of-software-testing/)

## Types of Testing

* How tests are executed:
  - __Manual__ - user runs test via the UI
  - __Automated__ - test scripts are executed. They call into the code and compare the results to the  expected values
* Granularity:
  - __Unit__: Focuses on testing individual "units" of code, usually individual functions or methods.
  - __Component__: class, library
  - __Integration__: set of components that are collaborating (interacting) to perform a task
  - __End-to-end (E2E)__: complete application running in an environment that mimics a real-world production environment
* Purpose
  - __Functional__
     * __Positive testing__ - does it work when it is supposed to work?
     * __Negative testing__ - does it fail when it is supposed to fail?
  - __Regression__: Did we break anything?
  - __Smoke__: Did the build work?
  - __Performance / Load__: How does the software behave under a heavy load?
     * Lots of users / traffic
     * Large data sets
  - __Usability__: How intuitive (easy to use) is the software?  Basically navigational testing.
  - __Security__: How secure is the application? Can the application be hacked?  Is it safe from external hacks?
  - __Compatibility__: How well does the software work with various hardware, O.S., network environments?
  - __Recovery__: How well does the system respond to hardware or software failures? Is it fault-tolerant?
  - __User Acceptance Testing (UAT)__ - Does the software do what the customers want it to do?
     * Actual software users test the software to make sure it can handle required tasks in real-world scenarios, according to specifications.

## You do (5 min)

- [Unit Testing TDD & BDD](http://codeutopia.net/blog/2015/03/01/unit-testing-tdd-and-bdd/)
- [TDD vs. BDD](http://joshldavis.com/2013/05/27/difference-between-tdd-and-bdd/)
- [TDD & BDD](http://www.joecolantonio.com/2014/07/29/unit-tdd-and-bdd-testing-whats-the-difference/)

## TDD and BDD

### TDD: Test-driven development

A development methodology of writing the tests first, then writing the code to make those tests pass. Thus the process is:

1. Define a test set for the unit
2. Implement the unit
3. Verify that the implementation of the unit makes the tests succeed.
4. Refactor
5. Repeat

### BDD: Behavior-driven development

A development methodology that was derived from `TDD` and [`DDD`](https://en.wikipedia.org/wiki/Domain-driven_design) (Domain-driven design) where tests are written in an English-like language (i.e. the `Gherkin` language) that specifies the external *behavior* (the specifications) of the unit without reference to how the unit was implemented (thus it is a form of *black box* testing). The purpose of BDD is to both describe and test the behavior of a unit of code in a single *specification* file.

## Mocha, Chai And Integration Testing - Intro (10 min)

To test our code in Node, we will use two primary libraries: one to run the tests and a second one to run the assertions.

Mocha will be our testing framework, but we're mostly just using it as a test runner. From the [Mocha Website](https://mochajs.org/)...

> "Mocha is a feature-rich JavaScript test framework running on Node.js and the browser, making asynchronous testing simple and fun. Mocha tests run serially, allowing for flexible and accurate reporting, while mapping (associating) uncaught exceptions to the correct test cases."


For assertions, we will use Chai. From the [Chai website](http://chaijs.com/)...

> "Chai is a BDD / TDD assertion library for node and the browser that can be delightfully paired with any javascript testing framework."


To be able to make HTTP requests inside tests, we will use [Supertest](https://github.com/visionmedia/supertest)...

> "The motivation with this module is to provide a high-level abstraction for testing HTTP"

Supertest allows easy assertions on top of those commands.

#### Setting up

Create the files:

```
mkdir test-ex
cd test-ex
npm init
```

```bash
mkdir src test
```

This command will create a `src/` and a `test/` folder

In order to connect our two files, we'll have to use the `require` function that is built into Node. You can read more about requiring modules at the link below or just follow our instructions here:

* [Free Code Camp: Requiring modules in Node.js](https://medium.freecodecamp.org/requiring-modules-in-node-js-everything-you-need-to-know-e7fbd119be8)


Then, let's install mocha using --save-dev:

```bash
npm install mocha --save-dev
```

Then we will install chai using --save-dev:

```bash
npm install chai --save-dev
```

Since we have mocha installed globally, in order to run our tests, we can just run `mocha` from the command line.  If we wanted to set up an npm script to run our tests, in our package.json we would add this line to the scripts object:

`"test": "mocha test/**/*.js"`

Try typing `npm test` into the terminal to run the tests.



#### Files and Folders

Now that we're configured, let's set up our file and folder structure.

```bash
touch src/calculator.js
```

#### Calculator file
We'll use `require` and `module.exports` to create a calculator in the file.

In your `src/calculator.js` file, add the following:

```js
const calculator = {
	saySomething: function(){
		console.log("hello");
	}
}

module.exports = {
  calculator: calculator
}
```


#### Let's write some tests

 All of the tests will be written inside a folder `test` at the root of the app.  This folder needs to be named test so that mocha can find it.

Then we will write the tests inside a file called `calculator.test.js`:


```
touch test/calculator.test.js
```

Open the file `calculator.test.js`. We need to require some dependencies at the top of this file:

```javascript
const chai = require('chai')

var should    = require("chai").should(),
  expect      = require("chai").expect;

const main = require('../src/calculator')

// call a function of calculator
main.calculator.saySomething();
```

Run this test file:
```
npm test
```

All of the tests need to be inside a `describe` block.  Describe blocks are high level groupings or **suites** for your tests.  They can be nested.  We will use one describe block per method:

```javascript
describe("calculator", function() {
  //tests will be written inside this function
});
```

First, we will write a test to make sure that it can add.

```javascript
describe("add", function() {
    it('should be a function', function () {
      expect(main.calculator.add).to.be.a('function')
    })

    it('should add two numbers together', function () {
      expect(main.calculator.add(2,2)).to.equal(4)
    })
});
```

Try running it now:
```
npm test
```

Get these tests to pass, edit the calculator file:
```
add : function(a,b){
	return a + b
}
```

Every block of code that starts with `it()` represents a single **test**.  Each test is performed in sequence, one after the other, in a queue.

##### Write Code

You should see 2 failing tests in your console. Great! Let's get that first one to pass.


#### Pairing Exercise
Run the above code.

In the `test/calculator.test.js` file, you should add another test:

```js
  describe('#multiply', function () {
    it('should be a function', function () {
      expect(main.calculator.multiply).to.be.a('function')
    })

    it('should multiply two numbers together', function () {
      expect(main.calculator.multiply(5,2)).to.equal(10)
    })
  })
```

```shell
npm test
```

##### Instructions

Get the two failing `#multiply` tests to pass.

##### Further

Add a new `describe` block for a `#divide` method. Add your own tests and get those to pass.


## Conclusion (10 mins)
> Review the answers to the tests specs above.

We've covered the principles of testing in JavaScript, but Chai offers a lot of different expectations syntaxes. Check the [Chai Documentation](http://chaijs.com/api/)

- How does Mocha work with Chai to write tests in your JavaScript application?
- Describe how to configure your app to use Mocha and Chai.


## Extra Resources

[BDD Cheatsheet](http://ricostacruz.com/cheatsheets/chai)

[https://www.codementor.io/olatundegaruba/integration-testing-supertest-mocha-chai-6zbh6sefz](https://www.codementor.io/olatundegaruba/integration-testing-supertest-mocha-chai-6zbh6sefz)
