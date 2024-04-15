# Curring 
Currying is a concept that involves transforming a function that takes multiple arguments into a sequence of functions that each take a single argument. It's a useful technique for creating more modular and reusable code.

## Base function 
```js
const discount = (discountValue,price) => { 
   return price * (1 - discountValue);
}

```

## Refactor to curring 
```js
const discCurring = (discountValue) => (price) => price * (1 - discountValue)
const disValue10 = discCurring(0.1) // 10 percent discount
const disValue20 = discCurring(0.2) // 20 percent discount - we can pass different values it's more practical
disValue10(100) // output: 90 

// or use discCuring 
console.log(discCurring(0.1)(100))
```


There ise anothet way to use curring using [Bind](https://github.com/Chomikens/ZTM-JS/blob/8-objects/objects/call()_bind()_apply().md#call-apply-and-bind)

```js
function discount (discountValue,price) { 
   return price * (1 - discountValue);
}

const tenPercent = discount.bind(this, 0.1) 
console.log(tenPercent(100))
```