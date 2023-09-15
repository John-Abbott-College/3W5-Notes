# JavaScript: Some weird parts

JavaScript can seem a little counter intuitive at first.

<br>

## Primitive wrapper objects

You can think of primitive data types as infant variables that can't do anything other than store a single value inside.

**Primitives don't have methods or properties.**

<br>

There are certain manipulations that are very common to person on primitive types. 

For example:

- transforming a `number` into a `string` or vice-versa,
- splitting a long `string` into smaller pieces,
- determining if a `string ` contains an occurrence of another `string`

<br>

> For this reason, there are **wrapper objects** that give primitives special powers. 

<br>

Except for `null` and `undefined`, all primitive types have object equivalents that wrap around the them (notice how they start in upper case) :

- [`String`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) for the string primitive.
- [`Number`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number) for the number primitive.
- [`BigInt`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/BigInt) for the number primitive.
- [`Boolean`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean) for the boolean primitive.

<br>

For example, in the code below, we create a string primitive, however, we call the method `toUpperCase()` on it.

<br>

```js
const sentence = 'The quick brown fox jumps over the lazy dog.';
console.log( sentence.toUpperCase() );

// Output: "THE QUICK BROWN FOX JUMPS OVER THE LAZY DOG."
```

<br>

The method `toUpperCase()` works because "behind the scenes", JavaScript used the `String` wrapper object to temporarily give the `string` primitive super powers.

<br>

**Here is how primitive wrapper objects work:**

<br>

1. Primitives types are still primitive and can only store a single value (no methods of properties).
2. The language allows methods and properties to be called on strings, numbers, booleans and symbols.
3. In order for that to work, a special “object wrapper” that provides the extra functionality is created, used, and then is destroyed.

<br>



> For all practical purposes, consider the methods and properties associated with the wrapper objects to belong to the primitive types.



<br>

##  Operators

Like most languages, JavaScript has several types of operators. We will focus on the following:

- Arithmetic Operators
- Assignment Operators
- Comparison Operators
- Logical Operators

<br>

Below are commonly used operators. See the [**JavaScript Operators page**](https://www.w3schools.com/js/js_operators.asp) for the full reference.

<br>

### Arithmetic Operators

| Operator | Description                                                  |
| -------- | ------------------------------------------------------------ |
| +        | Addition                                                     |
| -        | Subtraction                                                  |
| *        | Multiplication                                               |
| **       | Exponentiation ([ES2016](https://www.w3schools.com/js/js_es6.asp)) |
| /        | Division                                                     |
| %        | Modulus (Division Remainder)                                 |
| ++       | Increment                                                    |
| --       | Decrement                                                    |

<br>

### Assignment Operators

| Operator | Example | Same As   |
| -------- | ------- | --------- |
| =        | x = y   | x = y     |
| +=       | x += y  | x = x + y |
| -=       | x -= y  | x = x - y |
| /=       | x /= y  | x = x / y |



<br>

### Comparison Operators

| Operator | Description                                  |
| -------- | -------------------------------------------- |
| ==       | equal to                                     |
| ===      | strict equality (equal value and equal type) |
| !=       | not equal                                    |
| !==      | strictly not equal value or not equal type   |
| >        | greater than                                 |
| <        | less than                                    |
| >=       | greater than or equal to                     |
| <=       | less than or equal to                        |
| ?        | ternary operator                             |

<br>

### Logical Operators

| Operator | Description |
| -------- | ----------- |
| &&       | logical and |
| \|\|     | logical or  |
| !        | logical not |

<br>

### Explicit coercion

There are mechanisms we can use to *explicitly* cause values to be coerced, such as using the built-in type “wrapper” objects.

```javascript
String(42); // "42"
Boolean(42); // true
Number(true); // 1
```

<br>

For more information on coercion, see [JavaScript type coercion explained](https://www.freecodecamp.org/news/js-type-coercion-explained-27ba3d9a2839/) by freeCodeCamp or [JavaScript Type Conversion](https://www.w3schools.com/js/js_type_conversion.asp) by W3C Schools.

<br>

## References



### JavaScript Reference Documentation Pages

[**JavaScript reference**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference) by MDN web docs.

<br>

### WTF JavaScript (humour & quirks)

A good place to celebrate JavaScript quirks is [wtfjs.com](https://wtfjs.com/), where you will find a list of unexpected behaviors.

<br>



