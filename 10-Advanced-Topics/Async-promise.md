# Promises
What is promise? A Promise is an object that may produce single value some time in the future. 
Either a resolved value or a reson that it's not resolved (rejected).

Promise can be in one of three possible states: 
- fullfilled, 
- rejected, 
- pending. 


## Before promises
Before promises we use callbacks like below: 
```js
button.addEventListener('click', submitForm)

// Callback hell!
moveplayer(100, 'left', function (){
    moveplayer(400, 'left', function (){
          moveplayer(200, 'left', function (){
            moveplayer(200, 'left', function (){

            })
        })
    })
})

```

## How to create promise? 
```js

const promise = new Promise((resolve, reject)=> { // new Promise has two params: resolve and reject
// Then we must put a condition: 
if (true) {
    resolve('Ok, it works');
} else { 
    reject('Error')
    }
})

```

## How to invoke promise? 
```js
promise.then(result => console.log(result))

```


## Chaining promises
```js
promise
.then(result => result + "!")
.then(result2 => console.log(result2))
```

## What if somewhere we have an error? 
We can catch it using `catch` 

```js
promise
.then(result => result + "!")
.then(result2 =>  {
    throw Error; 
    console.log(result2)
})
.catch(() => console.log('Error'))

```

## What makes promises powerfull? 
It's async. 

Let's imagine we have few promises and want resolve them all

```js
const promise = new Promise((resolve, reject) => {
    setTimeout(resolve, 1000, 'Hello')
})

const promise2 = new Promise((resolve, reject) => {
    setTimeout(resolve, 2000, 'Is it me you looking for')
})


const promise3 = new Promise((resolve, reject) => {
    setTimeout(resolve, 10000, 'Naaa I am just passing here dude!')
})

```
### How we can achive this? 
This take all promises and params are array of promises that we want to execute. Exetuce it by longest time (in our case third promise setTimeout time)
```js
Promise.all([promise, promise2, promise3]) 
.then(values => {
    console.log(values)
})

```

## Real world example 

For this we are using JSON Placeholder API 

```js
const apiCallsArray = [
    'https://jsonplaceholder.typicode.co/posts', // Here is mispell to create an Error 
    'https://jsonplaceholder.typicode.com/comments',
    'https://jsonplaceholder.typicode.com/users',
]


Promise.all(apiCallsArray.map(url => {
    return fetch(url) // Fetch is returing a Promise so when we add then we answersing to what we called
    .then(response => response.json())
    .then(results => {
        console.log(results[0])
        console.log(results[1])
        console.log(results[2])
    })
    .catch(()=> console.log('Error'))
}))
```