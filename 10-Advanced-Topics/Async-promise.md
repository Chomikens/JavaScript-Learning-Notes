
# Promises

## What is a Promise?

A Promise is an object that may produce a single value some time in the future: either a resolved value or a reason that it’s not resolved (rejected).

A Promise can be in one of three possible states:

-   **fulfilled**: The operation was completed successfully.
-   **rejected**: The operation failed.
-   **pending**: The operation has not been completed yet.

## Before Promises

Before Promises, we used callbacks, which often led to "callback hell," making the code difficult to read and maintain.

```js
button.addEventListener('click', submitForm);

// Callback hell example
movePlayer(100, 'left', function() {
    movePlayer(400, 'left', function() {
        movePlayer(200, 'left', function() {
            movePlayer(200, 'left', function() {
                // Final callback
            });
        });
    });
});

```

## How to Create a Promise
A Promise is created using the `Promise` constructor, which takes an executor function with two parameters: `resolve` and `reject`.
```js
const promise = new Promise((resolve, reject) => {
    // Simulating an asynchronous operation
    if (true) {
        resolve('Ok, it works');
    } else {
        reject('Error');
    }
});

```

## How to Invoke a Promise

You can handle the result of a Promise using the `.then()` method for success and `.catch()` for errors.
```js
promise.then(result => console.log(result)).catch(error => console.error(error));
```
## Chaining Promises

Promises can be chained to perform a series of asynchronous operations.
```js
promise
    .then(result => result + "!")
    .then(result2 => console.log(result2))
    .catch(error => console.error(error));

```
## Error Handling in Promises

Errors in promises can be caught using the `.catch()` method.
```js
promise
    .then(result => result + "!")
    .then(result2 => {
        throw new Error('Something went wrong');
        console.log(result2);
    })
    .catch(error => console.error('Error:', error));

```
## `Promise.resolve` and `Promise.reject`

You can create resolved or rejected Promises directly using `Promise.resolve` and `Promise.reject`.

### Example: Fetch Data with `Promise.resolve` and `Promise.reject`

```js
function fetchData(url) {
    if (!url) {
        return Promise.reject(new Error('URL is required'));
    }
    return fetch(url).then(response => {
        if (!response.ok) {
            return Promise.reject(new Error('Failed to fetch data'));
        }
        return response.json();
    });
}

fetchData('https://jsonplaceholder.typicode.com/posts/1')
    .then(data => console.log(data))
    .catch(error => console.error(error.message));

```

## What Makes Promises Powerful?

Promises are powerful because they allow asynchronous operations to run in the background, improving the responsiveness of applications.

### Handling Multiple Promises

Imagine we have a few promises and want to resolve them all.
```js
const promise1 = new Promise((resolve) => {
    setTimeout(resolve, 1000, 'Hello');
});

const promise2 = new Promise((resolve) => {
    setTimeout(resolve, 2000, 'Is it me you’re looking for?');
});

const promise3 = new Promise((resolve) => {
    setTimeout(resolve, 3000, 'No, I am just passing by!');
});
```
### Using `Promise.all`

`Promise.all` executes all promises in parallel and waits for all of them to complete.
```js
Promise.all([promise1, promise2, promise3])
    .then(values => console.log(values))
    .catch(error => console.error(error));

```
### Advanced Example: Using `Promise.all` with Fetch

Let's fetch data from multiple endpoints.
```js
const apiCalls = [
    'https://jsonplaceholder.typicode.com/posts',
    'https://jsonplaceholder.typicode.com/comments',
    'https://jsonplaceholder.typicode.com/users',
];

Promise.all(apiCalls.map(url => fetch(url).then(response => {
    if (!response.ok) {
        throw new Error('Network response was not ok');
    }
    return response.json();
})))
    .then(results => {
        console.log('Posts:', results[0]);
        console.log('Comments:', results[1]);
        console.log('Users:', results[2]);
    })
    .catch(error => console.error('Error:', error));

```

### Advanced Example: Using `Promise.race`

`Promise.race` resolves or rejects as soon as one of the promises resolves or rejects.
```js
const urls = [
    'https://jsonplaceholder.typicode.com/posts/1',
    'https://jsonplaceholder.typicode.com/posts/2',
    'https://jsonplaceholder.typicode.com/posts/3'
];

Promise.race(urls.map(url => fetch(url).then(response => {
    if (!response.ok) {
        throw new Error('Network response was not ok');
    }
    return response.json();
})))
    .then(result => console.log('Fastest response:', result))
    .catch(error => console.error('There has been a problem with your fetch operation:', error));

```
