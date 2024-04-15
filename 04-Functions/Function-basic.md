
# Function

## Ways to declare functions

- ### Function declaration **(hoisted)**
```js
function name (parametr1, parametr2) {

// Tips
// What exactly do function when you give it params? 
// It;s create temporary variable named like your pamars
// do something 

 return parametr1 * parametr2
	 // When 'return' is executed, the function stops.
	// Statements after 'return' are not executed.
	//console.log("I'm not working, because return")
}
 ```
 
- ### Function expression **(not hoisted)**
```js
	const expressionFunction = function(parameter1, parameter2) {
    return parameter1 * parameter2;
}
 ```
 
- ### Function expression `ES6+ - arrow function` **(not hoisted)**
```js
const handleFunction = (param1, param2) => {
return param1 * param2
}

// Tips#1 - you can write even less code when you dont have parametrs
const handleWithoutParams = () => {
return `You are doing great!`

// Tips#2 - you can write even less code when your function does one thing
const handleWithoutImplicitReturn = () => "You are doing great!"
```
## Ways to invoke/call functions 
  
  ```js
  name (argument1, argument2)
  // When we call/invoke function we can pass arguments - which function convert to it's paramets - order is important
  ```
  
## When use expression and declaration 

In short - when you need anonymous function use `arrow function` in other case use `function name () {}`

## Passing function to function - when params starts to be arguments 

### Example with explain 


```js 
function handleCheckUser(userName, password) { // We pass paramters for function to check user
    for (const element of database) {
        if (userName === element.userName && password === element.password) {
            return true;
        }
    }
    return false;
}

function handleShowFeed(userName, password) {  // We pass paramters for function to show or not feed 
   if(handleCheckUser(userName, password)){  // IMPORTANT - Here we pass handleShowFeed params as arguments for this function. So it's goes back to place when we declare it and pass those arguments to params. 
    console.log(newsfeed)
   } else {
    console.log("Nope")
   }
}

handleShowFeed(userNameInput,userPasswordInput) // Here we pass arguments for final function 

```

## Function defaut values 

Function parametrs can have default values. It can be helpfull when we have property that we want to defined. 
For example function that calculate our income and taxrate. 

### Example 

```js
function calculateTax (income, tax = 0.23) {
    return `Your tax is ${income * tax}`
}

const yourTax = calculateTax(100) // Here in arguments we pass only income, because tax is default
console.log(yourTax)
```

### Example II  - what if after default value is another params? 

```js
function calculateTax (income, tax = 0.23, userName) {
    return `${userName}: your tax is ${income * tax}`
}

const yourTax = calculateTax(100, "Dominik") 
console.log(yourTax) // This will show us: undefined: your tax is NaN
```

#### Why this code show us `undefined`: your tax is`NaN`
Because JS count appearance of params and arguments. 
 - `Income` - is correct; 
 - `tax` - is reassing to "Dominik" so we multiply 100 * Dominik - this is NaN (Yes! if we want to change deafulat values we can do it!) 
 - `userName` - is undefined; 

 #### How to fix it? 
 - by passing undefined in argument that matches place of tax 

 ```js
 
const yourTax = calculateTax(100, undefined, "Dominik") 
 
 ```