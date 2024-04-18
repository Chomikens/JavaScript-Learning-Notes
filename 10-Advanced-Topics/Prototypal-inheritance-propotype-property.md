# Prototypal Inheritance - prototype property

## Important 
The .__proto__ property of an object points to the prototype of the constructor function that created it.


1.  **`.prototype` on Functions**: This is a special property that only functions have. When a function is used as a constructor (i.e., called with the `new` keyword), the `.prototype` property of the function becomes the prototype of the newly created object.
    
    For example, if you have a function `Person()` and you create a new object using `new Person()`, the new object's internal prototype (its `__proto__`) will be set to `Person.prototype`.
    
2.  **`.__proto__` on Objects**: This is an internal property on all objects (including function objects, since functions in JavaScript are also objects). It points to the prototype object that the object inherits methods and properties from.



### What is a Prototype in JavaScript?

In JavaScript, almost everything is an object. Each object can have a prototype, which is just another object that it inherits properties from. You can think of a prototype as a template or an ancestor.

### How Does it Work?

1.  **Prototype Chain**:
    
    -   When you try to access a property or method of an object, JavaScript first checks if that property or method exists on the object itself.
    -   If it's not found, JavaScript looks at the object’s prototype (its parent), then the prototype’s prototype (grandparent), and so on up the chain until it finds the property or reaches the end of the chain (no more prototypes).
    -   This is known as the "prototype chain."
    
2.  **Function Prototypes**:
    -   Functions in JavaScript are special objects, and they come with an extra feature: a `prototype` property. This property is significant when you use the function as a "constructor" to create new objects.
    -   The `prototype` property of a function is what new objects are linked to when you create them using that function with the `new` keyword. This setup allows all objects created from the same constructor function to share properties and methods, which saves memory and keeps code organized.

### Example in Simple Terms

Imagine you have a function intended to create "Car" objects. You can set common properties (like the number of wheels) on the `prototype` of this function since all cars will share these.

```js
function Car(make) {
  this.make = make;
}
Car.prototype.wheels = 4;
let myCar = new Car("Toyota");
```
-   Here, `myCar` will have its own `make` property set to "Toyota".
-   It doesn’t have its own `wheels` property. However, it can use the `wheels` property from its prototype.
-   If you check `myCar.wheels`, it returns 4, because it looks up the prototype chain and finds `wheels` on the prototype of the `Car` function.
- 
### Why Is This Useful?

-   **Efficiency**: Sharing properties through prototypes means not every object needs its copy of those properties or methods. They can all use the same ones set up on the prototype.
-   **Flexibility**: You can add new properties or methods to a constructor function's prototype at any time, and all objects created from that constructor will automatically have access to these new properties or methods.
