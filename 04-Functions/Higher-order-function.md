# Higher order function 

## Short defenition
Simply this is a function that can take function as argument or return other function

## Why HOF can be usefull 


### Case #1 - simple function
Imagine we have function that autencicate user to out system - for example Adam.
But what if we have also let Eva login to our system? In case below we must write whole new function for Eva. 

```js
// Imagine we have function that autencicate user to out system 

function letAdamLoginToSystem () {

    // some code that take a bit of time 

    return `Acces granted to Adam`
}
```

```js
// Imagine we have function that autencicate user to out system 

function letEvaLoginToSystem () {

    // some code that take a bit of time 

    return `Acces granted to Eva`
}
```


### Case #2 - function that accept parameters.
This is much better solution - we dont DRY - until there are for example other roles like: admin, menager etc. 

```js

const giveAccesTo = (name) => `Acces granted to ${name}`

function letUserLoginToSystem (user) {

    // some code that take a bit of time 

    return giveAccesTo(user)
}

letUserLoginToSystem("Adam")
letUserLoginToSystem("Eva")

```

Where there is other role we DRY becouse we must copy  letUserLoginToSystem update it's body and then invoke it with giveAccesTo  



### Case #3 - Higher order function. 

First let's create function that will simulation login time 


```js

const giveAccesTo = (name) => `Acces granted to ${name}`

function authenticate (verify) {
 
 // Some pseudo code that use verify params to simulate time to login 

 let array = []; 
 for (let i = 0; i < verify; i++) {
    array.push(i)
 }
return giveAccesTo(person.name)

}

```


Now we can write function that allow different level to acces. 

```js

funcion letPersonLogin(person, fn) {
if (person.level ==="admin") {
  return  fn(50000)
} else if (person.level==="user") {
   return  fn(1000)
}
}
```

Now we invoke this
```js
letPersonLogin({level: "user", name:"Tim"}, authenticate)
```