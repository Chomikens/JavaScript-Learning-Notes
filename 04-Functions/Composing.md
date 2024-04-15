# Compose 
Compose in JavaScript often refers to a functional programming concept where you create a new function by combining multiple functions. It's a way of building up more complex operations by combining simpler ones. The basic idea is to take some functions and produce a new function that is the result of those functions being called in sequence, with the output of one function being the input to the next.

Imagine you have two simple tasks:
 - Add 2 to a number.
 - Multiply by 3 the result of the first task.

## Base function

```js
function addTwo(x) {
  return x + 2;
}

function multiplyByThree(x) {
  return x * 3;
}
```


## Compose 
```js
const result = multiplyByThree(addTwo(4)); // Look here in revert order of function. It;s because it need to evaluate first the "right side" 
```

### More examples 

```js

/**
 * @param {function} - f is function 
 *  @param {function} - g is function 
 */
const add1ToNumber = (num) => num +1
// What the heck is happening here 
const composeFunc = (f,g) => (a) => f(g(a))
// Lets explain it passing args
console.log(composeFunc(add1ToNumber, add1ToNumber)(5))



```

```js
const add1ToNumber = (num) => num + 1;
// Modifying composeFunc to work with two arguments
const composeFunc = (f, g) => (a, b) => f(g(a), b);

// Example usage:
// g will be applied to 'a' only, and f will take the result of g(a) and 'b'
const addAndMultiply = (resultOfG, b) => resultOfG * b;

// Composing the new function
// This will first add 1 to 5 (g(a)), resulting in 6, and then multiply 6 by 2 (f(g(a), b))
console.log(composeFunc(addAndMultiply, add1ToNumber)(5, 2)); // Output should be 12

```