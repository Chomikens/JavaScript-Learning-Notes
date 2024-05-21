# Parallel, Sequence and Race

Important things with multiply promises is to decide how to manage this. 


## Example function that create promise with delay

```js 
const promisify = (item, delay) =>
  new Promise((resolve) =>
    setTimeout(() =>
      resolve(item), delay));

const a = () => promisify('a', 100);
const b = () => promisify('b', 5000);
const c = () => promisify('c', 3000);


```

## Parallel - all on the same time 

```js
async function parallel() {
  const promises = [a(), b(), c()];
  const [output1, output2, output3] = await Promise.all(promises);
  return `prallel is done: ${output1} ${output2} ${output3}`

  parallel().then(console.log)
}
```

## Sequence  - if first succes then second 


```js

async function sequence() {
  const output1 = await a();
  const output2 = await b();
  const output3 = await c();
  return `sequence is done ${output1} ${output2} ${output3}`
sequence().then(console.log)
}

```

## Race - call all but when first is resolve ignore rest. 

```js
async function race() {
  const promises = [a(), b(), c()];
  const output1 = await Promise.race(promises);
  return `race is done: ${output1}`;

}

race().then(console.log)

```