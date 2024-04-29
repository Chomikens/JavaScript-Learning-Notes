# OOP: Object Create

So how we can achive this [example](Object-oriented-programing-factory-functions.md) more practical?

## `Object.create()`

```js

// First lets create object that sore only methods that we are intrested for

const attackMethod = {
     attack(enemy) {
            enemy.hp -= this.attackValue;  
            return `${this.name} attacks with ${this.weapon}. ${enemy.name}'s hp is now ${enemy.hp}.`;
        }
}
function createElf(name, hp, weapon, weaponAttack) {
  
        // Now lets create new Object

        let newElf = Object.create(attackMethod);
        console.log(newElf.__proto__) // We can check it's propotype
        newElf.name = name;
        newElf.hp = hp;
        newElf.weapon = weapon;
        newElf.attackValue = weaponAttack;

        return newElf;

}


const legolas = createElf("Legolas", 100, "bow", 50);
const gimli = createElf("Gimli", 110, "axe", 10); 
console.log(legolas.attack(gimli));
console.log(gimli.attack(legolas));

```