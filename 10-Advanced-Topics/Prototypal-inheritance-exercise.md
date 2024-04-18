# Prototype exercise

## Exercise: Modify Date 

// Date object => to have a new method .lastYear() which
// shows you last year 'YYYY' format.


## Solution
```js
Date.prototype.lastYear = function() {
  return this.getFullYear() - 1;
};
```
## Exercise: Modify Map

// Modify .map() to print'🗺️' at the end of each iteration.

console.log([1,2,3].map())


## Solution 

Prototype in this case is an Array constructor so we must modyfi this. 

```js
Array.prototype.map = function () {
    const modifyArray = [];
    for (let i = 0; i < this.length; i++) {
        // Here, `this` refers to the specific array [1,2,3] that map was called on.
        modifyArray.push((this[i] + " " + "🗺️"));
    }
    return modifyArray;
}

console.log([1,2,3].map());  // Output: ["1 🗺️", "2 🗺️", "3 🗺️"] Tips: this is point so specyfic array - look where is the dot

```