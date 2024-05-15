# AJAX
For this far everytime we get response from server our page will refresh. So how can we solve this? 
When we need to load small chunck of data we can use `AJAX`

```js

fetch('https://jsonplaceholder.typicode.com/todos/1')
      .then(response => response.json())
      .then(json => console.log(json))
```

It allows us to change content dynamilcy. 

`Fetch` will return a [Promise](Async-promise.md). 
We can undestand this as: Hey! I'm making a request somehere over the Internet and I PROMISE to let you know when i have return this value

`response` is JSON so fetch has own method like `JSON.parse()`. This method is `response.json()`.