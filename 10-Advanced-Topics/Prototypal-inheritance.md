# Prototypal Inheritance
Before dive into this topic: see [data structure: object](../06-Data-Structure/README.md)

## Intro
Inheritance is when object gets access to methods and properties of another object. 

```js
const array = [] // Create array
array.__proto___ // This is constuctor to get to propotype an propotype of array. 
array.__proto___.__proto___ // This will get us an object which is prototype

```

## Example 

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

console.log(dragon.sing())


const lizard = {
    name:"Kiki",
    fight(){
        return 1
    }
}

// When our lizard want to sing - we can bing function from dragon 
const kikiSing = dragon.sing.bind(lizard)
```

### What when it will be more complicated? 

```js
const dragon = {
    name:"Ballrog", 
    fire:true,
    fight (){
        return 5
    }, 
    sing() {
        if(this.fire) {

            return `I'm ${this.name} and you shall burn`
        }
    },
}

console.log(dragon.sing())


const lizard = {
    name:"Kiki",
    fight(){
        return 1
    }
}

// When our lizard want to sing - we can bing function from dragon 
const kikiSing = dragon.sing.bind(lizard) 
console.log(kikiSing()) // Ups where we have undefined

```

### Ok so what we have more complex object and want our second object (lizard) to inherit all methods and properties? 
We can use `.__proto__` to inherit all method and object and then overwrite some of these - like below. 


```js
const dragon = {
    name:"Ballrog", 
    fire:true,
    fight (){
        return 5
    }, 
    sing() {
        if(this.fire) {

            return `I'm ${this.name} and you shall burn`
        }
    },
}

const lizard = {
    name:"Kiki",
    fight(){
        return 1
    }
}


lizard.__proto__ = dragon

// Now we can use all of it! 
console.log(lizard.fire, lizard.sing(), lizard.fight())

// lizard.fight will be 1 because we overwtire it
```