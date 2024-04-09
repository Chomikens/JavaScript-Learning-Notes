# CallStack 
The call stack in JavaScript is a crucial concept that helps us understand how JavaScript executes code. It's like a to-do list for the JavaScript [engine](/02-JavaScript%20Engine/Javascipt-engine.md), but with a very specific way of handling tasks.

## Understanding the Call Stack

-   **First-In, Last-Out (FILO)**: The call stack works on a "First-In, Last-Out" basis. This means that the last function that gets called is the first one to be completed and removed from the stack. It's similar to a stack of plates; you can only take off the top plate without disturbing the others, and the last plate you put on is the first one you take off.
    
-   **How It Works**: When a function is executed in JavaScript, it's placed (or "pushed") onto the call stack. The JavaScript engine then starts executing the function's code. If this function calls another function, the new function is also pushed onto the stack, and the engine executes it first.
    
-   **Execution and Removal**: Once a function completes its execution (i.e., there's nothing left to do), it's removed (or "popped") from the stack. The engine then continues with the next item on the stack. This process continues until the stack is empty.
    
### Example Explained
```js
function subtractTwo(num) {
    return num - 2;
}

function calculate() {
    const sumTotal = 4 + 5; 
    return subtractTwo(sumTotal);
}

calculate();
```
1.  **Calling `calculate()`**: When `calculate()` is called, it's placed on the call stack. Inside `calculate()`, a calculation is made (`sumTotal = 4 + 5`), and then `subtractTwo(sumTotal)` is called.
    
2.  **Calling `subtractTwo()`**: The call to `subtractTwo()` is placed on top of the call stack, above `calculate()`. The JavaScript engine executes `subtractTwo()`, which subtracts 2 from its argument.
    
3.  **Returning from `subtractTwo()`**: After `subtractTwo()` finishes execution, it's removed from the call stack, and the engine returns to the `calculate()` function.
    
4.  **Completing `calculate()`**: Finally, after `calculate()` finishes executing, it too is removed from the call stack.