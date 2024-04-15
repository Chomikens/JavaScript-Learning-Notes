# Traversing downwards

There are three ways to traverse downwards:
 - querySelector or querySelectorAll
 - children
 - firstElementChild

## querySelector or querySelectorAll 

```html
<div class="component">
  <h2 class="component__title">Component title</h2>
</div>
```

```js
const component = document.querySelector('.component')
const title = component.querySelector('.component__title') // Here we grab it from component abouve

console.log(title) // <h2 class="component__title"> ... </h2>
```

## children 
children is a property that lets you select direct descendants (elements that are immediately nested in another element). It returns a [HTML Collection](https://github.com/Chomikens/ZTM-JS/blob/10-domSelectors/DOMselectors/selectors.md#html-collection) that updates when children elements are changed.


```html
<ul class="list">
  <li><a href="#">Link 1</a></li>
  <li><a href="#">Link 2</a></li>
  <li><a href="#">Link 3</a></li>
  <li><a href="#">Link 4</a></li>
  <li><a href="#">Link 5</a></li>
</ul>
```
```js
const list = document.querySelector('.list')
const listItems = list.children 

console.log(listItems)
```

## firstElementChild / children[index]
```js
const list = document.querySelector('.list')
const firstItem = list.firstElementChild // Grab first child 
constSecond = list.children[1]

```

# Traversing upwards

There are two ways to traverse upwards:
 - parentElement
 - closest


## parentElement 
parentElement is a property that lets you select the parent element. The parent element is the element that encloses the current element. In the following HTML, .list is the parent element of all <li>. Each <li> is the parent element of their respective <a>.

```html
<ul class="list">
  <li><a href="#">Link 1</a></li>
  <li><a href="#">Link 2</a></li>
  <li><a href="#">Link 3</a></li>
  <li><a href="#">Link 4</a></li>
  <li><a href="#">Link 5</a></li>
</ul>
```

```js
const firstListItem = document.querySelector('li')
const list = firstListItem.parentElement

console.log(list)
```

## closest() 
closest lets you select the closest ancestor element that matches a selector. 
**closest starts searching from the current element**, then proceeds upwards until it reaches the document. It stops and returns the first element it finds. 

**It not search nested elements**

```js
const firstLink = document.querySelector('a')
const firstLinkThroughClosest = firstLink.closest('li')

console.log(firstLinkThroughClosest)
```

# Traversing sideways

There are three ways to traverse sideways:
- nextElementSibling
- previousElementSibling
- Combining parentElement, children, and index


## nextElementSibling
You can select the next element with nextElementSibling.

```html
<ul class="list">
  <li><a href="#">Link 1</a></li>
  <li><a href="#">Link 2</a></li>
  <li><a href="#">Link 3</a></li>
  <li><a href="#">Link 4</a></li>
  <li><a href="#">Link 5</a></li>
</ul>
```

```js
const firstListItem = document.querySelector('li')
const secondListItem = firstListItem.nextElementSibling

console.log(secondListItem)
// <li><a href="#">Link 2</a></li>
```

## previousElementSibling
Likewise, you can select the previous element with previousElementSibling.

```js
const secondListItem = document.querySelectorAll('li')[1]
const firstListItem = secondListItem.previousElementSibling

console.log(firstListItem)
// <li><a href="#">Link 1</a></li>
```