
# Look at code below - what will happend? 

```js
function callMeMaybe () {
    const calling = `London is calling`; 

    return setTimeOut( function() {
        console.log(calling)
    }, 4000)
}

```

What will appear when we change location of calling variable? 

```js
function callMeMaybe () {

    return setTimeOut( function() {
        console.log(calling)
    }, 4000)

    const calling = `London is calling`; 
}

callMeMaybe ()

```

Nothing! Becouse first we invoke callMeMaybe. Then due to setTimeout the callback function will add to WEB APIS Event Loop and wait there. Then rest of callMeMaybe funcion will execute so at this moment JS knew calling variable. 

## Function calling once

Imagine you have function that will be invoke only once when page is loaded. Knowing what you know use closure to achive this. 

```js
const initialize = () => {
    let called = 0

    return function () {
        if( called > 0) {
            return "Nothing happend"
        } else {
            
            called++
            return "Page is loaded once"
        }
    }
}

const onceFunc = initialize()

console.log(onceFunc()) // Page is loaded once
console.log(onceFunc()) // Nothing happend
console.log(onceFunc()) // Nothing happend
console.log(onceFunc()) // Nothing happend

```