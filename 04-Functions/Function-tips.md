# Carefull with those: 

- Avoid initialize function inside loop. Write in outside and call on the loop. 

```js

function exampleFunc(i) {
    console.log(`Hi nr ${i}`)
}
for (let i = 0; i <5 ; i ++) {
        exampleFunc(i)
}
```

