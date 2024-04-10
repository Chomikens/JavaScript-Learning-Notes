# JavaScript Primitive Types

JavaScript defines a set of data types known as "primitive types," which represent the simplest forms of data. 
Be mindful of JavaScript's capability for both explicit and implicit conversion between types to avoid unexpected outcomes.

Here's a comprehensive overview:

## String

Strings are used for text representation. They can be enclosed in single quotes (`'`), double quotes (`"`), or template literals (`` ` ``), the latter of which support embedding expressions and multi-line strings.

```js
const string = `Hey I'm a string type`;
const singleString = 'Hey I\'m a string type';
const doubleString = "Hey I'm a string type";
// Template literal with expression embedding
const name = 'John';
const greeting = `Hello, ${name}!
```
## Number

Used for both integer and floating-point numbers. Special values include `Infinity`, `-Infinity`, and `NaN` (Not-a-Number).
```js
const number = 2;
const float = 2.5;
const specialNumber = Infinity;
```
## Boolean

Represents logical entities. JavaScript uses `true` and `false`. It's important to know about truthy and falsy values in the context of conditionals.
```js
const booleanTypeTrue = true;
const booleanTypeFalse = false;
// Falsy values: 0, "", null, undefined, NaN, false
const falsyValue = "";
// All other values are truthy

```
## Null

Represents the intentional absence of any object value. Often used to indicate "no value" or "unknown."
```js
const nullType = null;

```
## Undefined 
Indicates that a variable has not been assigned a value. 
```js
let a;
console.log(a); // undefined
```
## Symbol

Symbols are unique and immutable values often used as the keys of object properties where uniqueness is required.
```js
const sym1 = Symbol("foo");
const sym2 = Symbol("foo");
console.log(sym1 === sym2); // false

```

## BigInt

A primitive type for integers larger than the `Number` type can safely represent.
```js
const largeNumber = BigInt(9007199254740991);

```

## Checking the Type of a Variable

Use the `typeof` operator to determine a variable's type.
```js
console.log(typeof "Hello, World!"); // "string"
console.log(typeof 42); // "number"
console.log(typeof true); // "boolean"
console.log(typeof Symbol('sym')); // "symbol"
console.log(typeof BigInt(9007199254740991)); // "bigint"
console.log(typeof undefined); // "undefined"
console.log(typeof null); // "object" (due to historical reasons)
```
