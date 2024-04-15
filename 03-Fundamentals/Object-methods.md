## Object: values and entries 

#### Example to work with 

```js
const exampleObject = {
    userName0: "Name",
    userName1: "Name1",
    userName2: "Name2",
}
```

### Before ES 8 - Object keys 
The `Object.keys()` method returns an array containing the names of all enumerable properties of an object.
`Returns`: An array of strings representing the keys of the provided object.

#### Syntax
```js
Object.keys(obj)
```

#### Example 
```js
Object.keys(exampleObject).forEach(key => {
    console.log(`This is a key: ${key} so we use brackets notation to get values:`, exampleObject[key])
})
```


### Object values 
The `Object.values()` method returns an array containing the values of all enumerable properties of an object.
`Returns:` An array containing the values of the provided object.


```js
Object.values(exampleObject).forEach(value => console.log("Just use value:" ,value))
```

### Object entries 
The `Object.entries()` method returns an array containing arrays of key-value pairs of all enumerable properties of an object.
`Returns:` An array of arrays, where each inner array contains a key-value pair.


### Example 
```js
Object.entries(exampleObject) 

/* Output: [
    [ 'userName0', 'Name' ]
    [ 'userName1', 'Name1' ]
    [ 'userName2', 'Name2' ]
 ] 
 */ 

const namesOfUsers = Object.entries(exampleObject).map(el => return el[1])

```

## Creating Objects from Entries

In JavaScript, the `Object.fromEntries()` method is used to transform a list of key-value pairs into an object. This can be particularly useful when you have an array of entries and you want to convert it into an object.

## Syntax

```js
const entries = [
    ["name", "Dominik"],
    ["nickname", "kotorozec"],
    ["age", 13]
];

const objFrom = Object.fromEntries(entries);

console.log(objFrom); // Output: { name: "Dominik", nickname: "kotorozec", age: 13 }
```


## Optional Chaining Operator (`?.`)

The Optional Chaining Operator (`?.`) allows you to read the value of a property located deep within a chain of connected objects without having to check that each reference in the chain is valid. The `?.` operator is like the `.`, except that instead of causing an error if a reference is nullish (`null` or `undefined`), the expression short-circuits with a return value of `undefined`.

### Syntax

```javascript
obj?.prop       // Accessing a property
obj?.[expr]     // Accessing a property through an expression
func?.(args)    // Calling a function if it exists` 
```
### Example

```javascript

const person = {
  name: 'John',
  address: {
    street: 'Main St',
    city: 'Anywhere'
  }
};

const streetName = person.address?.street;
console.log(streetName); // "Main St"` 
```

If `address` was not part of `person`, `person.address?.street` would return `undefined` instead of throwing an error.

### Use Cases

-   Safely accessing nested object properties
-   Optional function calls
-   Conditional property access in arrays and objects

## Nullish Coalescing Operator (`??`)
The Nullish Coalescing Operator (`??`) is a logical operator that returns its right-hand side operand when its left-hand side operand is `null` or `undefined`, and otherwise returns its left-hand side operand. This is useful for assigning default values.


### Syntax

```javascript
leftExpr ?? rightExpr` 
```
### Example

```javascript
const nullValue = null;
const undefinedValue = undefined;
const text = ''; // Empty string is considered a valid value
const defaultValue = 'Default';

console.log(nullValue ?? defaultValue); // "Default"
console.log(undefinedValue ?? defaultValue); // "Default"
console.log(text ?? defaultValue); // ""` 
```
### Use Cases

-   Setting default values for variables that might be `null` or `undefined`
-   Working with potentially missing data without resorting to OR `||` operator which considers any falsy value (e.g., `0`, `''`, `false`) as default trigger


## Combining Optional Chaining (`?.`) and Nullish Coalescing (`??`)

When working with deeply nested objects, there might be instances where not only the existence of nested properties is uncertain, but you also want to provide a default value in case the final target or any part of the chain is `null` or `undefined`. Combining `?.` and `??` allows you to safely navigate through the objects and set defaults efficiently.

### Syntax and Use

The general approach is to first use optional chaining to safely access properties or call functions within an object structure, and then use nullish coalescing to provide a default value if the result of the optional chaining is `null` or `undefined`.

```js
const result = obj?.prop?.nestedProp ?? defaultValue;
```

### Detailed Example

Consider an object `user` that may or may not have an `address` property, and even if it does, the `zip` code may not be set. You want to safely access `user.address.zip` and provide a default value if it's not found.

```js
const user = {
  name: 'Jane Doe',
  address: {
    street: '123 Main St',
    // Note: 'zip' is intentionally omitted
  }
};

const zipCode = user.address?.zip ?? '00000'; // Provides a default zip code
console.log(zipCode); // "00000"
```

In this example, `user.address?.zip` attempts to access `zip` within `address`. If `address` is `undefined` or `zip` is not present, the expression will result in `undefined`, triggering the nullish coalescing operator to return the default value `'00000'`.

## Benefits

-   **Safety and Readability:** This pattern allows for safe access and manipulation of object properties without verbose and complex error handling.
-   **Simplicity:** It simplifies the code by reducing the need for multiple conditional statements to check for the existence of each property in the chain.
-   **Default Values:** It provides a straightforward way to define default values for potentially undefined properties, making the code more resilient and predictable.
