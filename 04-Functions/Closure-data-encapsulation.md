# Closure data encapsultion 

Imagine we have a function but we dont want to get user access to all of it - how to achive it? 

```js
const makeNuclearButton = () => {
    let timeWithOutDesctuction = 0;


    const passTime = () => timeWithOutDesctuction++
    const totalPeaceTime = () => timeWithOutDesctuction
    const launch = () => {
        timeWithOutDesctuction = -1
        return 'Kaboom'
    }

    const countingInterval = setInterval(passTime, 1000)
    return {
        totalPeaceTime,
        kaboom: launch,
    }
}

const hitButton = makeNuclearButton()

// Now we can active some function thaht returns

```

