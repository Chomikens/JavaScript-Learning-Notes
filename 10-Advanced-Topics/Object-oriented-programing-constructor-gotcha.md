# OOP: Constructor Function - The biggest Gotcha!

The biggest gotcha in prototype is function inside function - see below!

```js
function CreateElf(name, hp, weapon, weaponAttack) {
    this.name = name;
    this.hp = hp;
    this.weapon = weapon;
    this.attackValue = weaponAttack;
}

CreateElf.prototype.attack = function(enemy) {

    function attacking () {
        enemy.hp -= this.attackValue; // this will be bing to window. 
        return `${this.name} attacks with ${this.weapon}. ${enemy.name}'s hp is now ${enemy.hp}.`;
    }

   return attacking() // Undefined
};

```

## How to solve this? 
```js
CreateElf.prototype.attack = function(enemy) {
  const self = this // We bind this to object.
    function attacking () {
        enemy.hp -= self.attackValue; 
        return `${self.name} attacks with ${self.weapon}. ${enemy.name}'s hp is now ${enemy.hp}.`;
    }

  return attacking() // Correct way. 
};

```


## Second approach with out self

```js
CreateElf.prototype.attack = function(enemy) {

    function attacking () {
        enemy.hp -= self.attackValue; 
        return `${self.name} attacks with ${self.weapon}. ${enemy.name}'s hp is now ${enemy.hp}.`;
    }

  return attacking.bind(this) // Correct way. 
};

// Creating instances
const legolas = new CreateElf("Legolas", 100, "bow", 50);
const gimli = new CreateElf("Gimli", 110, "axe", 10);

console.log(legolas.attack(gimli));  // Legolas attacks Gimli
```
