# Memoization 
Memoization is special form of Caching.
In simpler words it's abillity to store values to later use them on. 
This method is used to speed up programs and hold data in easly acessible box. 


## Example 
Let's imagine we have function that get a number (params) and add it to 80. But before this some massive calculation will be done. 

```js
function addNumberTo80 (n) {
    console.log('Massive calculation')

    return n + 80 
}

addNumberTo80(5) // Massive calculation; 85
addNumberTo80(5) // Massive calculation; 85
addNumberTo80(5) // Massive calculation; 85
```
### Important
On each call on this fn we do massive calculation - so how to prevent this? 

### Solution with Memoization 

```js

let cache = {} // Create empty object to store our examples; 

function addNumberTo80Memo (n) {
    if(n in cache) { // This is method to check if something is in object. This is eqal to if (cache.n)
    return cache[n]
    } else {
        console.log('Massive calculation')
        cache[n]= n + 80
        return cache[n]

    }
}

addNumberTo80Memo(5) // Massive calculation; 85
addNumberTo80Memo(5) // 85

```

### Solution refactor 
Ideally we dont want cache to be in global env. 

```js
function memoClosure () {
    let cache = {} 
    return function(n) {
        if(n in cache) { // This is method to check if something is in object. This is eqal to if (cache.n)
        return cache[n]
    } else {
        console.log('Massive calculation')
        cache[n]= n + 80
        return cache[n]
        }
    }
}

const addNumberCashing = memoClosure()
console.log(addNumberCashing(5))
console.log(addNumberCashing(5))


```