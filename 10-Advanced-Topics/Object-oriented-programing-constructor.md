# OOP: Constructor Function

```js
function CreateElf(name, hp, weapon, weaponAttack) {
    this.name = name;
    this.hp = hp;
    this.weapon = weapon;
    this.attackValue = weaponAttack;
}

CreateElf.prototype.attack = function(enemy) {
    enemy.hp -= this.attackValue;
    return `${this.name} attacks with ${this.weapon}. ${enemy.name}'s hp is now ${enemy.hp}.`;
};

// Creating instances
const legolas = new CreateElf("Legolas", 100, "bow", 50);
const gimli = new CreateElf("Gimli", 110, "axe", 10);

console.log(legolas.attack(gimli));  // Legolas attacks Gimli
```

## What does new keyword do? 

In short terms it binds this to new object - not f.e a window. 