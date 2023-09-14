# DOM Manipulation

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

   

3. Get a reference the node to receive the new element as its last child. To position the new node amongst other siblings, a reference to a sibling is also necessary.

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

