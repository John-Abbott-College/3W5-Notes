# Test 2b \- December 1st \- 13%

Assumption: you are able to apply the already covered JavaScript basics (events, DOM manipulation, scope of let/var/const, script tags and defer, debug JS code, etc)

* ### AJAX

  - A JavaScript technique
  - Use asynchronous JavaScript to get information from a web server and use the obtained information to update the already loaded page without reloading it.
  - Involves making an HTTPRequest to the web server and waiting for the HTTPResponse asynchronously.
  

- ### JSON

  - A text-based format in which you could represent structured data
  - Inspired by JavaScript object syntax, but not tied to JavaScript
  - Double quotes only (no single quotes)
    - Double quotes around property names too (unlike in JavaScript)
  - Often used by web servers to send data
  - Many languages, including JavaScript have easy ways to take in the JSON string and use it. In JavaScript JSON.parse( JSONString ) takes a JSON string and returns the equivalent JavaScript object.

- ### Promise

  - An object that represents the future (promised) result of an asynchronous operation.
  - When you create one (new Promise) you give it a function (executor) that takes in two functions: a resolve and a reject function (you assume that your promise executor function will be passed these functions by the Promise API)

let myPromise = new Promise( function( resolve, reject ){ 

​             //run code right away that triggers async work 

​           } );

- It is in the body of this function (that the promise is created with) that you trigger some async operation.
  - The function is started as soon as the promise is created. It is run synchronously. Usually this code sets up asynchronous operations.
  - The body must ‘settle’ the promise of a result by calling resolve or reject (all code paths should end up calling one of these). Usually this is set up to happen when the async operation finishes,
  - You can pass one argument in the calls to resolve or reject. This ‘thing’ is passed along in the functions specified in then() or catch() respectively.
- On a promise object, I could call then() passing it the function to call if the promise is resolved (usually when it finished the async operation successfully).
  - I could set a parameter on the ‘then’ function. On a resolve of the promise, the function will be called with whatever the resolve was called with: 
    - In the Promise’s function: resolve( “a” );
    - => in the then function: promise.then( function( param ){} ) //param will be “a”
- On a promise object, I could call catch() passing it the function to call if the promise is rejected (whenever the async operation failed).
  - I could set a parameter on that function. On a reject of the promise, the function will be called with whatever the reject was called with (often an error).

- Promise states: 
  - Pending
  - Settled:
    - Fulfilled (resolve was called)
    - Rejected (rejected was called)
- A settled promise will never change its state (cannot go back to pending or from resolved to rejected or vice versa).
- You can call then() or catch() on a settled promise, the function you pass to then() will be called right away if the settled promise is fulfilled, the function you pass to catch() will be called right away if the settled promise is rejected.

- ### Promise chain

- Useful when the result of one asynchronous operation is needed for the next asynchronous operation

- On a promise (promiseA), the then() function returns a promise. 

If the handler function passed into then() also returns a promise (promiseB), the promise returned by then() will resolve/reject with whatever the handler function promise (promiseB) resolves/rejects with.

- myPromise

.then( function( myPromiseResolveValue ){ return otherPromise; })

.then( function( otherPromiseResolveValue ) {});

- .catch( handlerFunction ) can be added to the chain. The handler function will be called when any promise in the chain is rejected.

- ### Promise.all

- I call it with an array of promise objects (Promise.all( [promiseA, promiseB, promiseC]);)

- It returns a promise (i.e. the megaPromise)

- That promise will be resolved ONLY when all the promises in the array are resolved.

- It is resolved with the array of the results of each of the promises.

- In a then function called on the megaPromise, I could specify a function with a parameter. When my function will be called, the parameter will be assigned the array of results from all the promises. 

- ### fetch API

  - The fetch call is given a URL and returns a promise (in that promise it does the HttpRequest to that URL and resolves the promise with the Response - all asynchronously).





be able to figure what is run when

See Moodle quizzes for important practice
