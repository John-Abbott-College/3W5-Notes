# Minification

## What is it?

Minification is the process of removing unnecessary characters from code, like spaces, line breaks, and comments. It can even include shortening variable names. The key is that it doesn't change how the code works; it simply makes the file smaller.

## Who uses it?

Minification is a common practice in web development. It's used to reduce the size of files like JavaScript, CSS, and HTML, helping websites run more efficiently.

## Real World Example

Check out all the jQuery releases [here](https://releases.jquery.com/jquery/). You'll notice that each version includes a minified option.

## Why use it?

- Improved Performance 👉 Smaller files mean faster downloads, leading to quicker page loads.
- Reduced Bandwidth Usage 👉 Minified files use less bandwidth, which is great when you're dealing with bad wifi connections.

## How it works

Here's an example of a typical JavaScript file before minification:

```js
function greetUser(name) {
  console.log("Hello, " + name + "!");
}

greetUser("Bob");
```

Minification usually removes things like:

- whitespace
- variable names
- comments

After minification, the file might look like this:

```text
function greetUser(n){console.log("Hello, "+n+"!")}greetUser("Bob");
```

If you run this in the Chrome DevTools console, you'll see it works exactly the same.

## How to avoid manually minifying

To automate the minification process in VSCode, you can install the [Minify](https://marketplace.visualstudio.com/items?itemName=HookyQR.minify) extension. Once installed, you can minify a file by opening the command palette and typing `Minify`.

# Exercise

Try to minify your assignment 1. What happens?
