
# Variable Declaration

`let`, `const`, and `var` are all used to declare variables. Whats the difference? They have different behaviors and scopes. Here’s a breakdown of the key differences:

## Var

`var` is function-scoped, meaning it is accessible within the function it is declared in. If declared outside a function, it is globally scoped.

```js
// a globally scoped variable
var x = 42;
function example() {
  // a locally scoped variable
  var y = 24;
  console.log(x + " " + y); // 42 24
}
example();
console.log(x + " " + y); // ReferenceError: y is not defined
```

Variables declared with `var` are hoisted to the top of their scope and initialized with `undefined`. This means you can reference the variable before its declaration, although it will be undefined until the declaration line is reached.

```js
var x = 42;
function example() {
  console.log(x + " " + y); // 42 undefined
  var y = 24;
  console.log(x + " " + y); // 42 24
}
example();
```

You can re-declare a variable using var without throwing an error.

```js
var x = 5;
var x = 42; // No error
console.log(b); // 42
```

## Let

`let` is block-scoped, meaning it is only accessible within the block ({}) in which it is declared.

```js
// a globally scoped variable
let x = 42;
function example() {
  // a locally scoped variable
  let y = 24;
  console.log(x + " " + y); // 42 24
}
example();
console.log(x + " " + y); // ReferenceError: y is not defined
```

Unlike `var`, it is not initialized with `undefined`. If you try to access it before its declaration, you’ll get a `ReferenceError`.

```js
let x = 42;
function example() {
  console.log(x + " " + y); // ReferenceError: Cannot access 'y' before initialization
  let y = 24;
  console.log(x + " " + y);
}
example();
```

You cannot re-declare a variable with let in the same scope.

```js
let x = 5;
let x = 42; // SyntaxError: Identifier 'x' has already been declared
console.log(b); // 42
```

## Const

`let` and `const` share many similar behaviors with respect to scope:

```js
// a globally scoped variable
const x = 42;
function example() {
  // a locally scoped variable
  const y = 24;
  console.log(x + " " + y); // 42 24
}
example();
console.log(x + " " + y); // ReferenceError: y is not defined
```

`const` behaves similarly to `let` if you try to access it before its declaration, you’ll also get a `ReferenceError`.

```js
const x = 42;
function example() {
  console.log(x + " " + y); // ReferenceError: Cannot access 'y' before initialization
  const y = 24;
  console.log(x + " " + y);
}
example();
```

`const` is used to declare constants, meaning the value assigned to a `const` variable cannot be reassigned.

```js
const x = 42;
x = 24; // TypeError: Assignment to constant variable.
```

Unless of course the constant is an object or array, the properties or elements of that object or array can still be modified.

```js
const x = [];
x.push(42, "beep", false, ["boop", [99]]); // shockingly, this is legal
```

You cannot re-declare a variable with `const` in the same scope.

```js
const x = [];
const x = []; // SyntaxError: Identifier 'x' has already been declared.
```

## Why are there so many choices?

Because JavaScript. All these options reflect the evolution of the language.

## When do I use what?

Best practice is to use `const` by default and `let` when you need to reassign. `var` tends to come in handy if you need function-scoped variables, though this is less common in modern JavaScript. Unfortunately, if you work with older software or legacy code developed over the past 30 years, you may still come across all these variable declaration options.

# Exercise 1

For the following Pen and Complete the following logic:

- Create an adoption center name, this shouldn't change over the course of your program.
- Initialize a variable to track the total number of cats adopted.
- Implement a function that simulates the process of adopting a cat.

```js
const centerName = "Cute Cats Adoption Center";
let adoptedCats = 0;

function adoptCat() {
  adoptedCats++;
  console.log(`Total adopted cats: ${adoptedCats}`);
}
```

# Exercise 2

In this exercise, you'll manage a global array of cat names and use the `adoptCat()` function to randomly select a cat for adoption. This will help you understand variable scope and random selection in JavaScript.

What you will need to randomly select a cat:

```js
Math.floor(Math.random() * arrayLength);
```


# Variable Declaration Lowdown

