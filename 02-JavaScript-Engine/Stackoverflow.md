# Stackoverflow 
Stack overflow is a term that describes what happens when the [call stack](/02-JavaScript-Engine/Callstack.md) — the place where JavaScript tracks function calls—exceeds its limit. In simpler terms, it's like overloading a plate with too much food until it can no longer hold anything more and everything spills over.

## How Does a Stack Overflow Occur?

-   **The Nature of Recursion**: Recursion occurs when a function calls itself. While recursion can be a powerful tool for solving certain problems, it needs careful handling to avoid issues. The example provided demonstrates a simple recursive function that calls itself without an end condition:
```js
function inception() {
    inception(); // This recursive call creates an infinite loop.
}
```
-   **Infinite Recursion Leads to Stack Overflow**: In the example, `inception()` calls itself endlessly. Each call is added to the call stack, but since there's no condition to stop the recursion, it continues indefinitely. The call stack has a limited size, so eventually, it runs out of space to store new function calls. This is when a stack overflow occurs.

## What Happens During a Stack Overflow?

-   **Call Stack Limit Exceeded**: The JavaScript engine keeps track of all the function calls in the call stack. When the stack is full and cannot accommodate any more calls, the engine throws a "stack overflow" error. This is the engine's way of saying, "I can't handle any more function calls; you've asked me to do too much."
    
-   **The Program Crashes**: Once a stack overflow error is thrown, the program can no longer continue to execute. This is similar to a circuit breaker tripping when too much electrical current flows through it. The system stops to prevent damage or further issues.
 

## Preventing Stack Overflow

-   **Base Case in Recursion**: To prevent stack overflow in recursive functions, it's crucial to include a base case. A base case is a condition that tells the recursive function when to stop calling itself. This prevents infinite recursion and, subsequently, stack overflow.
```js
function countDown(number) {
    if (number <= 0) {
        console.log("Done!");
        return;
    }
    console.log(number);
    countDown(number - 1);
}
```
In this improved example, the `countDown` function decreases the number by 1 with each recursive call and stops when the number is 0 or less, preventing a stack overflow.
