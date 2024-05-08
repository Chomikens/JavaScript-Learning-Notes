# Compose 

Keeping pure function approach let's imagine we need to do two things at the time. 
We want take a number (negative number or positive) multiply it by another number and then take the absolute of it (not negative)
Imagine we have assembly line in a factory so we take data --> fn --> data --> fn --> 

First let's create our own compose func
```js
const compose = (fn1, fn2) => (data, number) => fn1(fn2(data, number)) 

```

Then let's create our function that we need to execute compose 

```js

const multiply = (data, number) => data * number
const absoluteNumber = (output) => {
    if (output >= 0) return output;
    return output * -1;
};

```

Now we create a function that combines 'absoluteNumber' and 'multiply'

```js
const combinedFunction = compose(absoluteNumber, multiply);

```

Now call the combined function with the desired arguments
```js
const finalResult = combinedFunction(-1, 5);
console.log(finalResult); // This will log the absolute value of (-1 * 5), which is 5

```