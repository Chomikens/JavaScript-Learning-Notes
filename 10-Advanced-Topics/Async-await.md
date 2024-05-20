# Async - Await 

Async await is ES 8. And it's build on top o [promises](Async-promise.md)
Also benefit it's make code easier to read. Let's look: 

## Promise version 
```js
function fetchPlayer (url) {
    if(!url) Promise.resolve(new Error('You need to pass and endpoint url!'))

    return fetch(url)
    .then(response => {
        if(!response.ok) {
            return Promise.resolve(new Error(`Unable to fetch the data: Reson ${response.status}`))
        }
        return response.json()
    })
}

fetchPlayer('https://jsonplaceholder.typicode.com/todos/1')
.then(data => console.log(data))
.catch(error => console.error(error.message))

```

## Async / Await version 

```js
 async function fetchPlayer (url) {
    if(!url) await Promise.resolve(new Error('You need to pass and endpoint url!'))

   const response = await fetch(url)
   const data = await response.json()
   console.log(data)
   
}


fetchPlayer('https://jsonplaceholder.typicode.com/todos/1')
```

### How to understand `await`
Imagine that await is: wait for exevute untill i have something for you. 


### Where put `await`
We can put await front of any function that returns promise. 

## Async function on arrays 

```js
const urls = [
  'https://jsonplaceholder.typicode.com/todos/1', 
  'https://jsonplaceholder.typicode.com/todos/2',
  'https://jsonplaceholder.typicode.com/todos/3',
  'https://jsonplaceholder.typicode.com/todos/4'
]


const dataFromUrl = async function (urls) {
    const [users, posts, albums] = await Promise.all(urls.map(async url => { 
        /* ==  Why in map we also need async? == 
        
        Without it we have an issue in code that lies within the map function inside the Promise.all call. We  are trying to use await inside a function that you pass to map, but you haven't declared that function as async. This results in a syntax error because await can only be used inside async functions.
        */
        const response = await fetch(url);
        const data = await response.json();
        return data;  
    }));

    console.log(users, posts, albums);
}



dataFromUrl(urls)
```


```js
const urls = [
  'https://jsonplaceholder.typicode.com/todos/1', 
  'https://jsonplaceholder.typicode.com/todos/2',
  'https://jsonplaceholder.typicode.com/todos/3',
  'https://jsonplaceholder.typicode.com/todos/4'
];

const dataFromUrl = async function (urls) {
    return await Promise.all(urls.map(async url => {
        const response = await fetch(url);
        const data = await response.json();
        return data;  
    }));
};

// Creating an async function to use await 

/*
Using async and await: By declaring fetchAndLogData as an async function and using await when calling dataFromUrl, you tell JavaScript to pause execution of fetchAndLogData at the point where await is used, until the promise resolves. Once it resolves, the resulting data is stored in the variable data, and any code following this inside the fetchAndLogData function can safely use data, knowing it holds the fetched data.
*/
async function fetchAndLogData() {
    const data = await dataFromUrl(urls);
    console.log(data);  // Logs the actual data after it's fetched
}

fetchAndLogData();


```

## Async try & catch block; 


```js

const dataFromUrl = async function (urls) {
    
    try {const [users, posts, albums] = await Promise.all(urls.map(async url => { 
        const response = await fetch(url);
        const data = await response.json();
        return data;  
    }));

    console.log(users, posts, albums);
}
catch (error) {  // Catch any errors that occur during the try block
        console.error(error.message);  // Log the error message
    }
}



dataFromUrl(urls)


```