# Immediately Invoked Function Expressions (IIFE)

## Syntax

```javascript
(function() {
    // Your code here
})();

```


## Important Notes

-   The initial parentheses `()` around the function indicate that this is a function expression, not a function declaration. This distinction is crucial because only expressions can be immediately invoked.
-   Inside the parentheses, we define an anonymous function and then immediately invoke it with another set of parentheses `()`.

## Practical Example

Consider a scenario where we have multiple scripts on a webpage, and we inadvertently define functions with the same name in different scripts. This can lead to unexpected behavior, as the latter definition will overwrite the previous one.

**Problem Illustration:**
```js
<script>
    function a() {
        return 5;
    }
</script>

<script>
    function a() {
        return 'hahaha'; // This will overwrite the first definition of function a.
    }
</script>
```

**Solution Using IIFE:**

To avoid polluting the global namespace and ensure that our function definitions do not conflict, we can encapsulate our function `a` within an IIFE. This way, each function exists in its own scope, and we can expose any functionality we wish without risk of overwrite. 

```js

<script>
    const iifeFunction = (function() {
        function a() {
            return 5;
        }
        return {
            a: a // Here we expose function a by returning an object that contains a.
        };
    })();

    console.log(iifeFunction.a()); // This approach ensures that we don't pollute the global namespace and can access function a reliably without overwrite.
</script>
```
