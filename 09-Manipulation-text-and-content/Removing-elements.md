
# Removing Elements from the DOM 

You can remove an element with `parentNode.removeChild`.

Let’s see it in action. Say you want to remove Jen Simmons from the list below.

```html
<ol>
  <li>Rachel Andrew</li>
  <li>Jen Simmons</li>
  <li>Una Kravets</li>
</ol>
```

You’ll first get Jen with `querySelector`, then remove it with `removeChild`.

```js
const jen = document.querySelectorAll('li')[1]
jen.parentNode.removeChild(jen)
```

The result is:

```html
<ol>
  <li>Rachel Andrew</li>
  <li>Una Kravets</li>
</ol>
```

## Moving the HTML element

`removeChild` returns the Element you removed. You then use `appendChild` or `insertBefore` to move the element.

Let’s say you want to move Jen from the second position to the first position in the following HTML.

```html
<ol>
  <li>Rachel Andrew</li>
  <li>Jen Simmons</li>
  <li>Una Kravets</li>
</ol>
```

To do so, you need to get `jen` with `removeChild`, then add `jen` back into the list with `insertBefore`.

```js
const list = document.querySelector('ol')
const rachel = list.children[0]

const jen = list.removeChild(list.children[1])
list.insertBefore(jen, rachel)
```

The result is:

```html
<ol>
  <li>Jen Simmons</li>
  <li>Rachel Andrew</li>
  <li>Una Kravets</li>
</ol>
```
