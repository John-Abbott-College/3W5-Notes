# Intro to APIs

In today’s connected world, we rely on instant access to just about everything, whether it’s products, knowledge, or services. If I want any product, I can have it delivered to my doorstep within 24 hours thanks to Amazon. If I want to learn something about web development, chances are someone on Youtube has already posted a tutorial about it.

In a lot of ways, everything I want, I can get almost instantaneously.

## How does this happen?

How does data get from here to there? How does it move across systems, from me to you, or from one device to another?

![demo](C:/Users/helen.katalifos/OneDrive - John Abbott College/Documents/GitHubRepos/3W5-Notes/assets/1AJAX.png)

The unseen force behind this seamless exchange is the Application Programming Interface, or API for short:

![demo](C:/Users/helen.katalifos/OneDrive - John Abbott College/Documents/GitHubRepos/3W5-Notes/assets/2AJAX.png)

# What is an API?

An API is like a messenger: it takes a request, tells a system what you want, and returns a response.

## Conceptual Example

Think of an API like a waiter at a restaurant.

![demo](C:/Users/helen.katalifos/OneDrive - John Abbott College/Documents/GitHubRepos/3W5-Notes/assets/3AJAX.png)

Picture yourself at a restaurant with a menu of choices and a kitchen where orders are prepared.

![demo](C:/Users/helen.katalifos/OneDrive - John Abbott College/Documents/GitHubRepos/3W5-Notes/assets/4AJAX.png)

What’s missing? A link that communicates your order to the kitchen and brings the food back to your table. That’s where the waiter comes in.

![demo](C:/Users/helen.katalifos/OneDrive - John Abbott College/Documents/GitHubRepos/3W5-Notes/assets/5AJAX.png)

The waiter is the messenger that takes your order (request), tells the kitchen (system) what to prepare, and then brings the completed dish (response) back to you.

![demo](C:/Users/helen.katalifos/OneDrive - John Abbott College/Documents/GitHubRepos/3W5-Notes/assets/6AJAX.png)

## Real World Example

