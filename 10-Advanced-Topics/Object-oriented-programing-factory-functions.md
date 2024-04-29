# OOP: Factory Functions

Let's create a simple game with elves, dwarws etc. 

To not create an object always when we want new elf and reapet ourselves, we can use factory function: 

```js

function createElf(name, hp, weapon, weaponAttack) {
    return {
        name,
        hp,
        weapon,
        attackValue: weaponAttack,

        attack(enemy) {
            enemy.hp -= this.attackValue;  
            return `${this.name} attacks with ${this.weapon}. ${enemy.name}'s hp is now ${enemy.hp}.`;
        }
    };
}

const legolas = createElf("Legolas", 100, "bow", 50);
const gimli = createElf("Gimli", 110, "axe", 10); /
console.log(legolas.attack(gimli));

```

What's about disadvantage of this approach? 
We use to much memory for storing each attack method - it's not effecient!