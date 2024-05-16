```js
// Solve the questions below:

// #1) Create a promise that resolves in 4 seconds and returns "success" string

const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("success")}
    ,4000)
})

// #2) Run the above promise and make it console.log "success"
promise
.then(respond => console.log(respond))
.catch(err => err)


// #3) Read about Promise.resolve() and Promise.reject(). How can you make
// the above promise shorter with Promise.resolve() and console loggin "success"
const promise = Promise.resolve(
  setTimeout(() => {
    console.log("success");
  }, 4000)
);

// #4) Catch this error and console log 'Ooops something went wrong'
Promise.reject('failed')
.catch(console.log('Ooops something went wrong'))

// #5) Use Promise.all to fetch all of these people from Star Wars (SWAPI) at the same time.
// Console.log the output and make sure it has a catch block as well.
const urls = [
  'https://jsonplaceholder.typicode.com/todos/1', // If null of undefined se 41
  'https://jsonplaceholder.typicode.com/todos/2',
  'https://jsonplaceholder.typicode.com/todos/3',
  'https://jsonplaceholder.typicode.com/todos/4'
]

function fetchAllData(urls) {
  return Promise.all(urls.map(singleUrl => {
    // If any of urls are null, undefinde it will reject promise;
    if (!singleUrl) return Promise.reject(new Error('fetchData: URL is required but got ' + url));
  
        return fetch(singleUrl)
        .then(response => {
          if(!response.ok) Promise.reject(new Error('Unable to fetch url' + response.status))
          return response.json()
        })
   }))     
}

function renderUser(arr) {
  return arr.map(user => {
   const{title} = user;
   return title
  })
}

fetchAllData(urls)
.then(data => console.log(renderUser(data)))
.catch(error => console.error(error.message))

// #6) Change one of your urls above to make it incorrect and fail the promise
// does your catch block handle it?
```