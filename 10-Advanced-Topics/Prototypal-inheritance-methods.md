# Prototypal Inheritance - tips and tricks 

## Importat
`.__proto__` is really bad for performane - we should not do this. There is proper way to achive this. 

## `isPrototypeOf()`
### How to check if one object is prototype of an another? 

```js
const dragon = {
    name:"Ballrog", 
    fire:true,
    fight (){
        return 5
    }, 
    sing() {
        return `I'm ${this.name} and you shall burn`
    },
}



const lizard = {
    name:"Kiki",
    fight(){
        return 1
    }
}


lizard.__proto__ = dragon 
dragon.isPrototypeOf(lizard) //true
```

## `hasOwnProperty()`
### How to check if one object has own property not this inherit 

```js
const dragon = {
    name:"Ballrog", 
    fire:true,
    fight (){
        return 5
    }, 
    sing() {
        return `I'm ${this.name} and you shall burn`
    },
}



const lizard = {
    name:"Kiki",
    fight(){
        return 1
    }
}

lizard.__proto__ = dragon; 

for (let prop in lizard) {
    if (lizard.hasOwnProperty(prop)){
        console.log(prop) // name and fight only
    }
}

```