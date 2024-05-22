
# ES6 Modules

## Exporting

In ES6, you can export functions, objects, or primitives from a module to make them available for import in other modules. There are two types of exports: named exports and default exports.

### Named Exports

Named exports allow you to export multiple values. You must use the same name when importing.

```js
// Exporting named functions
export function sayHello() {
    console.log('Hello');
}

export function sayHello2() {
    console.log('Hello2');
}
```

### Default Export

A module can have one default export. Default exports are useful for exporting a single value or a fallback value for your module.


```js 
// Exporting a default function
export default function sayGoodbye() {
    console.log('Goodbye');
}

// Exporting a default object
export default {
    name: 'defaultExportObject',
    value: 42
};
```

## Importing

You can import values from other modules using the `import` statement. There are different ways to import named and default exports.

### Importing Named Exports

To import named exports, you use the curly braces `{}` to specify the names of the exports you want to import.


```js
import { sayHello, sayHello2 } from './source.js';

// Using the imported functions
sayHello();  // Output: Hello
sayHello2(); // Output: Hello2
```

### Importing the Default Export

To import a default export, you can give it any name you like.


```js 
import sayGoodbye from './source.js';

// Using the imported default function
sayGoodbye(); // Output: Goodbye

// Importing a default object
import defaultExportObject from './source.js';

console.log(defaultExportObject.name); // Output: defaultExportObject
console.log(defaultExportObject.value); // Output: 42
```

## Script Type Module

When using ES6 modules in an HTML file, you need to set the `type` attribute of the `<script>` tag to `"module"`.

```html

`<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ES6 Modules</title>
</head>
<body>
    <script type="module" src="main.js"></script>
</body>
</html>
```

By specifying `type="module"`, the browser treats the script as an ES6 module, enabling support for `import` and `export` statements.
