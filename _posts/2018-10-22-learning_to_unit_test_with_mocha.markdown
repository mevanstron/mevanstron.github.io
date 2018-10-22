---
layout: post
title:      "Learning to Unit Test with Mocha"
date:       2018-10-22 22:14:51 +0000
permalink:  learning_to_unit_test_with_mocha
---



When designing my own tests, I’ve preferred UI testing using the Web Browser and Developer Tools to expose weak points in my codebase.  Most of my web development efforts have benefitted from an already constructed test suite to guide my hand in a test-driven atmosphere.  When learning Ruby, I used RSpec and Capybara. JavaScript exposed me to Mocha.  Yet, I see the benefits of working inside a structured test environment.  This blog post will walk through the initial steps needed to begin working with the Mocha test framework.
We start by installing Mocha onto your local environment.
```
$ npm install --global mocha
```
Note that Node.js version 6.0 or higher is required for Mocha to run.
Change Directories into your project and enter
```
$ npm install mocha
```
This will add the modules mocha needs to run in your project.
At this point, add a test folder in your root directory.  Then add test/test.js. 
We’re going to keep a small scope on what we’re learning to do with mocha.  Add the following to test.js 
```
const assert = require('assert');
```
This will allow our use of mocha’s assert module.  Below is a basic structure from mocha’s documentation for a simple assert statement.  I’ve provided some updates enabled by ES6:
```
describe('Array', => {
  describe('#indexOf()', => {
    it('should return -1 when the value is not present', => {
      assert.equal([1,2,3].indexOf(4), -1);
    });
  });
});
```
Each ‘describe’ nests deeper into a testing tree.  In the example above, we create a large section testing ‘Array’, with a subsection testing ‘#indexOf’.
Use of ‘it’ creates an actual test inside the test tree.  In this case, the test ‘asserts’ that an array with values 1, 2, and 3 has a value of -1 when checking an index outside of its range. In other words, it tests that the first argument is equal to the second.
In my own project, I created a class called SuperFizzBuzz and decided to test that its behaviors matched my expectations.  Upon initialization, if no arguments are provided, it should begin with default pairs in its wordNums array.  Below is a sample of my code:
```
describe('SuperFizzBuzz Class', () => {
  let fizzBuzz = new SuperFizzBuzz;

  it('When no default wordNums is provided, SuperFizzBuzz is initialized with wordNums of [{word: "Fizz", num: 3}, {word: "Buzz", num:5}]', () => {
    assert.equal(fizzBuzz.wordNums[0].word, "Fizz");
    assert.equal(fizzBuzz.wordNums[0].num, 3);
    assert.equal(fizzBuzz.wordNums[1].word, "Buzz");
    assert.equal(fizzBuzz.wordNums[1].num, 5);
  });
});
```
These tests are simple, and often confirm what you can easily determine with UI testing in your browser.  However, creating tests empowers team-based projects to measure against consistent standards.  They also help demonstrate dedication to design process and software accountability.
Though I had been familiar with these test suites as a user, I hadn’t taken the plunge to learn how to use them effectively to write unit or integration tests.  Having a unified and quantifiable way to define expectations in design and functionality through a test suite adds tremendous stability and efficiency to the efforts of the development team.

