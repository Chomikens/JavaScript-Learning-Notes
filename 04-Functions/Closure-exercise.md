
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