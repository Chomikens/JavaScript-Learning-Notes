# OOP: Classes Inheritance

Imagine we have a lot more type of character in out game. 
And we want to avoid DRY and have one instace of character and rest of character will extend method and properties. 


```js
class Character {
  constructor(name, hp, weapon, attackValue) {
    this.name = name;
    this.hp = hp;
    this.weapon = weapon;
    this.attackValue = attackValue;
  }

  attack(enemy) {
    let { name, hp } = enemy;
    hp -= this.attackValue;
    return `${name} was hit by ${this.weapon}. Health is ${hp}`;
  }
}

class Ogre extends Character {
  constructor(name, hp, weapon, attackValue, type) {
    console.log(this) // It wont work - because we must first call super
    super(name, hp, weapon, attackValue); // We must use super to modify state and inherit previous ones
        console.log(this) // It will point to Ogre
    this.type = type;
  }

// No super in Overridden Method: If you want to completely redefine the method in your subclass without reusing any part of the base class implementation, you do not need to use super. You would simply write the new method implementation without referencing super.

//  When you override a method in a subclass but still want to use the base class's method (either before, after, or in between your additional subclass logic), you use super.methodName(...). This is what you're seeing with super.attack(enemy) in your Ogre class. It calls the attack method of the base Character class, allowing you to extend or modify its behavior while still leveraging the 
}

const fiona = new Character("Fiona", 40, "Fists", 10);
const shrek = new Ogre("Shrek", 100, "Sword of Onion", 50, "Green Ogre");

console.log(shrek.attack(fiona));

```

## Important to remember 


### Correct Syntax and Use Cases:

-   **In a Constructor**: Use `super()` to call the parent class constructor.
   ```js
constructor(name, hp, weapon, attackValue) {
	super(name, hp, weapon, attackValue);
	// additional subclass initializations
	} 
```    

-   **In a Method**: Use `super.methodName(args)` to call a specific method of the parent class.
```js
attack(enemy) {
console.log(super.attack(enemy)); 
// Extend the functionality of the parent class's attack method 
// additional subclass behavior
}
```