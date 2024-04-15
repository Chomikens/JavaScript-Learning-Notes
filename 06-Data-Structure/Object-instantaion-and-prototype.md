# Instantation 
Instantiation is a core concept in JavaScript for creating new objects from classes or constructor functions. It allows for the creation of multiple instances, each with their own set of properties and methods, based on a single template.


## Using Class Syntax

ES6 introduced the `class` syntax, a more readable and syntactically simpler way to create objects and deal with inheritance.
```js
class Player {
    constructor(class, name) {
        this.class = class;
        this.name = name;
    }
    introduce() {
        console.log(`Hi Im ${this.name} and I'm ${this.class}`)
    }
}

// Creating an instance of Player
const player = new Player('Wizard', 'Kotorozec');
console.log(wizard); 

```

## Class Inheritance with `extends` and `super` in JavaScript

What if we we want to create Wizard class to better inherit for players? 
Class inheritance is a mechanism that allows one class (child class) to inherit properties and methods from another class (parent class). This is achieved using the extends and super keywords in JavaScript.


### The extends Keyword 
The extends keyword is used in class declarations or class expressions to create a class as a child of another class.

```js
class Wizard extends Player {
     constructor(class, name, hasSpellBook,) { // It must have own constructor when we want to add something new
            super(class, name) // By using super we call Parent class and inherit it constructor
            this.hasSpellBook = hasSpellBook;
    }
      introduce(){
        super.introduce() // Call to the parent class's method
      }
}
```

## Prototype Inheritance

When an instance is created, it inherits properties and methods from its prototype. This is a powerful feature that allows for the efficient reuse of code.
```js
Player.prototype.shoot = function() {
    console.log('I dont give f*** how big is room! I said i cast fireball');
};

player.shoot(); // Outputs: Vroom Vroom!
```

    Performance: Prototype inheritance is generally more memory efficient. When methods are added to a constructor function's prototype, they are shared across all instances of the constructor. This means that each instance does not have its own copy of each method, saving memory.
    Flexibility: Prototype allows for more dynamic changes to an object's structure at runtime. You can add, modify, or delete properties and methods on the prototype, and these changes will be reflected across all instances.
    Complexity: Direct manipulation of prototypes can be less intuitive for developers coming from class-based languages, leading to potential confusion and errors.