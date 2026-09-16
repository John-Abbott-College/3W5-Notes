# Callbacks

A _callback_ is a function that is passed as an argument to another function and is executed after the completion of that function or event.

## Formal Definition

Remember the lecture I gave on functional programming in JavaScript, focusing on pure functions? This formal definition applies to all languages with a functional component. In the context of JavaScript, these pure functions are often referred to as callbacks.

TLDR: A callback is a function passed to another function.

## Example

```js
// Notice the parameters
function greet(name, callback) {
  console.log("Hello, " + name);
  callback();
}

// this is a `pure` function
function sayGoodbye() {
  console.log("Ok, bye bye");
}

// Pass `sayGoodbye` as a `callback` to `greet`
greet("Poggie", sayGoodbye);
```

# Arrow notation

You have encountered both notations for writing functions. Today, we will cover the details of what each one means.

## Syntax

Let's say I have written the below function in the traditional `function` syntax in JavaScript:

```js
function myFunction() {
  return "I am a function";
}
```

I can express a `function` using arrow notation with this general syntax:

```js
(parameters) => body;   //returns automatically

//OR

(parameters) => { multi-statement-body };
```

So I can rewrite `myFunction` using this cleaner syntax:

```js
const myFunction = () => "I am a function";
```

If the body is just one statement, then the value that the statement resolves to will be returned!

```js
(a,b) => a+b;

//is equivalent to

(a,b) => { return a+b; };
```

If the body needs to be more than one statement, you must use curly braces and return anything you want to return explicitly:

```js
(a,b) => { console.log(a);
           return a+b; }
```



If I only have 1 parameter, I can omit the parentheses:

```js
parameter => body;

a => 2 * a;
```



# Exercise 1

A) Re-code this arrow function with traditional syntax and run it:  

```js
let greetPerson = (greeting, name) => alert( greeting + ", " + name );
```

B) Can I omit the parentheses with 2 parameters? Try it!



## Why is this so popular?

Arrow functions are considered more modern and are part of ES6 (ECMAScript 2015). Many newer frameworks and libraries, like React, encourage using arrow functions because they represent current best practices and align with modern coding style guides. Why? Arrow functions offer several key benefits ...

## Concise Syntax

You write less code, and the code you do write is often cleaner:

```js
// Trad JS
const add = function (a, b) {
  return a + b;
};

// ES6 JS
const add = (a, b) => a + b;
```

## this binding

Arrow functions do not have their own `this` context; instead, they inherit this from the surrounding code (lexical scope):

```js
// Trad JS
function Student() {
  this.age = 0;
  setInterval(function () {
    this.age++; // `this` doesn't refer to the Student
  }, 1000);
}

// ES6 JS
function Student() {
  this.age = 0;
  setInterval(() => {
    this.age++; // `this` refers to the Student
  }, 1000);
}
```

## Simplifies Callbacks

Building on the previous example, let's simplify the logic using modern syntax:

```js
function greet(name, callback) {
  console.log("Hello, " + name);
  callback();
}
// Pass a cleaner `callback` to `greet`
greet("Poggie", () => console.log("Ok, bye bye"));
```

## Encourages Functional Programming

Arrow functions promote concise, single-expression functions, making them a natural fit for functional programming styles, which are increasingly popular in modern JavaScript development. When working with popular libraries like React, you will rarely see the traditional approach to JavaScript `function`s.

Eventually, we will explore common use cases later in the class when we start using advanced array methods such as `.map()`, `.reduce()`, and `.sort()`.

## Limitations

Arrow functions are often not suitable for object methods because object methods typically need to reference the object’s properties using `this`. Since arrow functions don’t have their own `this`, they may not behave as expected in many cases:

```js
// `this` breaks
const student = {
  name: "Poggie",
  greet: () => {
    console.log(`Hello, my name is ${this.name}`); // `this` will be undefined
  }
};

student.greet(); // "Hello, my name is undefined"
```

In this case, you should use traditional `function` syntax or a _regular function_ when you need to reference the object itself:

```js
const student = {
  name: "Poggie",
  // this is known as a `method` function
  greet: function() {
    console.log(`Hello, my name is ${this.name}`);
  }
};

student.greet();
```

However, arrow functions can still have a place in JavaScript objects, particularly for properties that don’t need to reference `this` or for handling callbacks:

```js
const calculator = {
  add: (a, b) => a + b,
  multiply: (a, b) => a * b,
};

console.log(calculator.add(5, 3)); // 8
console.log(calculator.multiply(4, 2)); // 8
```

Ultimately, it depends on the use case and context, but you are likely to encounter _all_ the above styles if you choose to pursue a career in web development.

# Exercise 2

Recode the following traditional code using the modern syntax where appropriate:

```js
var student = {
  name: "Your name",
  id: 12345,
  rScore: 90000,
  greet: function (name) {
    console.log("Hey there, " + name + "!");
  },
  reminder: function () {
    console.log(`Did you know that you have a Test Friday?`);
  },
  calculateRScore: function (bonus) {
    // at this fictitious school, the r score only goes up
    this.rScore += bonus;
  },
};

student.greet();
student.reminder();
student.calculateRScore(42);
console.log(student.rScore);
```

