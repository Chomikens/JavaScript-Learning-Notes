# Closure  
A way for a function to retain access to its lexical scope (where it was defined) even when the function is executed outside that scope.

In JavaScript, a closure is a function that remembers the variables from the place where it was defined, regardless of where it is executed later. This means that the function can access and manipulate variables that were in its scope when it was created, even after those variables are no longer in the global scope. This is a powerful feature because it allows for data encapsulation and creates private variables.


## Why Closures are Useful:

1.  **Data Encapsulation**: You can create private variables that can't be accessed directly from outside the function.
2.  **Maintaining State**: In event handlers or callbacks, closures can remember and continue to access variables from their defining scope.

### Private Variables: 

This example shows how `createCounter` returns a function that forms a closure around the variable `count`. Each time you call `counter()`, it increments and returns the `count` value. The `count` variable is encapsulated within the closure, making it private and only accessible through the returned function.

```js
function createCounter() {
    let count = 0; // 'count' is a private variable created by the closure
    return function() {
        count += 1;
        return count;
    };
}

const counter = createCounter(); // The function 'counter' forms a closure around 'count'
console.log(counter()); // 1
console.log(counter()); // 2
// 'count' is not accessible directly, but 'counter()' can manipulate it


```

### Encapsulating Variables
Here, `greet` returns a function that forms a closure around `greetingMessage` and `name`. Even after `greet` finishes execution, the returned function can still access `greetingMessage` and `name`, demonstrating how closures can capture and maintain the environment in which they were created.

```js
function greet(name) {
    let greetingMessage = "Hello"; // This variable is enclosed by the returned function
    return function() {
        console.log(greetingMessage + ', ' + name + '!');
    };
}

const greetJohn = greet("John");
greetJohn(); // Outputs: "Hello, John!"
// The function remembers 'greetingMessage' and 'name' even after 'greet' has finished executing

```

### Using Closures with Event Listeners 
Creating Factory Functions: You have multiple elements that need similar but slightly different event listeners, and you want to create these listeners dynamically with specific captured data for each one.


In this example, the function provided to `addEventListener` forms a closure around the `message` variable. Even though the function will be executed in response to a click event sometime in the future, it still has access to `message`, thanks to the closure.


```js
function setupButton(buttonId, message) {
    const button = document.getElementById(buttonId);
    button.addEventListener('click', () => {
        alert(message);
    });
    // The function passed to 'addEventListener' forms a closure around 'message'
}

setupButton('myButton', 'Button clicked!');
```