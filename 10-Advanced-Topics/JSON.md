# JSON

When exchanging data between a browser and a server, we can only exchange text. Therefore, we cannot send JavaScript objects directly to the server like this:

```js
const objectToSend = {
    name: "Kotorozec",
    age: 34,
};
```

## How to Send Data?
JSON (JavaScript Object Notation) is a standard format for sending and receiving data. It is text written in the notation of JavaScript objects.

JavaScript provides built-in methods for working with JSON:

- `JSON.stringify(object)` - Converts a JavaScript object into a JSON string.
- `JSON.parse(JSON_string)` - Parses a JSON string and returns a JavaScript object.

## Example
```js

const objectToSend = {
    name: "Kotorozec",
    age: 34,
};

const jsonString = JSON.stringify(objectToSend);
console.log(jsonString); // Output: '{"name":"Kotorozec","age":34}'

```

The JSON string can be sent to the server, and the server can parse it back into an object:

```js
const receivedJson = '{"name":"Kotorozec","age":34}';
const parsedObject = JSON.parse(receivedJson);
console.log(parsedObject); // Output: { name: "Kotorozec", age: 34 }

```