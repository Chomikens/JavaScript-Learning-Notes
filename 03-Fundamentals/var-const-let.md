
## 1. `var` - Function Scope

-   **Scope**: Variables declared with `var` are scoped to the function in which they are declared, or globally if declared outside of a function.
-   **Hoisting**: `var` declarations are hoisted to the top of their containing scope, but their initialization is not. This means you can reference them throughout their containing scope, but they will only have their assigned value after the line on which they are initialized.
-   **Re-declaration**: It's possible to re-declare the same variable within the same scope without error, which can lead to confusion and bugs.

```js
console.log(x); // undefined
var x = 5;
console.log(x); // 5

function exampleFunction() {
    var y = 10;
    console.log(y); // 10
}
console.log(y); // ReferenceError: y is not defined

```

## 2. `let` - Block Scope

-   **Scope**: `let` declarations are block-scoped, meaning they are only accessible within the nearest enclosing block (e.g., `if`, `for`, function block).
-   **Hoisting**: `let` declarations are hoisted to the top of their block scope but are not initialized. Accessing them before the declaration results in a ReferenceError (temporal dead zone).
-   **Re-declaration**: Re-declaring the same variable within the same scope is not allowed and will throw an error, making `let` safer to use than `var`.
```js
let z = 1;
if (true) {
    let z = 2; // This is okay, `z` is scoped within the block
    console.log(z); // 2
}
console.log(z); // 1

```
## 3. `const` - Block Scope and Constant

-   **Scope**: Like `let`, `const` is block-scoped.
-   **Immutability**: While a `const` variable cannot be re-assigned, it does not make the value it holds immutable. For example, if the value is an object or array, its properties or elements can still be modified.
-   **Initialization**: Variables declared with `const` must be initialized at the time of declaration.
```js
const greeting = "Hello, world!";
console.log(greeting); // Hello, world!

// Cannot do: greeting = "Another greeting"; // TypeError

const numbers = [1, 2, 3];
numbers.push(4);
console.log(numbers); // [1, 2, 3, 4]
// But cannot reassign `numbers` to a new array or value

```
## When to Use `var`, `let`, and `const`

-   **Use `const` by default** for all variables that do not need to be reassigned. This communicates intent more clearly and helps prevent accidental reassignments.
-   **Use `let`** for variables whose values are expected to change over time. For instance, counters in loops, or values that are recalculated.
-   **Avoid `var`** if possible, due to its confusing scoping. However, be aware of it and its behavior, as you may encounter it in older codebases or need to use it when dealing with specific legacy issues where function scope is required.


