# Quick Recap

- What is Node.js? Node.js is a runtime environment that allows you to run JavaScript code on the server
- What is npm? npm (Node Package Manager) is the default package manager for Node.js
- What is the entry point of a node project? `index.js`
- What is the `package.json`? The `package.json` file contains metadata about the project
- What happens if i delete `node_modules` from my project? How do I get them back? Deleting the `node_modules` folder removes all installed packages. To restore them, run `npm install`

# Exercise 1

As an exercise, set up a Node.js project and install `express` and `lodash`. Try to use `lodash` in your `index.js` by referring to the [official docs](https://lodash.com/docs/4.17.15) in order to use the lodash array groupBy function to group on the age property of an array of cat objects.



# Modules

So far, we have learned how to import modules created by others, but what if we want to create our own?

## Getting Started

Imagine you have some JavaScript code contained in a single file. You can turn this code into a module by exporting it. This allows other files to use an `import` statement to include your file as a dependency.

## What is a module?

A file that exports some code.

## Why is this so cool?

Creating modules helps developers organize their code within projects and share it with others through package managers like `npm`

## How do you export your code?

The method you choose to export your code will determine how other files import it. There are two main approaches to creating a custom module:

- ESModules: This is the modern approach that uses `import`/`export`
- CommonJS: This is the traditional method that uses `require`/`module.exports`

We will cover both methods in this lecture.

# ESModules

The `import` syntax is part of the newer module system that follows the ECMAScript standard. It is natively supported by modern browsers and the latest versions of Node.js. While it may require some additional setup, it provides a clear and structured way to manage modules. Here’s how it works:

## Names

```js
// Named Export Statement
export const name = "value";

// Named Import Statement
import { name } from "...";
```

## Default

Default Export Statement:

```js
// Default Export Statement
export default "value";

// Default Import Statement
import anyName from "...";
```

## Rename

You can also rename exports during the export and import processes.

```js
// Rename Export Statement
export { name as newName };

// Rename Import Statement
import { newName } from "...";
```

## Lists

You can export and import multiple items, including renaming some of them.

```js
// List + Rename Export Statement
export { name1, name2 as newName2 };

// List + Rename Import Statement
import { name1 as newName1, newName2 } from "...";
```

By using these `export` and `import` patterns, you can manage dependencies in your projects, making your code easier to maintain.

# CommonJS

The `require` function represents the older module system, primarily used in earlier versions of Node.js. By default, Node.js treats files as CommonJS modules. Here’s how it works:

```js
// CommonJS Import Statement
const { name } = require("...");

// CommonJS Export Statement
module.exports = { name };
```

# When do I use which method?

If you are working with modern JavaScript frameworks or libraries, such as React or Vue, the recommended approach is to use `import` for modules. This is especially true for new projects.

If you are maintaining older projects or working on projects that need to be backwards compatible, then using `require` is the preferred method.

## Do I need to know both?

Yes. Throughout your career, you will likely encounter both methods.

# Modules in Practice

Let’s create a new subfolder named utils where we will develop our own custom module called `customModule.js`. Your folder structure should look like this:

```md
node-app
├── node_modules
├── utils
│ ├── customModule.js
├── index.js
├── package-lock.json
├── package.json
```

Now we can begin developing reusable code. Let's start with something simple that we often need to rewrite in our projects: text formatting.

_Fun fact: In the industry, you rarely start a Node project from scratch. Instead, you often build upon the work of many others, using existing libraries, frameworks, and modules_ :^)

## CommonJS Approach

In `customModule.js`, let’s add the following code:

```js
function caps(input) {
  if (!input || typeof input !== "string") {
    return null;
  }
  return input.toUpperCase();
}

module.exports = { caps }; // notice me
```

Next, in `index.js`, you can import the code like this:

```js
// notice me
const { caps } = require("./utils/customModule");

console.log(caps("ahhhhhhhhhhhh"));
```

When you run the following command in your terminal:

```bash
node .
```

You should see the following output:

```text
AHHHHHHHHHHHH
```

Now, let’s take the more modern approach to modules

## ESModules

To inform Node.js that we want to use the modern approach, add the following line to your `package.json`

```json
{
  "type": "module", // notice me
  "dependencies": {
    "express": "^4.21.0",
    "lodash": "^4.17.21"
  }
}
```

This configuration tells Node.js to interpret `.js` files as ESmodules. Now, we can modify `customModule.js` to use the modern `export` syntax:

```js
export function caps(input) {
  if (!input || typeof input !== "string") {
    return null;
  }
  return input.toUpperCase();
}
```

In `index.js`, import it using the following syntax:

```js
import { caps } from "./utils/customModule.js";

console.log(caps("ahhhhhhhhhhhh"));
```

This achieves the same functionality as before.

