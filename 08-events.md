# HTML Events

HTML events can occur due to browser actions or user interactions. Here are a few common examples:

- An HTML web page has finished loading
- An HTML input field was changed
- An HTML button was clicked

## Common Events

For those that are curious, you can see the full list [here](https://www.w3schools.com/jsref/dom_obj_event.asp). For this class, focus on the following events:

- `click` 👉 Triggered when an element is clicked.
- `dblclick` 👉 Triggered when an element is double-clicked.
- `change` 👉 Triggered when the value of an input element has been changed.
- `mouseover` 👉 Triggered when the mouse pointer hovers over an element.
- `mouseout` 👉 Triggered when the mouse pointer leaves an element.
- `load` 👉 Triggered when an element (usually an image or script) has finished loading.

## Reacting to Events

JavaScript can respond to events by executing code when certain actions occur on HTML elements. For example:

```js
<button onclick="doStuff()">What are you doing?</button>
```

Here, the attribute `onclick` on the `button` element triggers `doStuff()` function when the `button` is clicked.

```html
<button onclick="doStuff()">What are you doing?</button>
<p id="stuff"></p>
<script>
  function doStuff() {
    document.getElementById("stuff").innerHTML = "I'm doing stuff, excuse you.";
  }
</script>
```

In this code, the `doStuff()` function updates the content of the `<p>` element with the id `stuff` to display a message. The `onclick` attribute is used to "listen" for the click event on the button and execute the specified function in response.

## Event Listeners

Instead of using HTML attributes to handle events, you can use JavaScript to add "event listeners" to elements on your page. For example:

```html
<button>What are you doing?</button>
<p id="stuff"></p>
<script>
  document.addEventListener("click", function () {
    document.getElementById("stuff").innerHTML = "I'm doing stuff, excuse you.";
  });
</script>
```

In this example, the `addEventListener` method is used to attach a `click` event listener to the `document`. When the `document` is clicked, the specified function is executed, updating the content of the `<p>` element.

## Arts & Crafts

Why is this so cool? Now we can have a lot more fun creating interactive web pages. Let's say we have the below HTML page with a sad cat:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Cat Pat Demo</title>
    <style>
      #cat {
        width: 200px;
        height: auto;
      }
    </style>
  </head>
  <body>
    <img id="cat" src="./sad-cat.jpg" alt="sad cat" />
  </body>
</html>
```

Suppose we want to change the image to a happy cat when the mouse hovers over it (`mouseenter` event) and revert it back to the sad cat when the mouse leaves (`mouseleave` event). Well we can do that :^)

Add the following to the `<script>` section

```js
const image = document.getElementById("cat");
image.addEventListener("mouseenter", () => {
  image.src = "./pet-cat.png";
});

image.addEventListener("mouseleave", () => {
  image.src = "./sad-cat.jpg";
});
```

Purfection. This code listens for `mouseenter` and `mouseleave` events on the image and updates the `src` attribute to show the appropriate cat image >:^)

To improve code maintainability, you can define the image URLs as constants and organize the JavaScript code a bit better:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Cat Pat Demo</title>
    <style>
      #cat {
        width: 200px;
        height: auto;
      }
    </style>
  </head>
  <body>
    <img id="cat" src="./sad-cat.jpg" alt="sad cat" />
    <script>
      const image = document.getElementById("cat");
      const sadCatSrc = "./sad-cat.jpg";
      const happyCatSrc = "./pet-cat.png";

      image.addEventListener("mouseenter", () => {
        image.src = happyCatSrc;
      });

      image.addEventListener("mouseleave", () => {
        image.src = sadCatSrc;
      });
    </script>
  </body>
</html>
```

# Exercise 1

Create an event listener that displays an `alert` whenever a user clicks on a camera. Make sure the `alert` message reflects the correct cat name.



# Exercise 2

Set up an event listener to change the profile image when a user hovers over it. The image should revert to the original when the user moves the mouse away.