Let’s take a look at the [Pokemon API](https://pokeapi.co/)

Similar to ordering from a menu, you can choose what information you want from the API by referencing the available options in the [docs](https://pokeapi.co/docs/v2)

Any useful API in the modern age uses detailed documentation that explains each of the endpoints.

Now, open [Postman](https://www.postman.com/) (or [Download it here](https://www.postman.com/downloads/)). If you don't already have an account, create one. If you can't download the Desktop App on the schools computer, use the [web interface](https://web.postman.co/) instead :)

In this example, Postman works like the tablet waiters give you at those unlimited sushi restaurants. It’s a tool that lets you communicate what you want, just like telling the waiter—or in this case, the API—your order.

To get started, let’s create a "Pokemon Collection" and add a "New Request." Using Postman, we’ll send a simple "GET" request to call the API and retrieve my favorite Pokemon:

```text
https://pokeapi.co/api/v2/pokemon/ditto
```

What is this response type anyways? Why is the default response `JSON`?

See the notes about JSON.

# Exercise 1

Now it's your turn. Setup postman, and use the Pokemon API to fetch information on your favorite Pokemon :^)

# Account Required APIs

The Pokémon API is a great example of an API that doesn’t require you to create an account or pay for access. However, for most APIs, that’s not usually the case.

## Api Keys

API keys are unique identifiers used to authenticate requests to an application programming interface (API). They function like a "password," allowing the server to identify who is making a request and whether they have permission to access specific data or features.

# AJAX

## How can we make server requests?

For the purposes of this class, we will be learning how to use AJAX to make requests to a server.

## What is AJAX?

AJAX (Asynchronous JavaScript and XML) allows web applications to send and retrieve data from a server asynchronously.

## How does it work?

![ajax](C:/Users/helen.katalifos/OneDrive - John Abbott College/Documents/GitHubRepos/3W5-Notes/assets/ajaxasync.gif)

Why is this so neat? It allows parts of web pages to be asynchronously updated without reloading the whole page.

## How do you make a server request with AJAX?

The browser sends a request to the server via JavaScript, typically using the `XMLHttpRequest` object or using the more modern `fetch` API.

When you make a request to the server, you are being "promised" by that server that it will get the data you desire.

## How is that response consumed?

Once you get that response, it is consumed as a "Promise" with the contents of that message containing the data that was "requested".

## What happens to the Webpage?

Once JavaScript has finished processing the response, it updates specific parts of the webpage dynamically.

## Docs

You can read more about it [here](https://www.w3schools.com/xml/ajax_intro.asp)

## AJAX requests

AJAX requests allow us to interact with APIs to `fetch` or `send` data without requiring a full page refresh. This technique is commonly used in web applications and will likely be part of your future careers.

## XMLHttpRequest

`XMLHttpRequest` was the original way to send asynchronous requests from JavaScript. While it’s a bit more complex, it provides a solid understanding of how AJAX actually works:

```js
// Step 1 👉 create the object
const xhr = new XMLHttpRequest();

// Step 2 👉 Init the request
xhr.open("GET", "https://pokeapi.co/api/v2/pokemon/ditto", true);

let data;

// Step 3 👉 Define the function that will run when the request is completed
xhr.onload = function () {
  // Step 4 👉 check if response is not trash
  if (xhr.status === 200) {
    // Step 5 👉 Read JSON
    data = JSON.parse(xhr.responseText);
    // Step 6 👉 print data
    console.log(data);
  } else {
    // handle if request is trash
    console.error("Request is trash with status:", xhr.status);+
        
  }
};

// more error handling
xhr.onerror = function () {
  console.error("WHAT IS THIS TRASH?????");
};

// Step 7 👉 Send to the API
xhr.send();
```

What's happening with the syntax?

- `open()` prepares a request to an API endpoint
- `onload` processes the response if successful, and `onerror` handles failures
- `send()` sends the request

Why am I logging the data inside the `onload`?

- If you add a `console.log(data);` statement at the end of everything, it will run before the AJAX request completes, which is why it will print `undefined`. The console log is prioritized by the event loop, while API requests are treated as "micro" asynchronous tasks.

# Using XMLHttpRequest

All modern browsers have a built in XMLHttpRequest object:

```js
let xhttp = new XMLHttpRequest();
```

## GET requests

If I want to make a GET request to a server using this object, it would be as follows:

```js
xhttp.open("GET", "<url>", true); // true ~ asynchronous
xhttp.send(); // send request
```

## Example

Let's explore the following:

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

console.log( superheroes );
```

As a reminder:

- `open()` prepares a request to an API endpoint
- `onload` processes the response if successful (and `onerror` handles failures)
- `send()` sends the request

# Exercise 1

Using an XMLHttpRequest object, retrieve and display for the user: the most probable country id for any name the user of your webpage enters into a textbox. 

Create a textbox with a button (do not use a form here since we want to remain on the page and update it with information).

When the user clicks the button, use the XHR to make an HTTPRequest to [https://api.nationalize.io](https://nationalize.io/). Look at the API documentation to see the GET parameters to send in the URL. 

example: https://api.nationalize.io/?name=michael&apikey=d111c2870371b078487afe38fb9066c4



# Exercise 2

Using an XMLHttpRequest object, retrieve and display for the user:

the topic and highlight from the 1st result received on https://www.edgechat.ai/mcp

Go to the Dev link and figure out the URL you would use to give encyclopedia results to your user for anything they want to search.



```html
<!DOCTYPE html>

<input type="text" id="theSearch"/>
<button>Search</button>
<h2 id="categoryLabel">The category of your item is:</h2>
<h3 id="category"></h3>

<h2 id="infoLabel">Information on your item:</h2>
<h3 id="info"></h3>
<script>

    "use strict";
    document.addEventListener("DOMContentLoaded", ()=>
    {
        
        //your code here!
        
    });

</script>
```

