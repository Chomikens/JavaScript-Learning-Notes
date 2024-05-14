# Exercise
```js
// Solve the questions below:

// #1) Create a promise that resolves in 4 seconds and returns "success" string

const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("success");
  }, 4000)
});

// #2) Run the above promise and make it console.log "success"

promise
.then(result => console.log(result))
.catch(()=> console.log('Error'))


// #3) Use Promise.all to fetch all of these people from Star Wars (SWAPI) at the same time.
// Console.log the output and make sure it has a catch block as well.
const urls = [
  'https://jsonplaceholder.typicode.com/photos',
  'https://jsonplaceholder.typicode.com/todos',
  'https://jsonplaceholder.typicode.com/users',
  'https://jsonplaceholder.typicode.com/album'
]

Promise.all(urls.map(url =>
    fetch(url)
    .then(response => response.json())
))
  .then(array => {
    console.log('1', array[0])
    console.log('2', array[1])
    console.log('3', array[2])
    console.log('4', array[3])
  })
  .catch(err => console.log('ughhhh fix it!', err));

// #4) Change one of your urls above to make it incorrect and fail the promise
// does your catch block handle it?



```
