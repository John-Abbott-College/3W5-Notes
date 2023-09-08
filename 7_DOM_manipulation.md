# DOM Manipulation pt.2

Now that we've learned more JavaScript, we can expand on DOM manipulation.

<br>

## Adding and removing elements to the DOM

We've already inserted simple elements in the DOM using the `getElementById` method and the `innerHTML` property.



<iframe height="297" style="width: 100%;" scrolling="no" title="wk11 - inserting_1v2" src="https://codepen.io/maujac/embed/jOydjrP?height=297&theme-id=dark&default-tab=js,result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/jOydjrP'>wk11 - inserting_1v2</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>





!> Manually constructing HTML elements from strings of code can easily lead to typos and missed syntax.

<br>

**Use the methods below to construct, modify and insert DOM elements using JavaScript:**

<br>

| Method                                                       | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [document.createElement(*tagName*)](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement) | Creates an HTML element                                      |
| [*parentNode*.appendChild(*newChild*)](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild) | Adds an HTML element                                         |
| [*parentNode*.replaceChild(*newChild, oldChild*)](https://developer.mozilla.org/en-US/docs/Web/API/Node/replaceChild) | Replaces an HTML element                                     |
| [*parentNode*.insertBefore(*newChild*,*referenceChild*)](https://developer.mozilla.org/en-US/docs/Web/API/Node/insertBefore) | Inserts a node before a *reference node* as a child of a specified *parent node*. |
| [*parentNode*.removeChild(*child*)](https://developer.mozilla.org/en-US/docs/Web/API/Node/removeChild) | Removes an HTML element                                      |
| [*element*.remove()](https://www.w3schools.com/jsref/met_element_remove.asp) | removes the specified element from the DOM.                  |

<br>

### New element recipe 👨‍🍳



In order to add new elements to the DOM using the methods listed above, follow these steps:



1. Create a new element and store it in a variable with  `createElement`

   ```js
   let newDiv = document.createElement("div"); 
   ```

   <br>

2. Add text to the new node (if desired)

   1. Add the text content to the new element with `innerHTML` 

    ```js
    newDiv.innerHTML = 'A brand new div';
    ```

    <br>

   2. Alternatively, create a new independent text node with `createTextNode` and then add it as a child of the element created in step 1.

   ```js
let newText = document.createTextNode('A brand new div');
   newDiv.appendChild(newText);
   ```
   
   <br>
   
   

3. Get a reference the node to receive the new element as it's last child. To position the new node amongst other siblings, a reference to a sibling is also necessary.

   <br>

4. Append the new node to the selected reference element with:

   1. `appendChild` if the new content should go as the last child

      ```js
      // Option 1: add as the last child of existingDiv
      
      let existingDiv = document.getElementById("tips");
      existingDiv.appendChild(newDiv);
      ```

      

   2. Alternatively, select a middle sibling node and use `insertBefore` to insert in the middle of the parent

      ```js
      // Option 2: add between siblings.
      
      let existingDiv = document.getElementById('tips');
      const heroSection = document.getElementById('hero');
      heroSection.insertAfter(newDiv, existingDiv)
      ```



<br>



<iframe height="330" style="width: 100%;" scrolling="no" title="wk11 - creating_elements -ex8" src="https://codepen.io/maujac/embed/abvwjBX?height=330&theme-id=dark&default-tab=js" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/abvwjBX'>wk11 - creating_elements -ex8</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>



<br>

## querySelector & querySelectorAll

In addition to selection elements by **Id** name, **Class** name or element **Type**, it is also possible to use CSS-selector syntax to specify element in JavaScript.



> Using the syntax of CSS-Selectors, it is possible to select DOM elements in JavaScript using `querySelector` and `querySelectorAll`



<br>

### querySelector Syntax

```javascript
element = document.querySelector(selectors);
```



<br>The method `querySelector()` returns the first [`Element`](https://developer.mozilla.org/en-US/docs/Web/API/Element) within the document that matches the specified selector, or group of selectors.

If no matches are found, `null` is returned.

<br>

In the example below, the first element in the document with the class "`myclass`" is returned:

```javascript
const el = document.querySelector(".myclass");
```

<br>



 <iframe height="265" style="width: 100%;" scrolling="no" title="wk13 - DOM_pt2 - querySelect - ex3" src="https://codepen.io/maujac/embed/zYvRgML?height=265&theme-id=dark&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/zYvRgML'>wk13 - DOM_pt2 - querySelect - ex3</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>



<br>

### querySelectorAll Syntax

```javascript
elementList = document.querySelectorAll(selectors);
```



<br>The method  `querySelectorAll()` returns a static (not live) [`NodeList`](https://developer.mozilla.org/en-US/docs/Web/API/NodeList) representing a list of the document's elements that match the specified group of selectors.

The returned `NodeList` can be manipulated like a regular Array object.

<br>

This example returns a list of all `div` elements with a class of either `note` or `alert`:

```javascript
const matches = document.querySelectorAll("div.note, div.alert");
```

<br>



Let's perform the same styling manipulation to Item list example used earlier:

<br>

<iframe height="265" style="width: 100%;" scrolling="no" title="wk13 - DOM_pt2 - querySelectAll - ex5" src="https://codepen.io/maujac/embed/ExVQqwL?height=265&theme-id=dark&default-tab=js" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/ExVQqwL'>wk13 - DOM_pt2 - querySelectAll - ex5</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

<br>



### querySelectAll vs getElementsBy*

The are a few important differences between 

- `getElementsBy*`  methods returns a `HTMLCollection` 
-  `querySelectAll` returns a `NodeList` 

<br>

The `HTMLCollection` object and the `NodeList` object are both **array-like objects** but they have slightly different methods available to them. For example, the `forEach()` method is only available to the `NodeList` object.



Regardless, both lists can be converted to array objects using the following syntax:

```javascript
let newArray = Array.from( array_like_obj );
```

<br>

#### Live vs Static Collections

Another important difference between `getElementsBy*`  methods and  `querySelectAll` is **how the lists that they return reflect the current state of the DOM**.



> All methods `"getElementsBy*"` return **a *live* collection**. Meaning that the collections always reflect the current state of the DOM and “auto-updates” when it changes.

In contrast...

>  `querySelectorAll` returns a *static* collection. Meaning it is a snap-shot of the DOM at the moment the method was called. The collection is like a fixed array of elements.

<br>

<iframe height="434" style="width: 100%;" scrolling="no" title="wk13 - DOM_pt2 - live_vs_static_collections_1 - ex6" src="https://codepen.io/maujac/embed/XWmEjpe?height=434&theme-id=dark&default-tab=html,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/XWmEjpe'>wk13 - DOM_pt2 - live_vs_static_collections_1 - ex6</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>



<br>

We'll use the exact same script, however, this time using `querySelectAll`:

<br>

<iframe height="434" style="width: 100%;" scrolling="no" title="wk13 - DOM_pt2 - live_vs_static_collections_2 - ex7" src="https://codepen.io/maujac/embed/NWGYRjG?height=434&theme-id=dark&default-tab=html,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/NWGYRjG'>wk13 - DOM_pt2 - live_vs_static_collections_2 - ex7</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>



<br>



The importance of having a live collection vs a static collection depends only how you are coding your application. **One is not inherently better than the other.**

<br>



## Attribute selectors

To refresh our memories:

<br>

> **Attribute selectors** select elements based on an attribute or attribute value of an HTML element.



<br>

<iframe height="255" style="width: 100%;" scrolling="no" title="wk13 - DOM pt2 - attribute selectors - ex2" src="https://codepen.io/maujac/embed/yLYPvMd?height=255&theme-id=dark&default-tab=css,result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/yLYPvMd'>wk13 - DOM pt2 - attribute selectors - ex2</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>




<br>

Since `querySelect` and `querySelectAll` use the name syntax notation as CSS selectors, you can also use **attribute selectors** as your query criteria.

<br>

>  A common application of `querySelect` with **attribute selectors** is when accessing a specific `<input>`  item from a `<form>` .
>
>  Forms normally have multiple `<input>` elements but their `type = `  attributes are different

<br>

In the example below we are gaining access to the number input by using `querySelector`:

<br>

<iframe height="265" style="width: 100%;" scrolling="no" title="wk13 - DOM pt2 - querySelect_form_type - ex3" src="https://codepen.io/maujac/embed/LYpOQOy?height=265&theme-id=light&default-tab=css,result" frameborder="no" allowtransparency="true" allowfullscreen="true" loading="lazy">
  See the Pen <a href='https://codepen.io/maujac/pen/LYpOQOy'>wk13 - DOM pt2 - querySelect_form_type - ex3</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>
<br>

## Ids, Classes & Attributes

Below is a summary of methods commonly used to modify element Ids, Classes and Attributes:



### Element classes

| Property or Method                                           | Description                                                |
| ------------------------------------------------------------ | ---------------------------------------------------------- |
| [*element*.className](https://www.w3schools.com/jsref/prop_html_classname.asp) | returns a string with the class(es) name(es) of an element |
| [*element.*classList.add( "class-name" )](https://www.w3schools.com/jsref/prop_element_classlist.asp) | returns the class name(s) of an element as an array        |



### Element Id's

| Property or Method                                           | Description                                     |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [*element.*id](https://www.w3schools.com/jsref/prop_html_id.asp) | returns the value of an element's id  attribute |



### Element Attributes

| Property or Method                                           | Description                                |
| ------------------------------------------------------------ | ------------------------------------------ |
| [*element.*setAttribute( attribute-name, "value" )](https://www.w3schools.com/jsref/met_element_setattribute.asp) | adds the specified attribute to an element |

<br>

In the example below we will transform a text input into a button.

This is possible because the only thing differentiating the text input field from a button is the **value of the type attribute**.

<br>

<iframe height="292" style="width: 100%;" scrolling="no" title="wk13 - DOM_pt2 - attributes - ex1" src="https://codepen.io/maujac/embed/VwvQNRo?height=292&theme-id=dark&default-tab=html,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/VwvQNRo'>wk13 - DOM_pt2 - attributes - ex1</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>



<br>

​     

## CSS Styles in JS: getComputedStyle()

We've learned **how to change style properties** using JS with the method [*element*.style.*property = new style*](https://www.w3schools.com/js/js_htmldom_css.asp)



>  However, when used to read style properties,  *element*.style.*property* has a major limitation:
>
> - This method can only read css properties that have been added via JavaScript.



In other words, **stylesheet properties are not accessible** via  *element*.style.*property*

<br>

In the example below, when trying to read the font-size, we are returned an empty string

<iframe height="327" style="width: 100%;" scrolling="no" title="wk13 - computed styles - not working" src="https://codepen.io/maujac/embed/OJWdKyN?height=327&theme-id=dark&default-tab=js,result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/OJWdKyN'>wk13 - computed styles - not working</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

<br>

> In order to read properties added via CSS or JavaScript, use the method [`Window.getComputedStyle()`](https://developer.mozilla.org/en-US/docs/Web/API/Window/getComputedStyle)



The method  **`Window.getComputedStyle()`** returns an object containing the values of all CSS properties of an element.

<br>

Once the styling rules are retrieved with `Window.getComputedStyle()`, the individual CSS properties can be accessed using ` getPropertyValue('prop-name')`

```js
const heading = document.getElementById("title");

const styles = window.getComputedStyle(heading);
let font_size = styles.fontSize;
```

<br>

Alternatively, reading the properties of the object returned by `Window.getComputedStyle()`.

```js
const heading = document.getElementById("title");

const styles = window.getComputedStyle(heading);
let same_size = styles.getPropertyValue("font-size");
```

<br>

<iframe height="457" style="width: 100%;" scrolling="no" title="wk13 - computed styles - working" src="https://codepen.io/maujac/embed/gOgqVgr?height=457&theme-id=dark&default-tab=js,result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/gOgqVgr'>wk13 - computed styles - working</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

<br>



## textContent vs innerText

There are many ways of accessing the text content of an element node:

 

*element*.`textContent` 

​		Returns the actual text inside the html file, regardless of styling (ex. display: none).



*element.*`innerText` 

​		Only returns the text that is displayed in the window. It considers modifications done via CSS.

<br>

The example below illustrates the difference between `textContent` vs `innerText`

The `span` inside the `h1` is hidden with  `display: none`. Notice how the outputs of `innerText` and `textContent` will differ:

<br>

<iframe height="265" style="width: 100%;" scrolling="no" title="wk13 - DOM manipulation pt2 - ex1" src="https://codepen.io/maujac/embed/wvKPyvj?height=265&theme-id=light&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true" loading="lazy">
  See the Pen <a href='https://codepen.io/maujac/pen/wvKPyvj'>wk13 - DOM manipulation pt2 - ex1</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

<br>

## nodeClone( ) Method

It is possible to clone an existing node with all of it's attributes and their values

The syntax is as follows:

<br>

```javascript
node.cloneNode(deep)
```

Where deep is a optional Boolean that specifies whether all descendants of the node should be cloned.

- true - Clone the node, its attributes, *and* its descendants
- false - Default. Clone only the node and its attributes

<br>

For more information [see cloneNode( ) documentation](https://www.w3schools.com/jsref/met_node_clonenode.asp)

<br>

> Note: If you will use cloneNode( ) to build your DOM, make sure that the element you are cloning is always available and part of the DOM



<br>

## References

**Recommended video**

<iframe width="560" height="315" src="https://www.youtube.com/embed/Nx2AhrCIlXE" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



<br>

## Hands-on

### Lab 3 - Event Delegation

In the event delegation section of the notes you were shown a similar code snip.

However, the buttons lacked implementation and only outputted a string to the console.

Implement the functionality of all 2 buttons using the event delegation pattern:

- **Add item** should add a new Item at the bottom of the `<ul>` with the value specified in the `<input>`
- **Remove item** should remove the last item in the list.

<br>

> Do this exercise in your local code editor.

<br>

<iframe height="265" style="width: 100%;" scrolling="no" title="wk13 - events exercise - lab 3" src="https://codepen.io/maujac/embed/zYNVwva?height=265&theme-id=dark&default-tab=result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/zYNVwva'>wk13 - events exercise - lab 3</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>


<br>

