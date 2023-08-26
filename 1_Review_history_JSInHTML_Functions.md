

# Intro to JavaScript

Beyond HTML and CSS, JavaScript is a programming language that is used to bring your website to life



## Origins

JavaScript was created during the browser wars in the mid 90's. In an ambitious maneuver to outperform Microsoft's Internet Explorer (IE), the team behind Netscape Navigator commissioned Brendan Eich to create a powerful, dynamic, language that could run in the browser.  In 1995, Eich created JavaScript in 10 days to add dynamic elements and interactivity to websites.

He first named the language Mocha, then LiveScript and then JavaScript (in order to benefit from the growing popularity of Java).

Microsoft reverse engineered Netscape's JavaScript interpreter and dominated the market-share by including IE with Windows.

Netscape had to cease its operations. As a last move, they open sourced JavaScript. Brendan and others behind Netscape Navigator went on to co-found the Mozilla foundation, the creators of the Firefox browser.



## Browser

As JavaScript evolved, a need was seen to create a standard to make sure that web pages could work across different browsers. 

ECMA, a standards organization, developed ECMAScript as the standard for scripting languages to be run in the browser. Although JavaScript it is the most prominent implementation of the standard, it is versions of the standard that are officially supported. Versions use ES as a prefix:  ES5, ES7, ES2022.

It is the browser that loads HTML pages and builds up the DOM. It runs JavaScript code as it encounters it when it runs through the page it is loading.



## Adding JavaScript in HTML

Where can we place JavaScript code in the HTML document?



### In-line

Attached to a window event such as `onclick`

```html
<button onclick="alert('Inline JavaScript!')">
    Click me for JS
<button>
```



<br>

### Internal

Inside the `<script>` tag.

The `<script>` tag is normally **placed just before the end of the `<body>`.** 



```html
<body>
    <h1>Welcome to our site!</h1>
    
... rest of the body

    <script>
        console.log('JavaScript inside the HTML document!');
    </script>
</body>
```

Technically, the `<script>`tag can be placed anywhere but its position matters. 

Remember that the html document is parsed (processed) from top to bottom.

- This means that the `<script>` tag will be executed as soon as the browser sees it in the html file.

  >If your JS script is manipulating DOM elements, make sure the browser has already added those elements to the DOM by the time your script is run.


<br>

## Variable Types & Dynamic Typing

JavaScript is a dynamic typed language.

This means that you don't specify what type of data a variable holds, **the JS engine figures it out when the code is run**.



Because of this, the same variable can hold different types of values inside the same execution environment.

<br>

In contrast, in static typed languages such as Java or C#, variable types must declared and respected.

```c#
bool isNew = "hello!"; // gives an error in C#
```



However, in JavaScript the sequence of lines below are valid:

```javascript
let isNew = true;			// holding a boolean
isNew = 1;					// now a number
isNew = "It's all good";	// now a string
```

<br>



## For-loops

There are several ways of using for-loops in Js. We will focus on two approaches:

- Classic `for( ) ` loop
- The `for...of` loop

<br>

### Classic for-loop

Works similarly as other languages:

<iframe height="265" style="width: 100%;" scrolling="no" title="wk12  - classic for-loop - ex11" src="https://codepen.io/maujac/embed/zYvzjjB?height=265&theme-id=dark&default-tab=js" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/zYvzjjB'>wk12  - classic for-loop - ex11</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>



<br>

### for...of

The `for...of` loop provides a method for directly accessing the items in the list (as opposed to using the array index).

<br>

<iframe height="228" style="width: 100%;" scrolling="no" title="wk12  - for-each - ex13" src="https://codepen.io/maujac/embed/XWmgYrp?height=228&theme-id=dark&default-tab=js" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/XWmgYrp'>wk12  - for-each - ex13</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>



<br>

### While-loops

While-loops also work similarly as other languages:

<iframe height="258" style="width: 100%;" scrolling="no" title="wk12  - while_loop - ex14" src="https://codepen.io/maujac/embed/KKdqedd?height=258&theme-id=dark&default-tab=js" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/KKdqedd'>wk12  - while_loop - ex14</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>


<br>

If you prefer `do...while` loops, they also exist in JavaScript. See [the do...while documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/do...while) for more info.

<br>

## If Statements

If statements work similarly to other languages

<iframe height="302" style="width: 100%;" scrolling="no" title="wk12  - if statements - ex10" src="https://codepen.io/maujac/embed/oNjwdoW?height=302&theme-id=dark&default-tab=js" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/oNjwdoW'>wk12  - if statements - ex10</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>



<br>

