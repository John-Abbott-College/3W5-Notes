## Using fetch

The fetch API is a modern alternative to `XMLHttpRequest` that simplifies the syntax for handling AJAX requests. It is "promise-based", making it more intuitive to work with asynchronous data:

```js
// Step 1 👉 Init a fetch request
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
  // Always good to add error handling
  .catch((error) => console.error("Please observe the trash:", error));
```

With `fetch`, data handling is a bit more straightforward:

- The `.then()` blocks handle success and parse the JSON response.
- `.catch()` manages errors, making the code easier to follow and debug.

We will cover the idea of `promises` more next class, for now, get comfy making API requests.


# Exercise 1

Rewrite using the fetch API

```js
let requestURL =
  "https://mdn.github.io/learning-area/javascript/oojs/json/superheroes.json";
let request = new XMLHttpRequest(); // create the object

//set the URL to retrieve info from
request.open("GET", requestURL, true); 

//set the function that should be run when the response is received
request.onload = function () { 
      let superHeroes = request.response; //the JSON string from the response
      console.log(superHeroes);
    };

request.send();

```



Solution



```js
let requestURL =
  "https://mdn.github.io/learning-area/javascript/oojs/json/superheroes.json";

//set the URL to retrieve info from
fetch(requestURL)
.then((response) => {
    return response.json();
.then((superHeroes) => {console.log(superHeroes)});
```



# Async Operations Summary

Today we discussed the following async operations:

- Callbacks 👉 Functions passed as arguments that are executed once a task is completed.
- `Promise`s 👉 Objects representing a future result of an async operation, which can be resolved or rejected.

We will later cover `async` and `await` which is just a more readable syntax for working with Promises