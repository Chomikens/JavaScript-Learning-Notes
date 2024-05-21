# For await of 

## Without For await of

```js
const urls = [
  'https://jsonplaceholder.typicode.com/todos/1', 
  'https://jsonplaceholder.typicode.com/todos/2',
  'https://jsonplaceholder.typicode.com/todos/3',
  'https://jsonplaceholder.typicode.com/todos/4'
]


const getData = async function (urlsArray) {
   
   try { 
    if(!urlsArray) await Promise.reject(new Error ('Pass an argument for function'))
     const data = await Promise.all(urlsArray.map(async  url => {
     const response =  await fetch(url);
     if(!response.ok) await Promise.reject(new Error('Unable to fetch the data'))
     const data = await response.json()
     return data
        }))
        return data;
   }
   catch(error) {
    console.error(error.message)
   }
} 

async function fetchAndLogData() {
    const dataN = await getData(urls);
    console.log(dataN);  // Logs the actual data after it's fetched
}

fetchAndLogData();

```

## For await of 

```js
const urls = [
  'https://jsonplaceholder.typicode.com/todos/1', 
  'https://jsonplaceholder.typicode.com/todos/2',
  'https://jsonplaceholder.typicode.com/todos/3',
  'https://jsonplaceholder.typicode.com/todos/4'
];

const getDataForOf = async function() {
  const arrayOfPromises = urls.map(url => fetch(url));
  const results = [];
  for await (let request of arrayOfPromises) {
    const data = await request.json();
    results.push(data);  // Collect the data in an array
    console.log(data.title);
  }
  return results;  // Return the collected data
};

async function fetchAndLogData() {
  const dataN = await getDataForOf();
  console.log(dataN);  // Logs the actual data after it's fetched
}

fetchAndLogData();
```