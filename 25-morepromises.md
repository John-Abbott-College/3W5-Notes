# Promises Continued

Let's continue what we talked about with a more concrete example.

## What is a promise?

It is something that is unknown now and may become known some time in the future.

## Promise code is run *synchronously*

Usually, though, you run asynchronous calls in the function it runs

- **The function runs immediately.** When you call `new Promise((resolve, reject) => { ... })`, the JavaScript engine executes the code inside the function right away on the current call stack. Any synchronous code inside it runs before the next line outside the Promise. 

  

- **Functions passed to then() and catch() run asynchronously.** Even if `resolve()` is called immediately inside the Promise function, the callbacks passed to `.then()` or `.catch()` never run right away. Instead, they are placed in the **microtask queue** and wait until the current synchronous call stack finishes executing. 

  

- **Promises do not make code asynchronous.** A Promise simply acts as a wrapper and a dependency chain for tasks. If you put heavy synchronous computation inside a `new Promise()`, it will still block the main thread immediately. Not what you want, normally!

 

## Promise.then() function

### Always returns a promise

Every call to `.then()` returns a new Promise, regardless of what its callback returns.

### The Promise returned by .then() resolves with whatever the function it is given returns

```javascript
Promise.resolve(5)
  .then(number => {
    return number * 2;  // returns a number, NOT a Promise
  })
  .then(result => //then is called on the Promise returned by the previous then()
        { 
   		   console.log(result); // 10
  });
```

Even though `number * 2` is just a number, the first `.then()` returns a Promise that resolves to `10`.

The difference is:

| What the `.then()` callback returns | What happens                                          |
| ----------------------------------- | ----------------------------------------------------- |
| A regular value (`10`)              | The new Promise resolves to `10`                      |
| A Promise (`response.json()`)       | The new Promise adopts that Promise's eventual result |
| Nothing                             | The new Promise resolves to `undefined`               |
| Throws an error                     | The new Promise rejects                               |



`response.json()` returns a Promise, and `.then()` itself also returns a Promise.

```javascript
fetch(url)
  .then(response => response.json())
  .then(data => console.log(data));
```

Here's what happens:

1. `fetch(url)` returns a Promise that eventually resolves to a `Response` object.
2. `.then(response => response.json())` calls `response.json()`, which returns another Promise that eventually resolves to the parsed JavaScript data.
3. `.then(data => console.log(data))` waits for that JSON Promise to resolve before executing.

You're actually doing two things:

- Calling `response.json()`, which returns a Promise.
- Returning that Promise from the callback, allowing the Promise returned by `.then()` to adopt its eventual result.

> `.then()` always returns a new Promise. If its callback returns another Promise, JavaScript automatically waits for that Promise to settle before passing its result to the next `.then()`.

That's why you can chain `.then()` calls indefinitely, whether you're returning regular values or Promises.

## From Concept to JavaScript

Your teacher "promises" to grade your Assignment 3. Here’s how this would look in JavaScript:

```js
function teacherMustGrade(assignment) {
  return new Promise(function (resolve, reject) {
    // teacher "promises" to grade your stuff
  });
}
```

Your teacher has set her grading deadline for Thursday, and they made this promise to the class on Wednesday. In JavaScript, this setup would look like this:

```js
function teacherMustGrade(assignment) {
  return new Promise(function (resolve, reject) {
    // Set a deadline (Friday)
    const deadline = new Date("2026-11-6");

    // simulate a wait period of 3 seconds instead of 3 days
    setTimeout(() => {
      // Get today's date
      const today = new Date();
      if (today <= deadline) {
        resolve(`The teacher graded your ${assignment.name} on time (wow)`);
      } else {
        reject(
          `The teacher slept through the deadline and failed to grade your ${assignment.name}`
        );
      }
    }, 3000);
  });
}
```

Initially, the promise is _pending_. After "3 days," the promise either gets `resolve`d (you receive feedback) or `reject`ed (you don’t get feedback)

Here’s how you’d call this promise:

```js
teacherMustGrade({
  name: "Assignment 3",
  content: "some really cool code",
});
```

Using `then` to handle the result of the promise once fulfilled would look like this:

```js
teacherMustGrade({
  name: "Assignment 3",
  content: "some really cool code",
})
  .then((message) => {
    console.log(message);
  })
  .catch((error) => {
    console.log(error);
  });
```

Since today is Wednesday, you should expect this output:

```text
Teacher slept thru her deadline and failed to grade your Assignment 3
```

But if your teacher had `resolve`d grading your assignment on time, you’d see:

```text
Teacher graded your Assignment 3 on time (wow)
```

## What if I want to “chain” multiple actions together?

For example, after your teacher has graded your assignment, you want to check Lea for your grade.

## Chaining

Let’s add a new function called `checkGrade` that takes a `feedback` object and returns a boolean indicating whether you’ve read it:

```js
// example feedback object
const feedback = {
  grade: 0.8,
  comments: ["blah", "blah", "blah"],
};

// example method
function checkGrade(feedback) {
  console.log(`grade: ${feedback.grade}`);
  feedback.comments.forEach((comment) => {
    console.log(`${comment}`);
  });
  return true;
}
```

Now, we’ll set the deadline for _Sunday_ and modify the resolve statement to return a `feedback` object:

```js
resolve({ grade: 0.8, comments: ["blah", "blah"] });
```

You only want to check Lea once you’re sure there’s feedback; otherwise, what's the point? Do you want to check Lea before the operation is complete? Absolutely not.

So, let’s handle the promise response only once there’s some sort of notification:

```js
teacherMustGrade({
  name: "Assignment 3",
  content: "some really cool code",
})
  .then((feedback) => {
    checkGrade(feedback);
  })
  .catch((error) => {
    console.log(error);
  });
```

## Why is this so neat?

We only trigger the `checkGrade` method AFTER the assignment is graded. What's cooler? We can keep chaining methods as needed :)

Let’s say you get a notification once you’ve checked your grade. Here’s what that would look like:

```js
// another method
function sendTeacherDM(res) {
  if (res) {
    console.log("wow the student left me on read");
  }
}
```

Now, we can consume these responses quite elegantly like so:

```js
// updated chaining
teacherMustGrade({
  name: "Assignment 3",
  content: "some really cool code",
})
  .then((feedback) => {
    return checkGrade(feedback); // notice the return
  })
  .then((response) => {
    sendTeacherDM(response);
  })
  .catch((error) => {
    console.log(error);
  });
```

## Helpful tip

When you start creating promises, it’s easy to mess it up. This is where effective error handling in your catch block is important 👀

# Exercise 1

You are a student that needs to submit an essay. Once this essay is created, it should be reviewed, and then finally submitted on Lea once finished. How could you do this in JavaScript?

## Requirements

Each task is asynchronous and takes `3000` milliseconds to complete.



# Promise.all

You can use the **all** function on the globally available Promise object to run promises concurrently. This allows you to specify what should happen only when they all resolve.

Pass in the array of promises.

The then function will be run only when ALL the promises resolve.

The **mega promise** will resolve with an array of what each promise was resolved with.

```javascript
Promise.all([promise1, promise2, promise3])//returns mega promise

.then( function (arrayOfThingsThePromisesResolvedWith) { })

.catch( function( error ) {});
```

If one fails all the other promises also stop executing. 



## Exercise

Using the pokemon API and Promise.all, retrieve the info for the 3 pokemon: ditto, pikachu and squirtle and only when you get all their info display their combined weight. 

reminder of the URL "https://pokeapi.co/api/v2/pokemon/ditto",

Hint: use a function to return the promise you get from the last then on a fetch.



### Exercise 2

Make sure you are clear on what is run when.

```javascript
  function foo()
  {   
   	alert("A");

	return new Promise( function(resolve, reject){
        alert("B");
	 	setTimeout( ()=>{ alert("C");
                          resolve()}, 0)
        alert("D");
	 } );
  }

  alert("E");

  foo()
  .then(()=>alert("F"));

  alert("G");
```



### Solution to Exercise 2

Alerts in order seen:
E
A
B //because function given to the Promise constructor is run synchronously
D // because setTimeout returns right away and the JS runner must finish running the function given to the constructor
G // because the .then sets up what should happen when the promise resolves but then returns right away
C // the JS runner is finally free, it can run the function setTimeout added to the queue
F // the promise resolved so the function passed to then is added to the queue and since the JS runner is free, it is run