The best practice is to use `const` by default, reserving `let` for cases where reassignment is necessary. While `var` can be useful when you need function-scoped variables, it is less common in modern JavaScript.

```js
const x = "I am the best";
let y = "use me in loops and such";
var z = "Why are you using me 👀";
```

# Scope

The lifetime of a JavaScript variable begins when it is declared. Local variables exist only within the function or block where they are defined and are removed when the function or block completes, meaning they are no longer accessible.

Understanding the scope of variables helps in managing and organizing code effectively, ensuring that variables are used correctly within their intended context.

```js
// a globally scoped variable
const x = 42;
function example() {
  // a locally scoped variable
  const x = 24;
  console.log(x);
  // end of local x's lifetime
}
example();
// end of global x's lifetime
```

When trying to access an identifier, the JavaScript Engine will first look in the current function:

```js
const x = 42;
function example() {
  const x = 24;
  console.log(x); // 24 will print because it is in the current function
}
example();
```

If it does not find the identifier in the current scope, JavaScript will search for it in the next outer scope. This process continues until it reaches the global scope.

```js
const x = 42;
function example() {
  const y = 24;
  console.log(x); // 42 will print because it is declared globally
}
example();
```

Global identifiers can introduce risks, so it is important to understand when their use is appropriate. Examples of global identifiers include variables, functions, or objects that can be accessed from any part of your code. Being mindful of their scope helps prevent potential conflicts and unintended behaviors.

# Global Identifiers

## Constants or Configuration Values

Global identifiers are useful for values that should remain consistent throughout your entire application and are unlikely to change, such as environment variables or configuration settings. For example:

```js
const BASE_URL = "https://example.com/";
```

It is a best practice to use uppercase letters with underscores to declare these constants, making it clear that they are intended to never change.

## Libraries

When you are developing or utilizing a library or framework that needs to make certain functions or variables accessible across different parts of your application, global identifiers can be necessary. For example:

```js
window.myLibrary = {
  greet: "hallo",
};
```

In this case, global identifiers ensure that the library’s functions and variables are available throughout your application, allowing different parts of your code to interact with them.

## What does this look like in action?

