
# Event delegation
The event delegation pattern makes use of event propagation. It works like this:

1.  you attach one event listener to an ancestor element
2.  ancestor element listens to all events in descendant elements

**Note**: the event delegation pattern only works for events that bubble.

```html
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
  <li>Item 4</li>
  <li>Item 5</li>
</ul>
```
```js
const list = document.querySelector('ul')
list.addEventListener('click', e => {
  // Do something when list is clicked on
})
```

## Determining the event target
The element that fires the event is called the **event target**. It can be found with the `target` property.

## Avoid misfires
The event delegation pattern is sensitive to all events fired from the listening element onwards. In this case, you can also fire the callback when you click on the list itself.

To prevent such misfires from happening, we need to check if the target element matches the element we’re looking for. We can do so with the `matches` method.

### Matches 

`matches` checks if the element matches the selector we provided. You should be familiar with it’s syntax.

```js
list.addEventListener('click', e => {
  if (e.target.matches('li')) {
    // Do something
  }
})
```

### Nested elements 
Let’s say you want to listen to a click event on a `<button>`. This button has an SVG and some text embedded in it.

```html
<button>
  <svg><!-- Gear icon --></svg>
  <span>Click me!</span>
</button>
```

```js
const button = document.querySelector('button')
button.addEventListener('click', e => {
  console.log(e.target)
})
```

When we click on the gear icon, the SVG shows up in the console. that’s because the `event.target` (which was the clicked element) is the SVG itself. Ditto for the text.

Most of the time, we’re not looking for the SVG or the text. We’re looking for the `button` element instead. There are two methods to always ensure we get the `button` element.

-   Set `pointer-events` to `none`
-  Use `closest`

#### Pointer events

`pointer-events` is a CSS property that determines how an element respond to mouse events. (`click` is a mouse event). If you set `pointer-events` of an element to `none`, it will not respond to mouse events.

In this case, we can set `pointer-events` of all descendant elements to `none`. We can do this with the following CSS:

```css
button * {
  pointer-events: none;
}
```

### Closest
`closest` searches the DOM upwards for an element that matches the selector. This search includes the element itself.
-   If it finds an element that matches the selector, it returns the element.
-   If it doesn’t find any elements, it returns `undefined`
- 
If search for `button`, we can ensure we work with the button element even though the user clicked on the SVG (or text).

```js
button.addEventListener('click', e => {
  const button = event.target.closest('button')
  if (button) {
    // Activates when user clicked any element within `button`
  }
})
```
