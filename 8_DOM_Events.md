This section is based on the page [Introduction to browser events](https://javascript.info/introduction-browser-events) by javascript.info



# DOM Events

An **event** is a signal that something has happened. All DOM nodes generate such signals.



## Event Examples

Here’s a list of some DOM events:



### Mouse events:

| Event name               | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| `click`                  | When the mouse clicks on an element.                         |
| `contextmenu`            | When the mouse right-clicks on an element.                   |
| `mouseover` / `mouseout` | When the mouse cursor comes over / leaves an element.        |
| `mousedown` / `mouseup`  | When the mouse button is pressed / released over an element. |
| `mousemove`              | When the mouse is moved.                                     |



### Form element events:

| Event name | Description                                                  |
| ---------- | ------------------------------------------------------------ |
| `submit`   | When the visitor submits a `<form>`.                         |
| `focus`    | When the visitor focuses on an element, e.g. on an `<input>`. |
| `blur`     | Fires when an element loses focus                            |



### Keyboard events:

| Event name | Description                        |
| ---------- | ---------------------------------- |
| `keydown`  | When the visitor presses the key.  |
| `keyup`    | When the visitor releases the key. |



### Document & other events:

| Event name         | Description                                                |
| ------------------ | ---------------------------------------------------------- |
| `DOMContentLoaded` | When the HTML is loaded and processed, DOM is fully built. |
| `load`             | The event occurs when an object has loaded                 |



<br>

> For a complete list of events see:
>
> - [**HTML DOM Events page**](https://www.w3schools.com/jsref/dom_obj_event.asp) from W3Schools for a **summary list**.
> - [**Event reference page**](https://developer.mozilla.org/en-US/docs/Web/Events) from MDN Web Docs for a **full list of all event organized by types**

<br>

**Events are constantly being fired** in the browser,  it's only a matter **how we handle them**.

<br>

## Event Handlers

> To ktrigger an action when a specific event happens, we can assign an **event handler** to the event.
>
> **An event handler is a JavaScript function.**

<br>

There are three ways of assigning an event handler to an event:

- As a HTML **in-line attribute**;
- As a **DOM property** on a element;
- Using an **event listener** - the proffered method in this course 🏆



### Handlers as HTML Attributes

A handler can be set in HTML with an attribute named  `on<event>`  (*without the angled brackets*).

This is the **simplest** method but **has many limitations**.

For example, to assign a handler to the  `click` event for a `<button>` element, we can use the  `onclick` attribute:



<iframe height="265" style="width: 100%;" scrolling="no" title="wk12 - Lab 2 - solution" src="https://codepen.io/maujac/embed/BaoJKRx?height=265&theme-id=dark&default-tab=html" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/BaoJKRx'>wk12 - Lab 2 - solution</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>




<br>

Note that we could have written an complete JavaScript command inside the HTML event-handler attribute:

<iframe height="166" style="width: 100%;" scrolling="no" title="wk13 - events - ex1" src="https://codepen.io/maujac/embed/OJyzNww?height=166&theme-id=dark&default-tab=html" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/OJyzNww'>wk13 - events - ex1</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>



<br>

!> This method is error-prone for long JS expressions and is not recommended. Keep your structure (HTML) and your functionality (JavaScript) separated.

<br>

### Handlers as DOM Properties

We can assign an event handler to an HTML element using the DOM property `on<event>`  syntax.

<br>

*Inside code.js:*

```js
element.onclick = myFunction	// a function defined elsewhere in this file
```

<br>

The example below uses the `mouseover` event:

<br>

<iframe height="279" style="width: 100%;" scrolling="no" title="wk13 - events - ex2" src="https://codepen.io/maujac/embed/GRpyqGa?height=279&theme-id=dark&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/GRpyqGa'>wk13 - events - ex2</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>




<br>

### Syntax differences for event handlers

There is an important syntax difference between the two methods listed above:

- Handlers assigned as **HTML attributes** **take bracket**s `( )`  in the function call:

  ```javascript
  <div id="zone" onclick="activate()">
  ```

- Handlers assigned as **Object properties** **do not take brackets** `( )` in the function call:

  ```javascript
  // right
  zone.onmouseover = activate;
  
  // wrong
  zone.onmouseover = activate();
  ```



If we add parentheses, `activate()` becomes a function call, meaning that is will be executed at that line.

<br>

The last line actually puts the *result* of the function execution, which is `undefined` (since the function returns nothing), and assigns it to the `onmouseover` event.

<br>

### Handler Limitations: HTML attributes & DOM properties

> Event handlers assigned as HTML attributes or as DOM properties have **one major limitation**:
>
> **Events can only be handled by a single event handler**

<br>

### Handlers via Event Listeners 🏆

<br>

If more than one handler is assigned to the same element, only the last assignment will be effective:

```javascript
input.onclick = myHandler;
// ...
input.onclick = myOtherHandler // replaces the previous handler
```



<br>

> The method **addEventListener( )** is used to assign one or more handlers to a single event.
>
> **This is the recommended method for adding event handlers to events** 🏆

<br>

It uses the following syntax:

```javascript
element.addEventListener("event", handler, [options]);
```



- **event** - name of event (e.g. `"click"` or  `"mouseover"`);
  - see [HTML DOM Events page](https://www.w3schools.com/jsref/dom_obj_event.asp) from W3Schools for a **summary list**.
- **handler** - function that will handle the event;
- **options** - optional object with the properties `once`, `capture`, or `passive`.
  - see [docs for optional object](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)



<br>

<iframe height="265" style="width: 100%;" scrolling="no" title="wk13 - events - addEventListener - ex3" src="https://codepen.io/maujac/embed/BaoJLOR?height=265&theme-id=dark&default-tab=js" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/BaoJLOR'>wk13 - events - addEventListener - ex3</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>



<br>

> An event handler function is also a **callback function**.
>
> The idea is that when an element observes the specified event, it's handler function will be **"called back".**



<br>

### Removing event listeners

To remove an event handler from an element, use the method `removeEventListener`, with the same syntax as `addEventHandler`:

```javas
element.removeEventListener(event, handler, [options]);
```



<br>

## Event Object

As soon as an event happens, the browser automatically creates an **event object** and stores details about the event as **object properties**.



Some properties of the event object:

- **event.type** - type of event (e.g. `"click"` ,  `"mouseover"` or  `"keydown"` );
- **event.target** - element where event was **originally triggered**;
- **event.currentTarget** - element who's event handler function is currently handling the event (see event bubbling for contrast with `event.target` );
- **event.clientX / event.clientY** - window-relative coordinates of the cursor, for **mouse events only**.
- **event.key** - key value of the key represented by the event, for **keyboard events only**.



<br>

There are many more properties, some are generic to all events, others are specific to certain event types.



For example:

- The `"keydown"` event has a `key` property which stores the key value of the key pressed. A `"click"`  event does not have the same property. 
- In turn, the  `"click"` event has the `"clientY"`  property, which returns the vertical coordinate of the mouse pointer, relative to the current window.  A `"keydown"` event returns a meaningless value for the same property.

<br>

### Event Types

Below is a list of common event object types:

| Event Object                                                 | Description                                    |
| ------------------------------------------------------------ | ---------------------------------------------- |
| [AnimationEvent](https://www.w3schools.com/jsref/obj_animationevent.asp) | For CSS animations                             |
| [ClipboardEvent](https://www.w3schools.com/jsref/obj_clipboardevent.asp) | For modification of the clipboard              |
| [DragEvent](https://www.w3schools.com/jsref/obj_dragevent.asp) | For drag and drop interaction                  |
| [FocusEvent](https://www.w3schools.com/jsref/obj_focusevent.asp) | For focus-related events                       |
| [InputEvent](https://www.w3schools.com/jsref/obj_inputevent.asp) | For user input                                 |
| [KeyboardEvent](https://www.w3schools.com/jsref/obj_keyboardevent.asp) | For keyboard interaction                       |
| [MouseEvent](https://www.w3schools.com/jsref/obj_mouseevent.asp) | For mouse interaction                          |
| [PageTransitionEvent](https://www.w3schools.com/jsref/obj_pagetransitionevent.asp) | For navigating to, and away from, web pages    |
| [ProgressEvent](https://www.w3schools.com/jsref/obj_progressevent.asp) | For the progress of loading external resources |
| [StorageEvent](https://www.w3schools.com/jsref/obj_storageevent.asp) | For changes in the window's storage area.      |
| [TouchEvent](https://www.w3schools.com/jsref/obj_touchevent.asp) | For touch interaction                          |
| [TransitionEvent](https://www.w3schools.com/jsref/obj_transitionevent.asp) | For CSS transitions                            |
| [UiEvent](https://www.w3schools.com/jsref/obj_uievent.asp)   | For user interface interaction                 |
| [WheelEvent](https://www.w3schools.com/jsref/obj_wheelevent.asp) | For mousewheel interaction                     |



<br>

See the [Event API documentation](https://developer.mozilla.org/en-US/docs/Web/API/Event) for details on event properties and types.

- For an list of generic event properties (common to all event types), [see the "Properties" section](https://developer.mozilla.org/en-US/docs/Web/API/Event#Properties).

- For an extensive list of all available event types see the ["Interfaces based on Event" section](https://developer.mozilla.org/en-US/docs/Web/API/Event#Introduction).



<br>
