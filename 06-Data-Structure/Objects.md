# JavaScript Objects

Objects in JavaScript are used to store keyed collections of various data and more complex entities. An object can store data of any type, including other objects and functions (which are referred to as methods when defined within an object).

## Basic Object Structure

Here’s an example of a simple object that illustrates several key concepts:

```js
const example = {
    // Key: Value pair
    name: "Dominik",
    lastName: "Kantorowicz",

    // Use brackets for keys with invalid identifiers or spaces
    ["Invalid key syntax"]: "trolololo",

    // Method using function expression
    handleSayHi: function() {
        this.name === "Dominik" && this.lastName === "Kantorowicz" 
        ? console.log("Hi Kotorożec!") 
        : console.log("Hi User!");
    },

    // ES6+ shorthand method syntax
    handleSayBye() {
        console.log('Bye');
    }
};` 
```
## Accessing Object Properties

You can access properties of an object in two ways:

-   **Dot notation**: Preferred when you know the exact property name.
```js
console.log(example.name);  // Outputs: Dominik
console.log(example.handleSayHi());  // Calls the method, which logs: Hi Kotorożec!` 
```
   
-   **Bracket notation**: Useful for properties with invalid identifiers or when accessing properties dynamically.

```js
console.log(example["Invalid key syntax"]);  // Outputs: trolololo 
const property = "name";
console.log(example[property]);  // Outputs: Dominik` 
  ```  

## Modifying Objects

-   **Adding or changing a property**:
    
```js
example.age = 30;  // Adds a new property 'age'
example.name = "Kotorożec";  // Changes the value of 'name'` 
```    
-   **Deleting a property**:
```js  
delete example.age;  // Removes the 'age' property` 
```