# Pure Functions
 - The idea of pure function is that function must always return the same output when given the same input; 
 - No side effects - function can't modify anything outside of itself

 ## Side effects 

 As we see in below example we have simple array outside the function; After few call of our function that array has no item inside. 

 This is example of side effects. 

 ```js
 const simpleArr = [1,2,3]; 
 
 function mutableArrayFunc = (arr) {
    arr.pop(); 
 }
 
mutableArrayFunc(simpleArr); 
mutableArrayFunc(simpleArr); 
mutableArrayFunc(simpleArr); 


console.log(simpleArr)

 ```

 ### No side effects 
 So how me can change our function above to pure funcion? 

 ```js
 
 const secondSimple = [1,2,3,4]

 function immutableDeleteLastElement (arr) { 

    const arrayDuplicat = [...arr] 
    arrDuplicat.pop()
    return arrayDuplicat
 }
 
 ```

 ## Input - Output && Referencial Transparency 

 ### Input - Output 
 No matters how many times we call `addNumbers(3,4)` we will have output === 7

```js

function addNumbers (num, num2) {
    return num + num2
}

addNumbers(3,4)

function multiplyByTwo (num) {
    return num *2
}

```

### What is Referencial Transparency? 

Because function are first class Citizen we have pass one function to another function as paramaters - like below. 



```js
multiplyByTwo(addNumbers(3,4))

```

Referencial Transparency tell us this: `multiplyByTwo(addNumbers(3,4))` still will be the same output when we pass to `multibyByTwo` result of `addNumbers` in our example: 7;

## an everything be pure ? 

No, because our code will interact with DOM, change it, etc etc. 

The idea of this approach is to minimalize siede effects.