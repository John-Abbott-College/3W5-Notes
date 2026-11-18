# JSON

We covered JSON at a high level in previous classes, today we cover it in greater detail

## What is it?

- A standard text-based format for representing structured data that's _very_ popular
- It's based on JavaScript object syntax, but it is independent of JavaScript (could be used anywhere)

## When do we use it?

- It's often used to transfer data from web server to browser (client).
- When we transfer it, it is represented as a string because that's great for transfer.

## How do we make sure JavaScript is happy when dealing with JSON?

JavaScript provides a JSON object with methods to convert it to a JavaScript object.

# JSON vs JavaScript

## JSON data types

In JSON, values must be one of the following data types:

- a string (e.g. `"Don't Panic"`)
- a number (e.g. `42`)
- an object (e.g. JSON object)
- an array (e.g. `[stuff]`)
- a boolean (e.g. `true`/ `false`)
- `null` (angry user defined error)

## JavaScript data types

In JavaScript values can be all of the above, plus any other valid JavaScript expression, including:

- a function (e.g. `() => stuff`)
- a date
- `undefined` (angry JavaScript defined error)

## Examples

JSON Syntax:

```json
{
  "name": "Arthur Dent",
  "age": 42,
  "isPanicking": false,
  "items": ["blanket", "towel", "coffee"],
  "spaceship": null
}
```

Fun fact with the [autoformatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) when you assign this object to a constant will immediately turn it into a JavaScript object :^)

JavaScript Object Syntax:

```js
// you cant put comments in a json file
const arthur = {
  name: "Arthur Dent",
  age: 42,
  isPanicking: false,
  items: ["blanket", "towel", "coffee"],
  spaceship: undefined, // JSON doesn't support undefined lol
  panic() {
    this.isPanicking = true;
    console.log("AHHHHHHH");
  },
};
```

## Key differences

JSON requires _double_ quotes to be used around _property names_ and _values_ that are strings (unlike in JavaScript). Single quotes are not valid.

Even a single misplaced comma or colon can cause a JSON file to go wrong. (which is always lovely when it happens)

# Converting and Parsing JSON

Sometimes we want to receive JSON from a server and sometimes we are the server that wants to send JSON.

## Examples

JavaScript object => JSON

```js
const jsonString = JSON.stringify(arthur);
console.log(jsonString); // notice how some previously defined properties disappear
```

JSON => JavaScript object

```js
const processedArthur = JSON.parse(jsonString);
console.log(processedArthur);
```

# Usage and Best Practices

## Response.json()

Remember this example from yesterday?

```js
fetch("https://pokeapi.co/api/v2/pokemon/ditto")
  // Step 2 👉 Handle the response once retrieved
  .then((response) => {
    // Step 3 👉 is the response NOT trash?
    if (!response.ok) {
      // Step 4 👉 error if trash
      throw new Error("TRASHHHHHHHHH: " + response.statusText);
    }
    // Step 5 👉 parse JSON if not trash
    return response.json();
  })
  // Step 6 👉 now handle JSON
  .then((data) => console.log(data))
```

`response.json()` in JavaScript returns a Promise that resolves with the JavaScript object - it automatically parses the JSON for you, so you don't need to use `JSON.parse()` on the result.
