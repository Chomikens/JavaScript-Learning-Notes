
# How to write optimiesed code?

To help JS Engine compile we want to be carefull with these below:

-   using `eval()` - just Never use eval()! -- MDN
    
-   we must be really carefull using `arguments object` . The arguments object is a local variable available within all non-arrow functions. You can refer to a function's arguments inside that function by using its arguments object. It has entries for each argument the function was called with, with the first entry's index at 0. 
- **Never use arguments directly without .length or [i]**
    ```js
    function func1(a, b, c) {
        console.log(arguments.length);
    }
  ```
-   for in loop - can also be problem. Use object.keys/entries or values
-   with
-   delete - JS like predictable code and have hidden classes. When we delete something - it will look at it and think o - this another object.
    
## Inline caching

Inline caching relies on the assumption that objects with the same hidden class (shape) will store properties in the same way, making it an effective optimization for code that frequently accesses properties on objects of the same shape.

### Hidden Classes
Hidden classes (also known as "shapes" or "structures" in some JavaScript engines) are an optimization technique used by JavaScript engines like V8 (Chrome, Node.js). They are not part of the JavaScript language itself but an implementation detail of the engine.

JavaScript objects are dynamic, meaning properties can be added and removed at runtime. This dynamic nature makes it hard for engines to optimize. To address this, JavaScript engines use hidden classes to keep track of the shape of objects—what properties they have, in what order, and of what type.
