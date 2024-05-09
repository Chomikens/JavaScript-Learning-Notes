# Exercise
```js
// Amazon shopping
const user = {
  name: 'Kim',
  active: true,
  cart: [],
  purchases: []
}


//Implement a cart feature:
// 1. Add items to cart.
// 2. Add 3% tax to item in cart
// 3. Buy item: cart --> purchases
// 4. Empty cart

//Bonus:
// accept refunds.
// Track user history.

```

## Solution 

- Lets write now rest of fucntions 

```js

// This is how we implement more complex compose - when we have more data. 
// Instead of this we can use special libs for compose 
const compose = (f,g) => (...args) => f(g(...args)) 

// We dont know how many function will take purchaseITem so we also need to spread this 
// Addons we must use reduce because it will take f and g but albo iterate over all functions 

function purchaseItem(...fns) {return fns.reduce(compose)} 

 function addItemToCart(user, item) {
     // Why we use here concat? Because we don't want to overwrite those item thaht user has in cart.
    const updateCart = user.cart.concat(item)
    return Object.assign({}, user, { cart: updateCart })
  }

 function applyTaxToItems(user, taxRate = 1.3) {
    const {cart} = user;
    const updatedCart = cart.map(item => {
      return {
        name: item,
        price: item.price*taxRate
      }
    })
    return Object.assign({}, user, { cart: updatedCart })
  }

function buyItem(user) {
    return Object.assign({}, user, {purchases: user.cart})
  }

function emptyCart(user) {
    return Object.assign({}, user, {cart: []})
  }
  
// Important: We are going from right to left so function that we need at first will be at right
purchaseItem(clearCart ,buyItem, taxes, addItem)(user, {name:'laptop', price:300,})

```