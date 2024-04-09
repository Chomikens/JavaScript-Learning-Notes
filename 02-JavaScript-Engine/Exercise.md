```js
console.log(myFavoriteFood);
var myFavoriteFood = "Pizza";

function declareFavoriteFood() {
    console.log(myFavoriteFood);
}

declareFavoriteFood();

```
### What is the output of the first console.log() statement and why? 
In creation phase var is hoisted but only its name not values

### What is the output of the console.log() statement inside the function and why? 
After reaching `declareFavoriteFood();` var is reasing to `Pizza value` so declareFavoriteFood hasn't in scope this variable so it will search upper scope.

```js
function firstFunction() {
    secondFunction();
    console.log('First function executed');
}

function secondFunction() {
    thirdFunction();
    console.log('Second function executed');
}

function thirdFunction() {
    console.log('Third function executed');
}

firstFunction();
```

### In what order will the console.log() statements execute? 
First we invoke whe `firstFunction()`but in body we have call second function which called third. 

So callstack will be: 
 - Global 
 - firstFunction();
 - secondFunction()
 - thirdFunction()

There output will be: 
`Third function executed` - function remove from callstak 
On callstack we have secondFunction() so `Second function executed` - function remove from callstak 
On callstack we have firstFunction() so `First function executed` - function remove from callstak 


```js

var snack = 'chocolate chip cookie';
function getSnack() {
    console.log(snack);
    var snack = 'granola bar';
    return snack;
}
console.log(snack);
console.log(getSnack());

```
### What will be the output of the first console.log(snack); and why?
Outputs: "chocolate chip cookie" because it accesses the global snack variable.

### What will be the output of console.log(getSnack()); and why?
First will be undefined - due to hoising var is "moved" to top of their respective scope. 
Console.log(getSnack()); outputs: "granola bar" because it logs the return value of getSnack(), which is the local snack variable within the function after being assigned 'granola bar'.