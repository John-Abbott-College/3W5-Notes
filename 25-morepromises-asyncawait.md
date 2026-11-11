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

## Solution

```js
// Step 1: Create an Essay
function writeEssay(essay) {
  return new Promise((resolve, reject) => {
    console.log("Creating essay...");
    setTimeout(() => {
      if (essay.content) {
        resolve({ ...essay, id: 1, status: "created" });
      } else {
        reject("Failed to write essay lol");
      }
    }, 3000);
  });
}

// Step 2: Review the Essay
function reviewEssay(essay) {
  return new Promise((resolve, reject) => {
    console.log("Reviewing essay...");
    setTimeout(() => {
      if (essay.status === "created") {
        resolve({ ...essay, status: "reviewed" });
      } else {
        reject("Didn't Review lol");
      }
    }, 3000);
  });
}

// Step 3: Submit the essay
function submitEssay(essay) {
  return new Promise((resolve, reject) => {
    console.log("Submitting Essay on Lea...");
    setTimeout(() => {
      if (essay.status === "reviewed") {
        resolve({ ...essay, status: "submitted" });
      } else {
        reject("Cannot submit essay: Omnivox is down again lol");
      }
    }, 3000);
  });
}

// Chaining the functions
writeEssay({ title: "Humanities Essay", content: "Wow this is an essay" })
  .then((essay) => reviewEssay(essay))
  .then((essay) => submitEssay(essay))
  .then((essay) => console.log("Essay status:", essay.status)) // Should print "submitted"
  .catch((error) => console.error(error));
```

# Async / Await

Alright, so we know that `Promises` made handling asynchronous code a lot easier than the old "callback hell" approach. But when you start chaining too many promises, the code can still get messy and hard on our retinas

## Where does Async Await come in?

`async` and `await` make your code look cuter and easier to follow by letting you write asynchronous code in a more natural way, almost like regular synchronous code (but not quite)

- `async` 👉 A keyword used to declare a function that will handle asynchronous actions
- `await` 👉 A keyword used to pause the function until a promise is `resolve`d or `reject`ed

Let’s rewrite our earlier example with `async` and `await` so you can see the difference.

## Rewriting our example

The synchronous helper functions stay the same, but the `teacherMustGrade` function now becomes an `async` function:

```js
// Declare the function with "async"
async function teacherMustGrade(assignment) {
  const deadline = new Date("2026-11-13");

  // TODO - Simulate a wait period of 3 seconds instead of 3 days

  const today = new Date();
  if (today <= deadline) {
    return { grade: 0.8, comments: ["blah", "blah"] };
  } else {
    throw new Error(
      `Teacher slept through their deadline and failed to grade your ${assignment.name}`
    );
  }
}
```

The `teacherMustGrade` function is marked as `async`, meaning we’ll need to `await` its result when we call it, like this:

```js
try {
  // "await" the response
  const feedback = await teacherMustGrade({
    name: "Assignment 3",
    content: "some really cool code",
  });
  // synchronous code can now be executed
  const response = checkGrade(feedback);
  sendTeacherDM(response);
} catch (error) {
  console.log(error.message);
}
```

With `try` and `catch`, error handling is now much more sleek since you can wrap everything in one simple block.

## Can we have awaits inside of async functions?

Yeees 👉 If we need to simulate a delay inside `teacherMustGrade`, we can use `await` as follows:

```js
// Simulate a wait period of 3 seconds instead of 3 days
await new Promise((resolve) => setTimeout(resolve, 3000));
```

💡 Note: Once you have an `await` in a function, the function itself must be marked `async`.

# Exercise 2

Take your Exercise 1 and transform it to work with `async` and `await`

