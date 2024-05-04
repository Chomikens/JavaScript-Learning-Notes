# Immutability  

Immutability is ability to not change the state - look below for example 


```js

const exampleObject = {name: "Dominik", age: 34}

function pureClone (data) {
  return {...data} // This is pure 
}

// exampleObject.name = "Lorem" - This is change to state 

// So to change stare we can make a copy of object using function and then update copy state; 


function updateName (obj) {
    const clone = pureClone(obj); 
    clone.name = "Lorem"
    return clone
}

```

What about memory efficient in cloning all things? 

## Structural Sharing 

In short terms - copy only this part of obj/array/any sort of data that you need at the moment;