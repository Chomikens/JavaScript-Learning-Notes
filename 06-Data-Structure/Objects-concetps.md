

# Important Object Concepts

## Passing by Reference

Objects in JavaScript are passed by reference, meaning that modifying an object through one reference will affect its original and any other references.

```js
const originalObject = { key: 'value' };
const referenceToObject = originalObject;

referenceToObject.key = 'newValue';
console.log(originalObject.key);  // Outputs: newValue` 
```

## Copying Objects

To create a copy of an object without linking to the original, you can use `Object.assign` or the spread operator, both of which perform a shallow copy:

-   **Using `Object.assign`**:
    
```js
    
let copiedObject = Object.assign({}, originalObject);
copiedObject.key = 'new value';
console.log(originalObject.key);  // Outputs: value` 
```
    
-   **Using the spread operator**:
    
```js

let copiedObject = { ...originalObject };
copiedObject.key = 'new value';
console.log(originalObject.key);  // Outputs: value` 
```

## Deep Copying

For deep copies, especially when the object contains nested objects:

-   **Using JSON serialization**:
    
```js
let deepCopiedObject = JSON.parse(JSON.stringify(originalObject));
deepCopiedObject.nested.key = 'new value';
console.log(originalObject.nested.key);  // Outputs: value`
```

## Destucturing 

To access object properties we can use `dot notion` or `bracket notation`. [See more](https://github.com/Chomikens/ZTM-JS/blob/8-objects/objects/objects.md#how-to-get-value)
But what if we want to short it and make it more readable? 

## Example 

```js 
const simpleObject = {
    name:"Dominik",
    nickName:"Kotorozec"
    secondNickname: "Ziemniaki i Mastodonty",
}

// Get values without destucturing  : 
const firstName = simpleObject.name 

// With Destucturing 

const {name, nickName} = simpleObject 
console.log(name)
```

## This in objects 

Short def: 
This is the object that the function is a property of

###  Usage
We can also use this to execute same code for multiple objects

```js


function logName() {
    console.log(this.name)
}
const name = "Kotorożec"


const firstObj = {
    name:"Dominik",
    logName:logName,
}

const secondObj = {
    name:"Lalala",
    logName:logName,
}

firstObj.logName() // Dominik 
secondObj.logName() // Lalala

logName() // Kotorożec - global variable. But here is a twist: However, in strict mode, the value of this remains undefined in functions that are called in such a manner. If you're not in strict mode, this does indeed refer to the global object, 

// Second twist: 
//: When you declare a variable with const, let, or class at the top level (outside of any function, block, or module), it does not create a property on the global object. Instead, it creates a variable in the global lexical environment which is not accessible via the this keyword.

// So, when you declare const name = "Kotorożec", you're not actually setting a property on the global object. As a result, this.name within logName (when called as a standalone function and assuming this refers to the global object like in non-strict mode or in a browser environment) doesn't refer to the name you've defined with const.

// If you wanted name to be a property of the global object, you'd have to explicitly set it as such:
window.name = "Kotorożec"; // In a browser environment
// or
global.name = "Kotorożec"; // In a Node.js environment

```

In JavaScript, the this keyword is a special variable that refers to the current context or object within which it is used. Its behavior can sometimes be a bit tricky to grasp, as it depends on how and where it is employed. Here are some important points to understand about this:

 ### "this" in object methods:
When you use this inside an object method (a function that is a property of an object), it refers to the object itself. In our example, we have one methods, handleSayHi, where we use `this` - more about [this](https://github.com/Chomikens/ZTM-JS/blob/8-objects/objects/this.md)
 ```js
 const example = {
  //... 
    handleSayHi: function () {
        this.name === "Dominik" && this.lastName === "Kantorowicz" 
        ? console.log("Hi Kotorożec!")
        : console.log("Hi User!")
    },
}

 ```

 In the handleSayHi method, this refers to the example object. This allows you to access the object's properties like name and lastName.

 ### "this" in nested object:

 ```js
const outer = {
    name: "Outer",
    inner: {
        name: "Inner",
        logName: function () {
            console.log(this.name); // will refer to inner name
        }
    }
};

outer.inner.logName(); // "Inner"

 ```

 #### So how to refer to "Outer?" from example? 
 Use `arrow function` . If you want to ensure that this inside a nested object's method refers to a specific context, such as the outer object, you can use arrow functions. Arrow functions don't have their own this context and instead inherit it from the surrounding code. 

 ```js
const obj = {
  name: "Billy",
  sing() {
    console.log("a", this);
    const anotherFunc = () => {
      console.log("b", this);
    };
      const anotherFunc2 = function(){
      console.log("c", this);
    };
    anotherFunc()
    return anotherFunc2.bind(this);
  },
};

obj.sing()();

 ```


## Call(), Apply() and Bind() 

### Important: 
Underhood all function use call when invoking function 

```js

function a() {
    console.log("Hi")
}

a() 
//  This is the same as a.call()
//  This is the same as a.apply()
```

### Call

`Call()` has two paramaters: 

- first is an object on which we want call our method

```js
const wizard = {
    name:'Merlin', 
    health:100, 
    heal() {
       return this.health = 100;

}
}

const archer = {
    name:'Legolas', 
    health:30, 
}

 // What if we want to "borrow method from our wizard and heal our archer"
console.log(archer) // 30 
wizard.heal.call(archer)
console.log(archer) // 100 
```

- second is arguments for function that we call 

```js
const wizard = {
    name:'Merlin', 
    health:100, 
    heal(num1, num2) {
       return this.health = num1 + num2;

}
}

const archer = {
    name:'Legolas', 
    health:30, 
}

 // What if we want to "borrow method from our wizard and heal our archer"
console.log(archer) // 30 
wizard.heal.call(archer,30,100)
console.log(archer) // 130 
```

### Apply 
Apply works the same as call, but second arguments are array

```js
const wizard = {
    name:'Merlin', 
    health:100, 
    heal(num1, num2) {
       return this.health = num1 + num2;

}
}

const archer = {
    name:'Legolas', 
    health:30, 
}

 // What if we want to "borrow method from our wizard and heal our archer"
console.log(archer) // 30 
wizard.heal.apply(archer,[30,100])
console.log(archer) // 130 
```

### Bind 
Bind return new function with a certain context and parametrs. 
Usually used for function to be called later on with a certain type of context.

```js
const wizard = {
    name:'Merlin', 
    health:100, 
    heal(num1, num2) {
       return this.health = num1 + num2;

}
}

const archer = {
    name:'Legolas', 
    health:30, 
}

 // What if we want to "borrow method from our wizard and heal our archer"
console.log(archer) // 30 
const healArcher = wizard.heal.bind(archer,30,100)
healArcher() // Invoke function 
console.log(archer) // 130 
```
