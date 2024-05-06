# Partial Application 

This can often be confused with [curring](../04-Functions/Curring.md)

## Explanation 
This is a process of producing a function with a smaller number of parametrs.
We applying some of its arguments - so its remembers those parametrs and then it use closures on be called with all the rest of args


## Curring vs Partial Application 

```js

//Curring 

const multiplyFunction = (a) => (b) => (c) => a * b * c 
const multiplyByFive = multiplyFunction(5)
multiplyByFive(4)(10) // This will 5 * 4 * 10 

// Partial Application 

const multiply = (a, b, c) => a * b * c 
const partialApplication - multiply.bind(null, 5) // null is because we dont care about "this"
partialApplication(4, 10) // This will 5 * 4 * 10 
```