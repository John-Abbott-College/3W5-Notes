# Test 2a \- November 27th \- 12%

> Assumption: you are able to apply the already covered JavaScript basics (events, DOM manipulation, scope of let/var/const, script tags and defer, arrow notation, etc)
>

* #### Script tags (do not need to know what async does)

  - with a src attribute set, run when encountered unless defer is used
    - defer:
      -  doesn’t block page load while retrieving
      - Only run the Javascript when the DOM is ready
    
  - Directly in a script element in the html
    - Cannot use defer
    - Code is run as soon as it is encountered
    
    

* #### Node.js

  * What is it? A JavaScript run-time environment + lots of useful packages

  * Running JavaScript on your computer directly instead of in a browser. 

  * Advantages:

    - uses JavaScript 
      - Same syntax for front-end developers
    - Many packages/libraries available
      - database, file system access, etc.

  * npm is the node.js package manager. It comes with node.js

    -  package.json is the file npm uses to track packages that are installed

    - Allows you to download and manage packages for node.js

      - Takes care of downloading any dependent packages as well.
      - To add a package.json (to a new project for example): 

      \> npm init

      - When you have a package.json file, install all packages in its list of dependencies

      \> npm install

      - To install a specific package: npm install <packageName>
      - the package will be dowloaded into the node_modules directory

      If you have a package.json, the package name will be added to the list of dependencies.  

    - We used Node.js to code a web server which serves web pages to a browser that requests them.

      * Webserver running on Node.js is coded in JavaScript, run by the Node.js JavaScript engine we installed on our machine.
      * The browser asks our web server for files to show in the browser. These files could have JavaScript in them. The browser runs this JavaScript code with its in-browser JavaScript engine.
      * It is normal that I am coding JavaScript in node.js to create my webserver and that, in response to an HTTP request, I (the webserver running on node.js) am sending back a file that contains JavaScript code to be run by the browser.

      

* #### JS Modules

  * (syntax will be provided) Given a function in one .js file, be able to expose it as a module and be able to use it in a different .js file:

  * CommonJS:
    * in **myModule**.js:
      * module.exports = { **myFunction** }; 

    * in index.js:
      * const { **myFunction** } = require("./utils/**myModule**"); console.log(myFunction());

  * ESModules
    * need to change package.json to add "type": "module"
    * in **myModule**.js:
      * export function **myFunction**() { ... }; 
    * in index.js:
      * import { **myFunction** } from "./utils/**myModule**.js"; console.log(myFunction());


  

* #### Lazy loading images

  * What is it

    * Deferring the loading of images to when the user is about to see them
    * Why is it a good idea?
      * Smaller web pages load faster
      * Cost savings if image never loaded because never about to be seen

  * How

    * Do not set the src attribute on the image up front, so it does not get loaded. 

    * Give the img element a size so its collapsed state does not make it appear in the viewport unintentionally, triggering some lazy loading techniques.

    * Only when you want to the browser to bother loading the image, set the src

      

* #### IntersectionObserverAPI

  - Available in JavaScript

  - We used it for lazy loading of images, but it is a flexible API to do anything when any of a set of tracked elements intersects (or stops intersecting) with a specified parent.

  - Create the observer
    - Give it the function to run when one of the observed elements intersects with the viewport (by default).
    - Optionally pass it an **object** with custom intersection parameters
      - Default: the viewport is the root, the intersection threshold is 0
      - The **threshold** property can be set to indicate how much of the element needs to intersect
      - These intersection options apply to all the observed elements

  - Tell the observer which elements to observe, by passing them in a call to observe on the observer - one at a time.

  - In the function you told the observer to run (when any of the observed elements intersects):
    - You receive, as a parameter, an array of IntersectionObserverEntry (not the element directly) objects, one per element for which an intersection change has occurred.
      - The observer sends you this array to give you intersection information on the elements that had a change among the ones you told it to observe
      - Each IntersectionObserverEntry has the observed element that intersected/stopped intersecting in the **target** property
      - Each IntersectionObserverEntry has other properties too, **isIntersecting** is useful in knowing if this element is intersecting (stopped or started intersecting) when the function was called by the observer. 
    - You could do whatever you want in this function.
      - For images that are now intersecting, we set the src property on the image elements (element.src) to the full size images so the browser only loads them then (when they come into the viewport)
        - We had stored the image location in the data-src attribute (accessible in JavaScript on the element object via the element.dataset.src property).
        - The img elements are in the target property of the IntersectionObserverEntry objects we receive in an array in the function.

  - You can call the unobserve function on the observer o unobserve an element (tell the observer to no longer track it).

    

* #### Using data-x HTML element attributes and retrieving the value in JavaScript

  * set them in the HTML

  * for lazy loading of images, we set the real image's src URL in its data-src attribute to easily associate the src to use when we are ready to set it on the img.

  * retrieve the values in JavaScript via the dataset property on the element object. The dataset property holds an object with a property called **x** for every data-**x** HTML attribute.

    * for example, for an element <p id="theId" data-bob="chips"></p>

      ```javascript
      console.log(document.getElementById("theId").dataset.bob) 
      ```

      would log "chips" to the console


  

  
