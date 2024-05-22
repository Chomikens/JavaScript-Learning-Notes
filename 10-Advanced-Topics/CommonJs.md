# CommonJs and AMD
It' will create for Node.js and it's still use it. For server and aplications. But it's not ideal for browsers. 

## Importing 
```js
const module1 = require('module1')
const module2 = require('module1')

```

## Exporting 

```js
function fight () {
    console.log('Elo')
}

module.export = {
    fight:fight
}

```

## AMD 
AMD was created for browsers and it load script async. 

```js
define(['module1', 'module2']

function(module1Import, module2Import) {
    var module1 = module1Import
    var module2 = module2Import

    function dance() {

    }
    return {
        dance:dance,
    }
}

)
```