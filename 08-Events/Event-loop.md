
## The event loop
To envision the event loop, imagine JavaScript is a butler that carries around a **todo-list**. This list contains everything you tell JavaScript to do.

Upon receiving this todo-list, JavaScript executes the tasks one by one, in the order you’ve listed.

Let’s say you give JavaScript six commands as follows:

```js
function addOne(n) {
  return n + 1
}

addOne(1) // 2
addOne(2) // 3
addOne(3) // 4
addOne(4) // 5
addOne(5) // 6
addOne(6) // 7
```

In addition to a todo-list, JavaScript also keeps a **waiting-list** where it tracks things it needs to wait for. If you tell JavaScript to order a pizza, it will call the pizza shop and adds “wait for pizza to arrive” in the waiting list. Meanwhile, it does other things that are already on the todo-list. 

So, imagine you have this code:
``` js
function orderPizza (flavor, callback) {
  callPizzaShop(`I want a ${flavor} pizza`)

  // Note: these three lines are pseudo code, not actual JavaScript
  whenPizzaComesBack {
    callback()
  }
}

function layTheTable () {
  console.log('The pizza is set for your consumption, master. Please stop playing and start eating.')
}

orderPizza('Hawaiian', layTheTable)
mopFloor()
ironClothes()
```

While executing `orderPizza`, JavaScript knows it needs to wait for the pizza to arrive. So, it adds “waiting for pizza to arrive” to its waiting list while it tackles the rest of its jobs.

When the pizza arrives, JavaScript gets notified by the doorbell and it makes a **mental note** to execute `layTheTable` when it’s done with the other chores.

Then, once it’s done with the other chores, JavaScript executes the callback function, `layTheTable`.

This system is called the Event Loop. You can substitute our butler analogy with actual keywords in the Event loop to understand everything:

-   **Todo-list** -> Call stack
-   **Waiting-list** -> Web apis
-   **Mental note** -> Event queue