For an example of defining constants, take a look at where I set up my constants 👉 [NOTES_BASE_FOLDER](https://github.com/elizabeth-poggie/elizabeth-poggie/blob/main/pages/notes/index.tsx#L16). This setup ensures that the notes I create are specifically tied to John Abbott College.

## The Risks

Despite their usefulness, global identifiers should generally be avoided. Here’s why:

- Conflict Risk 👉 Global identifiers can lead to conflicts, especially in larger projects or when integrating multiple libraries.
- Security Concerns 👉 They can be accessed and modified by any script on the page, which might create security vulnerabilities.
- Testing Challenges 👉 They can complicate unit testing because their state persists across different tests. This will be covered in Web 2.

Returning to my code, I use the following constant to track my base folder:

```js
const NOTES_BASE_FOLDER = "john-abbott-college";
```

If I switch to a new job at another college or want to include notes from my undergraduate studies, I’ll face the challenge of refactoring a lot of code and deprecating a variable. While this approach works for my current small codebase and limited user base, it could become a significant issue in the next five years as the project grows.

## Best Practices

- Minimize Global Identifiers 👉 Use global identifiers sparingly. Instead, prefer local scope, functions, or closures to manage your variables and functions. This approach helps keep your code organized and prevents potential conflicts.
- Leverage Module Systems 👉 Modern JavaScript supports module systems that confine variables and functions to the module level. However this concept is outside the scope of this lecture.

# Hoisting

## What is it?

Hoisting is a concept in JavaScript that allows variables and functions to be used before they are explicitly declared in the code. Here’s an example from our last class:

```js
var x = 42;
function example() {
  console.log(x + " " + y); // 42 undefined
  var y = 24;
  console.log(x + " " + y); // 42 24
}
example();
```

In this example, only the declarations of variables are hoisted to the top of their scope, not their initializations. As a result, `y` is `undefined` when it is first accessed because its value is assigned later in the code.

## What can be hoisted?

Only variables declared with `var` are hoisted. Declarations made with `let` or `const` are not hoisted.

## What are more examples of hoisting?

This code WILL NOT run:

```js
test = "hi"; // ReferenceError: Cannot access 'test' before initialization
let test = "bye"; // No hoisting for 'let' or 'const'
console.log(test);
```

This code WILL run and print `"bye"`:

```js
test = "hi"; // no error 👉 variable declared using 'var' is hoisted
var test = "bye"; // Variable declaration is hoisted
console.log(test);
```

This code WILL run:

```js
console.log(test); // undefined 👉 only the declaration is hoisted
var test = "bye";
console.log(test); // bye
```

This code WILL NOT run:

```js
console.log(test); // ReferenceError: Cannot access 'test' before initialization
let test = "bye"; // No hoisting for 'let' or 'const'
console.log(test);
```

# Objects

JavaScript objects are a data structure that allow you to store collections of related data and more complex entities. They are made up of key-value pairs, where each key is a string (or a symbol) that is associated with a value, which can be of any data type, including functions or even other objects.

```js
const student = {
  firstName: "Arthur",
  lastName: "Dent",
  id: 1234567,
  greeting: function () {
    return "don't panic";
  },
};
```

In this example, the `student` object includes properties like `firstName`, `lastName`, and `id`, as well as a method `greeting` that returns a string. This helps keep my code ✨ CLEAN ✨

_NOTE: properties and methods within the object are separated by commas._

## Accessing Properties

You can access object properties in a couple of ways:

```js
// You can access it like you may be familiar with arrays
student["firstName"];

// dot notation is also fair game
student.firstName;

// Invoking a method
student.greeting();
```

## Property Conventions

When naming properties, follow these conventions:

- Do not use quotation marks around property names.
- Use `camelCase` for naming conventions
- Avoid starting property names with a number, including spaces, or using hyphens.

```js
// trash example
var car = {
  "model name": "tesla",
};
console.log(car.model name); // Uncaught SyntaxError: missing ) after argument list

// good example
const betterCar = {
  modelName: "tesla",
};
console.log(betterCar.modelName); // tesla
```

Following these conventions helps ensure your code is clean and avoids weird errors at run time.

# Exercise 1

Create a breakfast object to represent the following menu item:

```text
The Lumberjack - $9.95
eggs, sausage, toast, hashbrowns, pancakes
```

Your object should include the following properties:

- `name`: The name of the menu item
- `price`: The price of the menu item
- `ingredients`: An array of ingredients included in the menu item


# Accessing properties from within an object

Within an object method, the `this` keyword refers to the object itself, allowing you to access other properties and methods.

Using our breakfast example, let's say we want to add an ingredient to the ingredients array. Here’s how you might do that:

```js
const breakfast = {
  name: "The Lumberjack",
  price: 9.95,
  ingredients: ["eggs", "sausage", "toast", "hashbrowns", "pancakes"],
  addIngredient: function (newIngredient) {
    this.ingredients.push(newIngredient); // notice the `this` keyword
  },
};
```

When you run the following code, it will update the object:

```js
// ofc coffee MUST be included
breakfast.addIngredient("coffee");

// now print again
console.log(
  `${breakfast.name} - $${
    breakfast.price
  } \n${breakfast.ingredients.toString()}`
);
```

To avoid duplicating code and to make our solution more concise, we can add a `print` method to the `breakfast` object:

```js
const breakfast = {
  name: "The Lumberjack",
  price: 9.95,
  ingredients: ["eggs", "sausage", "toast", "hashbrowns", "pancakes"],
  addIngredient: function (newIngrediant) {
    this.ingredients.push(newIngrediant);
  },
  print: function () {
    // Print the details of the breakfast
    console.log(
      `${this.name} - $${this.price} \n${this.ingredients.toString()}`
    );
  },
};
```

Now, to see any updates to our object, we can simply call:

```js
breakfast.print();
```

# Exercise 2

Create an object called `instagramProfile`. This object should include the following three properties:

- Your `name`
- the number of `friends` you have
- an array of `messages` you've posted as strings

Additionally, the object should contain two functions:

- `addFriend()` that increases the friend count by 1
- `removeFriend()` that decreases the friend count by 1


