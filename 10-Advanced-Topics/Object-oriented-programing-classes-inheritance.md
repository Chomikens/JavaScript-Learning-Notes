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

  // When we want to modyfi attack function here we also must use super on function and modify its
}

const fiona = new Character("Fiona", 40, "Fists", 10);
const shrek = new Ogre("Shrek", 100, "Sword of Onion", 50, "Green Ogre");

console.log(shrek.attack(fiona));

```