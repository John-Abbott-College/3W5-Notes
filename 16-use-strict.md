
# Use Strict

To quote the official documentation:

```text
JavaScript's strict mode is a way to opt in to a restricted variant of JavaScript,
thereby implicitly opting-out of "sloppy mode"
```

## Why use it?

Using strict mode helps catch common coding errors and unsafe practices, making JavaScript easier and safer to work with.

## How to use it?

You can place the _directive_ at the beginning of a script or at the start of a function to apply it only to that function.

```js
"use strict"; // notice me
const stuff = "stuff";
// other stuff
```

```js
"use strict"; // notice me
function doStuff() {
  console.log("doing stuff");
}
```

## Benefits

Prevents Undeclared Variables 👉 In strict mode, trying to assign a value to an undeclared variable will throw a `ReferenceError`.

```js
x = 3.14; // ReferenceError: x is not defined
```

Prevents duplicate Parameter Names 👉 Strict mode disallows duplicate parameter names in function declarations.

```js
"use strict";
function addStuff(x, x, y) {
  return x + x + y; // Uncaught SyntaxError: Duplicate parameter name not allowed in this context
}
```

## Official Documentation

For more information, check out the official documentation on strict mode [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode).

## Compatibility

Strict mode is ignored by older browsers, such as Internet Explorer. However, if you are using modern browsers like Chrome, you should be good to go.

# Exercise (Group Competition)

Get together in groups of up to 3 people.

## The Task

Write the worst JavaScript code you can possibly think of that still compiles. Refer to the [official documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode) for inspiration.

Compare your results before and after applying strict mode. What is the worst piece of trash you can create that only gets flagged as an error when applying `"use strict";`?

