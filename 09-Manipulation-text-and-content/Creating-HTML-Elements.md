
# Creating HTML Elements

You need to create elements with `createElement` before you can add them to the DOM.

## createElement

`createElement` takes in one value—the tag of the element you want to create.

```js
const paragraph = document.createElement('p')
const div = document.createElement('div')
```

You can change your element’s contents and attributes after creating it.

```
paragraph.classList.add('red')
paragraph.textContent = `I'm red!`
```

## Adding elements to the DOM

You can use two methods to add elements to the DOM:

1.  `appendChild`
2.  `insertBefore`

### appendChild

`appendChild` adds your element as the final child of the specified element. It takes in one argument—the element you want to append.

```js
parentElement.appendChild(newElement)
```

Let’s see it in action. Say you have the following HTML.

```html
<ol>
  <li>Banana</li>
  <li>Pineapple</li>
  <li>Orange</li>
</ol>
```

You want to add another item, Strawberry, to the end of the list. Here’s how you’d do it with `appendChild`.

```js
// Create Strawberry
const li = document.createElement('li')
li.textContent = 'Strawberry'

// Append Strawberry
const list = document.querySelector('ol')
list.appendChild(li)
```

Here’s the result:

```html
<ol>
  <li>Banana</li>
  <li>Pineapple</li>
  <li>Orange</li>
  <li>Strawberry</li>
</ol>
```

`appendChild` has a wonky behavior—if the element you want to append already exists in your DOM, `appendChild` moves the element from its existing location to the new location you specified.

```html
<ol class="fruits-i-like">
  <li>Banana</li>
  <li>Pineapple</li>
  <li>Orange</li>
</ol>

<ol class="fruits-i-dont-like">
  <li>Strawberry</li>
</ol>
```

```js
const orange = document.querySelectorAll('li')[2]
const dontLike = document.querySelector('.fruits-i-dont-like')
dontLike.appendChild(orange)
```

The result is:

```html
<ol class="fruits-i-like">
  <li>Banana</li>
  <li>Pineapple</li>
</ol>

<ol class="fruits-i-dont-like">
  <li>Strawberry</li>
  <li>Orange</li>
</ol>
```

Don’t use `appendChild` to move elements because you wouldn’t expect this behavior. If you want to move an element, delete it before moving it. Be explicit.


### insertBefore

`insertBefore` adds an element before another element. It has the following syntax:

```js
parentElement.insertBefore(newElement, referenceElement)
```

-   `newElement` is the element you want to insert.
-   `referenceElement` tells browsers where to insert `newElement`. `newElement` will be inserted just before `referenceElement`.

Let’s see this in action. Say you have the following HTML:

```html
<ol>
  <li>Banana</li>
  <li>Pineapple</li>
  <li>Orange</li>
</ol>
```

If you want to insert Strawberry as the first list item, you need to set Banana as your `referenceElement`.

```js
// Create strawberry node
const strawberry = document.createElement('li')
strawberry.textContent = 'Strawberry'

// Add strawberry node before banana
const list = document.querySelector('ol')
const banana = list.children[0]
list.insertBefore(strawberry, banana)
```

The result will be:

```html
<ol>
  <li>Strawberry</li>
  <li>Banana</li>
  <li>Pineapple</li>
  <li>Orange</li>
</ol>
```
