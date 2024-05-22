# Module

Before modules to dont pollute global name spaces we have some tricks to have moduls. 

## Reval Modul Pattern using IIFE 

Because it IIFE ands Closure we dont have access to fight (in case if we have another fight method.) Now we have modulefirst.fight()
```js
const modulefirst = (function () {
    function fight(char1, char2) {
        const attack1 = Math.floor(Math.random()*char1.length)
        const attack2 = Math.floor(Math.random()*char2.length)

        return attack1 > attack2 
        ? `${char1} wins` 
        : `${char2} wins` 
    }
    return {
        fight,
    }
})()

```

## Whats a problem with this? 
We still pollute global name space - we still can rewite something. So order of script was imporatant;