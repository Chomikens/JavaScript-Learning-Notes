# Events 
Events tell you that something has happened in JavaScript. For example, if a user clicks on something, a click `event` fires. If the user hits a key on their keyboard, the `keydown` and `keyup` events are fired.

## Listening for events 
You need event listeners to listen to events. You can add event listeners to any element in the DOM like this:

```js
Element.addEventListener('event-name', function () {}) 
```

### Example 
Let’s say you want to listen for a click event on a <button> element. To do so, you add the click event listener to the button.

```js
const button = document.querySelector('button')

button.addEventListener('click', function () {
  // Do something here
})
``` 

Next, you want to make sure your event listener works. To do so, you can do a console.log statement.

```js
const button = document.querySelector('button')

button.addEventListener('click', function () {
  console.log('Button is clicked')
})
```

## The event object

All event listener callbacks accept an argument. This argument is the `event` object. People usually abbreviate it either to `evt` or` e`.