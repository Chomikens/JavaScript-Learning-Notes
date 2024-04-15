
# Loops 
- In short terms loops are block of code that will execute n numbers of time. 
- Loops are fundamental in programming for performing repetitive tasks.
-  In JavaScript, loops can iterate over any iterable object. Iterable objects include Arrays, Strings, and certain Object types like Map and Set. Regular Objects are not iterable by default, but you can iterate over their properties in different ways: Arrays, Object and Strings

### Example for loops 

```js
const loopArrayBase = [1, 2, 3, 4, 5, 6]
const loopArrayObjects = [
    {name:"user1",},
    {name:"user2",},
    {name:"user3",},
    ]

const loopObject = {
    name: "Dominik",
    lastName: "Kantorowicz",
    havePet: true, 
    petName: "Zagwozdka",
    petNumber: 1,
}
```
## Basic

### For loop 
Traditional loop with a counter, condition, and increment/decrement expression.

```js
for (counter, condition, increment/decrement expression) {
    // Do something
}

for(let i = 0; i< loopArrayObjects.length; i++) {
    console.log(loopArrayObjects[i].name) // it will show us each object in array
}
```

###  While  loop 
Executes as long as a specified condition is true.

```js
let counter = 0 // starting position
while (counter < loopArrayObjects.length) { // check the condition 
console.log(loopArrayObjects[counter]) // Then do this
counter ++
}
```

### Do-While Loop
Similar to the while loop, but it runs at least once and then checks the condition.

```js
let counterTwo = 10

do {
    console.log(counterTwo) // Do this at first
    counterTwo--
} while (counterTwo > 0) // Then check the condition
```


## Modern 

## For in (ES 5)
Iterates over the enumerable properties of an object. 
Check [Get object property via variables](https://github.com/Chomikens/ZTM-JS/blob/8-objects/objects/objects.md#how-to-get-value) to better understand: `loopObject[key]`

```js
for (key in loopObject) {
    console.log(loopObject[key]) // We must get value using bracket notation to get it via variable
}
```

## For of (ES 6+)
Introduced in ES6, iterates over iterable objects (like arrays, strings, maps, sets, etc.), accessing the values directly rather than their indexes or keys. 

```js
for (item of loopArrayBase) {
    console.log(item)
}
```



