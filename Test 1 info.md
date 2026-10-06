# Test 1 \- October 14th \- 25%

* Who runs the JavaScript in the HTML page? When is it run?  

* JavaScript \- official standard name, creator, company he worked for, original purpose of JavaScript , where it got this name

* Arrays  
  * Syntax (creation and access), index  
  * Can have mixed data types  
  * Can have an array as an item in an array
  * Simple functions and properties
    * push(), pop(), length, indexOf
    * splice
  * Functions with functions as parameters (functional programming)
    * Have to be aware of what the array function:  
      * Does  
      * Returns, if anything (undefined if not)  
      * Requirements for passed in function  
        * parameters
        * does the function need to return something specific?  
    * forEach  
      * myArray.forEach( x=\> console.log( \++x); );  
      * Doesn’t return anything (undefined)  
      * Give it a function to apply to each element in the original array  
        * Doesn’t change the original array unless:  
        * the function modifies the passed in elements and the elements are objects: the objects passed by (copy of) reference are also changed in the original array that references them too.  
        * Return value of passed in function is not used anywhere  
    * map  
      * let newArray = myArray.map( function(x) { return x \+ 2; } );   
      * returns a new array of the same size as the original array  
      * Given a function to apply to each element of the original array.  
        * What that function returns, is what will appear in the new array for that element.   
          * If it returns nothing, new array will be an array of undefined values, one for each element in the original array  
        * (Doesn’t change the original array unless changes objects that are passed by (copy of) reference.)  
    * filter  
      * let over18 = numbers.filter( value =\> value \> 18);  or   let over18 = numbers.filter( value =\> {return value \> 18; });
      * returns a new array with only the elements of the original array that match the filter (function returns true for)  
      * Give it a function to apply to each element of the original array.  
        * Must return a boolean, true if the original array element should appear in the returned array, false otherwise.  
        * (Doesn’t change the original array unless changes objects that are passed by (copy of) reference).  
  
* Dynamic typing  
  * JS is dynamically typed, what does this mean?  
  
* if/else, for loops, while loops  

* &&, ||, !

* Functions  
  * pure when use all parameters and do not use global variables.
  * Syntax, create a function with 0 to many parameters  
  * Implement the function body, return something. When the function does not return anything, it returns undefined.  
  * Call the functions with appropriate arguments  
  * Declared functions \- code is not run unless the function is called.  
  * Can send more or less arguments than there are parameters.   
  
* Be able to use the alert and console.log  functions

* Objects  
  * Syntax \- properties and object functions  
  * ‘this’ keyword to use object properties in body of object’s functions  
    * Why not use the variable the object is currently stored in?  
  * Access properties on the object (retrieve value)  
  * Assign a different value on a property.  myObject.property \= newValue;  
  * Call functions on the object.  
  * The value of an object’s property can be another object, a function  
  * Accessing a property that does not exist in the object: undefined value

* ### Review \- function parameters

  * Primitives are passed into functions by value  
    * If the function changes the parameter, it is only changing its copy, not the original.  
  * Objects are passed into function by (copy of the) reference  
    * If the function changes the parameter value, it is changing the referenced object for anyone holding a reference to it.  
  
* Scoping  
  * Child scopes always see everything in parent   
  * What is hoisting?  
  * let  
    * Block scoped (any pair of brackets defines a scope that cannot be ‘seen’ by parent/sibling scopes).  
    * No hoisting  
  * const  
    * Same scoping as let  
    * Cannot reassign the variable (error)  
    * But can modify the object that is assigned to the variable.  
    * No hoisting  
  * var  
    * Function scoped only (other scopes do not limit access)  
    * Hoisting (only the declaration, not the assignment of a value)  
  
* undefined value (value of a declared variable with no value assigned to it) vs getting an error because your variable is not declared/defined (can’t see the variable or has never been declared)  

* Strict equality vs loose equality  
  * What is type coercion  
  
* “use strict”;  
  * Why? JavaScript behaviour  
  * What does it do? Makes more errors appear. Avoids inadvertent behaviour due to code errors that cause unexpected behaviour  
  * Undeclared variables, same-named parameters  
  * Need to add it to the top of the script or function  
  
