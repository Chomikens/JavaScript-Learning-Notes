# OOP: Introduction

In OOP we create object in which we create state (properties) and methods that manipulate that state

```js
const dragon = {
    fire: true, // State
    hp: 500, // State

    attack(enemy) { // methods to modify state
        if (this.fire) {
            enemy.hp -= 100;  // Reducing the enemy's hp when attacked by the dragon
        }
    }
};

const soldier = {
    hp: 100,
};

console.log("Dragon HP:", dragon.hp);
console.log("Soldier HP:", soldier.hp);
dragon.attack(soldier);
console.log("Soldier HP after being attacked by the dragon:", soldier.hp);
```

When we face OOP there are two main approach: Class Based OOP and Prototype Based OOP. 