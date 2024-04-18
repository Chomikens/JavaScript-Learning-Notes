# What is safe way to create prototype? 

## `Object.create()`

```js

const human = {
    mortal:true, 

}

const socrates = Object.create(human) // Here we create an object based on human and human are prototype of socrates

console.log(human.isPrototypeOf(socrates)) // true



function sing (){
   return `Am I mortal? ${this.mortal}` // We create function and then bind this to object.
}


const socratesSing = sing.bind(socrates)
socrates.sing = socratesSing()
socrates.sing
socrates.age = 78;

console.log(socrates)
```