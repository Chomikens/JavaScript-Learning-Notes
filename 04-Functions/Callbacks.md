# Callbacks 
A callback is a function that is passed into another function as an argument to be executed later.

## Example of a callback
An example of a callback in use is the `event listener`.

```js
function callback() {
  // do something
}

button.addEventListener('click', callback)
```

## Why use callbacks?

Callbacks are useful for two situations:

- They allow code to be swapped easily
- They prevent blocking operations in asynchronous code