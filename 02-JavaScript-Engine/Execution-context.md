
# Execution Context

Consider the following JavaScript code snippet:
```js
function printName() {
    return 'Dominik Kotorożec';
}
function findName() {
    return printName();
}

function sayName() {
    return findName();
}
sayName();` 
```
When the JavaScript (JS) engine encounters this code, it performs several steps to execute it, primarily involving the creation and management of execution contexts. Here's a more accurate description of the process:

1.  **Global Execution Context Creation**: Before executing any code, JS creates a global execution context. This context is for variables and functions not inside any other function. It's the default or base execution context where your script starts its execution. In this context JS give us Global Object and global this
    
2.  **Execution Context for Each Function Call**: When the JS engine encounters a function call (signaled by the parentheses `()`), it creates a new execution context for that function. Each function call gets its own execution context, which includes the function's local variables, parameters, and the ability to access variables in the global context or outer functions' contexts (if any).
    
3.  **Call Stack Management**: The call stack is a LIFO (Last In, First Out) structure that tracks which execution context is currently running.
    
    -   When a function is called, its execution context is pushed onto the call stack.
    -   JS then starts executing the function body. If this function calls another function, the new function's execution context is created and pushed onto the call stack.
    -   After a function completes execution, its execution context is popped off the call stack, and control returns to the context below it on the stack.
4.  **Execution Flow in the Provided Code**:
    
    -   The `sayName()` function is called, creating its execution context and pushing it onto the call stack.
    -   Inside `sayName()`, `findName()` is called, creating a new execution context for `findName()` and pushing it onto the call stack.
    -   `findName()` then calls `printName()`, which also gets its execution context pushed onto the call stack.
    -   `printName()` returns a string, and its execution context is popped off the call stack. Control returns to `findName()`, which then also completes and gets popped off the stack.
    -   Finally, control returns to `sayName()`, which completes and gets its context popped off the call stack, leaving the global execution context.
5.  **Global Context Completion**: The global execution context is the last to be popped off the call stack when the entire script finishes executing. Unlike function execution contexts, which are created and destroyed during the script's execution, the global execution context exists throughout the life of the script.
