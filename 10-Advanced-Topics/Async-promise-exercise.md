# Exercise
```js
// Solve the questions below:

// #1) Create a promise that resolves in 4 seconds and returns "success" string

const promise = new Promise((resolve, reject)=> {
    setTimeout(resolve, 4000, "success")
})

// #2) Run the above promise and make it console.log "success"

promise
.then(result => console.log(result))
.catch(()=> console.log('Error'))


// #3) Use Promise.all to fetch all of these people from Star Wars (SWAPI) at the same time.
// Console.log the output and make sure it has a catch block as well.
const urls = [
  'https://swapi.co/api/people/1',
  'https://swapi.co/api/people/2',
  'https://swapi.co/api/people/3',
  'https://swapi.co/api/people/4'
]

// #4) Change one of your urls above to make it incorrect and fail the promise
// does your catch block handle it?



```
