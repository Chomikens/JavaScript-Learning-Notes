# Job Queue

```js
// Callback Queue - Thanks to WEB API 
setTimeout(()=>{console.log('1', 'is the loneliest number')}, 0)
setTimeout(()=>{console.log('2', 'can be as bad as one')}, 10)

//2 This is Microtask Queue (Job Queue). 
// This has higher prioritate than callback queue. So JS will look first at this, after that callback queue. 
Promise.resolve('hi').then((data)=> console.log('2', data))

//3 - This is not async - so this will console.log first. 
console.log('3','is a crowd')
```