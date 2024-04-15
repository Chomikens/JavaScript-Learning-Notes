
# JavaScript Logic

## JavaScript Comparisons

-   **Strict Equality (`===`)**: Checks if both value and type are the same.
    
```js
const firstNum = 5;
const secondNum = "5";
console.log(firstNum === secondNum); // false` 
  ```  
-   **Loose Equality (`==`)**: Checks if values are equal after type coercion.
    
```js
console.log(firstNum == secondNum); // true` 
```

-   **Strict Inequality (`!==`)**: Checks if value and type are not equal.
```js
console.log(firstNum !== secondNum); // true` 
```
    
-   **Greater Than (`>`), Less Than (`<`), Greater Than or Equal (`>=`), Less Than or Equal (`<=`)**: Comparison operators that focus only on values.
    

## Conditionals

### If Statement

Syntax:

```js

if (condition) {
    // do something
} else {
    // do something else
}
```
Example:

```js

const birthMonth = 12;
if (birthMonth === 12) {
    console.log('You get two presents');
} else {
    console.log('Enjoy your day!');
} 
```
## Switch Statement

How it works:

```js

function moveCommand(direction) {
    let whatHappens;
    switch(direction) {
        case "forward":
            whatHappens = "You encounter a monster";
            break;
        case "left":
            whatHappens = "You find a treasure chest";
            break;
        case "right":
            whatHappens = "You fall into a pit";
            break;
        case "backward":
            whatHappens = "Nothing happens";
            break;
        default:
            whatHappens = "Please insert a valid direction";
    }
    return whatHappens;
}

console.log(moveCommand("forward"));
```
## Logical Operators

### AND Operator (`&&`)

-   Evaluates each operand as a boolean value.
-   Returns the first falsy value or the last value if all are truthy.
-   Useful for chaining conditions.

Example:
```js
if (username === storedUsername && password === storedPassword) {
    console.log("User authenticated");
}
```
### OR Operator (`||`)

-   Returns the first truthy value it encounters or the last value if all are falsy.
-   Useful for setting default values.

Example:

```js

const fullName = firstName || 'Guest';` 
```

### Nullish Coalescing Operator (`??`)

-   Returns the right-hand operand when the left-hand operand is `null` or `undefined`, otherwise returns the left-hand operand.
-   Useful for assigning default values for potentially `null` or `undefined` variables.

Example:

```js
const nullValue = null;
const defaultValue = 'Default';
console.log(nullValue ?? defaultValue); // "Default"` 
```
## Unary NOT Operator (`!`)

-   Inverts the boolean value of its operand.

Example:

```js
const truthyValue = true;
console.log(!truthyValue); // false` 
```
## Ternary Operator

-   Shorter form of if-else statement. Can be nested but should not be nested more than two levels deep for readability.

Syntax:

```js

condition ? expressionIfTrue : expressionIfFalse` 
```
Example:

```js

const userIsValid = isUserValid(name, userArray);
console.log(userIsValid ? "Hello, user" : "Please log in");
```
Nesting Example:

```js

const toy = gender === 'boy'
    ? birthMonth === 'December'
      ? 'santa hat'
      : 'toy car'
    : birthMonth === 'December'
      ? 'candy cane'
      : 'doll';`
```
