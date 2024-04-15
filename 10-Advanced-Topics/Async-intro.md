


# Preventing blocking operations in asynchronous code

Synchronous code is code that executes in a top to bottom, left to right manner, sequentially, waiting until one code has finished before the next line begins. So far, you’ve written synchronous code for every lesson prior to this one.

Asynchronous code is code that doesn’t follow the top to bottom, left to right manner. An example of asynchronous code is an event listener.

Consider this click event. Why is it asynchronous? Because the callback doesn’t get executed until a user clicks on a button!

## Asynchronous code is critical in JavaScript

Imagine you have a robot helper, Mr. Robot, that can only do one thing at a time. If you tell Mr. Robot to order pizza, it picks up, dials the pizza hotline, orders pizza, and waits at the front door until the pizza arrives.

“Sweep the floor! Clean up the dishes in the kitchen sink! Wash the toilet!”, you shout at Mr. Robot. But Mr. Robot doesn’t respond. It continues to sit quietly at the front door.

When the pizza arrives, Mr. Robot passes you the pizza and continue with the rest of the chores—sweep floor, clean dishes and wash toilet, in the order you mentioned.

JavaScript is like Mr. Robot. It can only do one thing at a time. It cannot do anything else in the meantime, until the one thing gets completed. This behavior is called **single threading**.

If you ask JavaScript to do something else in the meantime, it doesn’t respond. This behavior is called **blocking**. To see blocking operations in action, run the following JavaScript:

```js

while (true) {
  console.log('stuck')
}

console.log('This log never happens')
```

Let me explain what happened.

The code above uses a while block (you’ll rarely use a while block when you code for real, so don’t bother about remembering it. I use it here because it’s perfect for explaining a blocking operation).

A while block executes code in curly braces if a condition remains true (kind of like an if/else statement). In this example, the condition always remains true, so the while block keeps logging stuck in the console.

In this case, JavaScript is like Mr. Robot. It hasn’t finished waiting for the pizza to arrive. The unfortunate thing is, the pizza will never arrive…

Imagine this.

Let’s say you have a event listener that blocks operations, and you used this listener to listen for click on the button. If you do this, JavaScript stares and waits till a user clicks on the button—that may never happen—before doing anything else… You can imagine the horror, so I’d leave you with the details.

See where it goes? That’s why asynchronous programming is such a big thing in JavaScript. That’s why we use callbacks.

Asynchronous operations is a really important concept to understand in JavaScript. To make it clearer, let’s take some time to dig deeper into the underlying mechanics—the event loop.