> Careful! **The equality operator "==" behaves differently** than most languages.
>
> This is a design decision that [Brendan Eich regrets](https://thenewstack.io/brendan-eich-on-creating-javascript-in-10-days-and-what-hed-do-differently-today/). We will discuss this in a lecture next week.

<br>



## Primitive Data Types

Primitive types are the most basic variable types in JavaScript.

A primitive type is a type of data that holds a single value. In other words, variables that are not objects (more on objects later).

<br>

| Type                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [`undefined`](https://developer.mozilla.org/en-US/docs/Glossary/undefined) | Absence of a value. The use of `undefined` should be reserved for the JavaScript engine. |
| [`null`](https://developer.mozilla.org/en-US/docs/Glossary/Null) | Lack of existence. Can be assigned to variables by developers. |
| [`boolean`](https://developer.mozilla.org/en-US/docs/Glossary/Boolean) | `true` or `false`                                            |
| [`number`](https://developer.mozilla.org/en-US/docs/Glossary/Number) | The only number type available. It's a floating point number (some decimals are always attached) |
| [`string`](https://developer.mozilla.org/en-US/docs/Glossary/String) | A sequence of characters. Either ' ' or " " can be used. Most other languages consider strings as an array of characters, but in JavaScript it is a primitive type. |
| [`BigInt`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/BigInt) | Similar to numbers but can store much larger numbers. *Not covered in this course.* |
| [`symbol`](https://developer.mozilla.org/en-US/docs/Glossary/Symbol) | New in ES6. *Not covered in this course.*                    |



<br>

See [JavaScript data types and data structures page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures) by MDN web docs for more info on primitive types.

<br>

### The undefined keyword.

Note that **`undefined`** is a special value in JavaScript and it means slightly different things when dealing with variables, methods or functions:

- A **variable** that has not been assigned a value holds the value `undefined`. 
- A **function** returns `undefined` if a value was not [`returned`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/return).

<br>

Try the following code to see what is displayed in the *Console* tab of the *Dev Tools*

<br>

**Undefined with variables:**

```js
let a;				// Variable declared but nothing assigned to it
console.log(a);		// undefined
```

<br>

**Undefined with functions:**

```js
// Declare two functions
function sayHi(name){
  console.log("Hi there ", name);		// Return nothing but print to console
}

function hiMessage(name){
  return ("Hello my friend ", name);	// Returns a string
}

// Now run them
console.log( sayHi("Larry") );			// Logs string to console but then logs undefined 
                                        // because that is what is returned

console.log( hiMessage("Meghrig") );	// Logs the returned string to console
```



<br>

## Functions

### Function Declarations

Function declarations in JavaScript work similarly to other languages:

- Start the declaration with the keyword `function`
- Add a function **name**
- Optionally return something with the keyword `return`
- To invoke it use its name followed by parenthesis **( )**

<br>



<iframe height="331" style="width: 100%;" scrolling="no" title="wk12  - function declarations -ex7" src="https://codepen.io/maujac/embed/oNjwqyX?height=331&theme-id=dark&default-tab=js" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/oNjwqyX'>wk12  - function declarations -ex7</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>



<br>

Major differences from other languages:

<br>

- It is not necessary to specify the data type returned
-  JavaScript allows you to pass in any number of arguments to a function. 
  - If you pass less arguments than there are parameters in the function definition, the remaining parameters will hold the value undefined.  **There will not be an error**.
  - If you pass more, the extra arguments will be ignored (although technically there is a way to get the args array and see the extra ones too). If parameters are expected but not provided 

- This flexibility can lead to bugs as a developer might not have passed in a different number of arguments intentionally, for example.

<br>

<iframe height="323" style="width: 100%;" scrolling="no" title="wk12  - argumentless function -ex8" src="https://codepen.io/maujac/embed/ExVXErq?height=323&theme-id=dark&default-tab=js" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/ExVXErq'>wk12  - argumentless function -ex8</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>
<br>



## References

#### JavaScript Reference Pages

1. [**JavaScript reference**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference) by MDN web docs.

   

   

<br>

## Hands-on 

### Exercises (answers at the end of this page)

1. What will be logged to console when a page is loaded with this code in a script tag?

   ```javascript
   function test()
   {
     console.log( "Hi" );
   }
   ```

   <br>

2. What will be logged to console when a page is loaded with this code in a script tag?

   ```javascript
   function test()
   {
       console.log( "Hi" );
   }
   
   console.log ( "Hola" );
   console.log ( test() );
   
   
   ```

   <br>

<br>



### Lab - ECMAScript latest version

When was the latest version of JavaScript released? What is the official name of the version of the standard?



### Lab - Seat numbers

Theater seats often display a row and seat number to help theatergoers find their seats. 

There are 6 rows (0 to 5) and 20 seats (1 to 20) in each row.

In a function, write a nested for loop to print to **console** all of the different seat combinations in the theater. 

Example console output:

0-1 

0-2 

... 

5-17 

5-18 

5-20



To concatenate strings use the '+' operator:

```javascript
console.log(  myVariable + " " + myOtherVariable );
```





### Answers - Exercises 

1. nothing, the function is never called.

2. first Hola will be logged. Then Hi will be logged from the execution of the test function. Then the console will show undefined, when it logs the return of the call to test. 

   Hola

   Hi

   undefined

   Remember, the lines of code in test will only be run when they are executed. Even if the test function is defined before the console.log("Hola"), console.log("Hola") is the first line of executed code. console.log("Hi") will only be run after, when test() is executed on the next line.