* The DOM  
  * Who creates it?  
  * document object  
    * Retrieving elements from it  
      * By id  
        * What do you get back?  
        * What if there is no element with such an id?  
      * By tag name or class name  
        * What do you get back?  
        * What if there is no element with such a tag/class name?  
        * How do I get the element from the array  
    * Can walk the DOM (traverse properties for parents, siblings, children)  
  * Being able to access and change properties on elements retrieved from the DOM  
    * innerHTML, id, class  
    * style properties  
    * Changes are to the currently loaded DOM  
  * Being able to create a new element in the DOM  
    * let newElement \= document.createElement(“tagName”)  
    * myElement.appendChild( newElement )  
  * Style properties  
    * How to assign a new style property is JS: myElement.style.theCSSProperty \= newCSSPropertyValue;  
    * CSS styles are not pre-calculated in DOM objects  
      * To read properties specified in CSS scripts:  
        * let stylesObject \= window.getComputedStyle( myElement ) returns an object with all the CSS properties for that element  
        * You can then retrieve CSS properties from that objects:  
          let font\_size \= stylesObject.fontSize;  
      *   
  * InnerHTML vs InnerText  
  
* What is jQuery  
  * A library of functions  
  * Written in JavaScript  
  * \$()  
  * How to use it  
    * Provide it yourself (download)  
    * Specify a ContentDeliveryNetwork script tag to get jQuery  
      * Why is this better? Browser will often have a copy retrieved for another page.  
  * CSS-style selectors:  
    * \$(“tag“)  
    * \$(“.class”)  
    * \$(“\#id”)  
  
* JavaScript css-style selector equivalents (catching up to jQuery)  
  * querySelector returns first matching element  
  * querySelectorAll  
  
* HTML Events   
  * Set up an event listener where you specify:  
    * The HTML element that you are interested in the event for.  
    * The event you are interested in knowing occurred.  
    * The function to run when the event occurs on the element. You do not run it when setting up the event listener \- you pass the function without calling it.  
  * Can add an event listener in JavaScript  
    * document.getElementId(“theId”).addEventListener( “event”, functionToRun);  
  
* HTML Forms  
  * Are HTML elements (can have an id, etc)  
  * action attribute =\> url to go to on submit, default (action attribute is not specified) is the page itself (reloads the same page, but from scratch)  
  * method attribute =\> GET or POST \- understand the difference  
  * Should you validate using HTML attributes when available for the validation you need?  
  * Why is it good to validate a form using JavaScript in the browser?  
  * Submit event should be blocked on the form and why?  
    * What if multiple ways to submit?  
  * event.preventDefault()  
    * Browser passes the event object when it calls listener functions  
    * Can call event.preventDefault() to stop the default behaviour of the submit (going to the server)  
  
* Event bubbling  vs capturing, target

  * Different phases
* target vs currentTarget properties  
  * (You do not need to know about stopPropagation)  

* Arrow notation for functions

  * Just a different, more concise, syntax.

  * Functions can be passed around (event listener)

  * How to call a function assigned to a variable.

  * General syntax:  (parameters)  **=\>**    {  body  }  
  * No parameters: () \=\> {body}  
  * One return statement as the body (no curly braces):   
      (parameters)  =\> statement\_to\_return;  
    
    * ( name ) =\> name;      
      * same as: function(name) {**return** name;}  
      * As opposed to ( name ) =\>{ name }; which is the same as: function(name){name;} //does nothing with name  
  * Multiple parameters: (param1, param2) =\> {body}     
    * or could be no curly braces if just one return statement:
  
       (param1, param2) =\> return\_what\_this\_resolves\_to;
  
  * Only one parameter: param1 =\> {body} or  param1 =\> statementToReturn;   
  * Be able to convert arrow function to regular syntax equivalent and vice versa.  
  
* Making sure the DOM is ready
  
  * Know why it is important and and how to use
    * $(document).ready()
    * DOMContentLoaded event
  
* Compiled vs scripting language  

  * Run with pre-compiled machine-readable code vs run on the fly.  
    * C\# vs JavaScript  
    * If there are errors in your code when would you see them

  

    

