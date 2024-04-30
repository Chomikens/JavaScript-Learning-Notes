# OOP: Classes

```js
class Elf {
 constructor(name,hp,weapon,attackValue,) { // Here we use constructor
  this.name = name;
  this.hp = hp;
  this.weapon = weapon;
  this.attackValue = attackValue;
 }
 attack (enemy) {
enemy.hp -= this.attackValue
const {name, hp} = enemy
return `${name} was hit by ${this.weapon}. Health is ${hp}`
 }
}

const elf = new Elf ("Legolas", 500, "bow", 100)
const elf2 = new Elf ("Legolas2", 500, "bow", 100)
console.log(elf2.hp)
elf.attack(elf2)
console.log(elf2.hp)

```

## Why our function is not in constructor? 
Because everytime we create object based on constructor we alocate memory. In upper example attack method is called once and all object point to this memory. 

## How to check is one object is instance of another? 

```js

console.log( elf instanceof(Elf))
console.log( Elf isProtorypeOf(elf))
```