# Closure memory efficient 

Let imagine we have function thah create big array and retrun n element when we call it

```js
function heavyDuty(index) {
    // Way to create big array and fill it 
    const bigArray = new Array(7000).fill(":)")
    return bigArray[index]
}
```

Everytime we call this `heaveDuty(666)` -it will create array execute code and then garbage collector remove it. 

## How to use it more efficient? 
We can use closure! 

```js
// Closure for memory efficiency
// Function that creates a large array and returns a function to access an element by index
function heavyDutyRefactor() {
    const bigArray = new Array(7000).fill(":)")
    return function(index) {
        return bigArray[index]
    }
}

const getItem = heavyDutyRefactor(); // The array is created once here
console.log(getItem(666)); // Now we can get an item at index 666 without recreating the big array
console.log(getItem(6)); // Access another item at index 6
```