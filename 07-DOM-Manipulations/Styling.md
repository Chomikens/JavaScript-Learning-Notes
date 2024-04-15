# Inline styling in JS 
To style inline in JavaScript you can use two methods: 

## Example HTML 
```html
<!-- For inline style -->
<h1 class="mainHeadingInlineStyle">Hey! I'm heading</h1>

<!-- Here we have custom css prop - but not defined in css file -->
<h2 class="mainHeadingSetProperty" style="var(--color)">Hey! I'm another heading</h2>

<!-- For inline style -->
<h3 class="getComputed">Hey! I'm heading with computed style</h3>
```

```css
.mainHeadingSetProperty {
    /*  Here we have only fallback for our custom prop so now its color it: #fff;*/
    /* Imagine that we want to change it color only in one special condition */
    color:var(--color, #fff)
}

.getComputed {
    color:#e3e3e3;
    font-size:clamp(1.5rem, 2vh, 2.5rem)
}
```

- ## element.style 
To style inline in JS we can set element.style(style is an object).[properties] 
### Example 
```js
// Let grab our h1. 

const mainHeading = document.querySelector('.mainHeadingInlineStyle')

// If we have properties thah is two words we write it using camelCase
mainHeading.style.backgroundColor = "#e3e3e3"
```
- ## element.setProperty('name of property - also custom variable', value) 

The setProperty method is used on the style property of a DOM element. This method is useful for setting both standard CSS properties and custom CSS properties (CSS variables).

### Example 

```js
// Let grab our h2. 

const mainHeadingSetProperty = document.querySelector('.mainHeadingSetProperty')

// If we have properties thah is two words we write it using camelCase
mainHeading.style.setProperty("--color", "red") // or we can just set color to red like below: 
mainHeading.style.setProperty("color", "blue")
```

 - ## getComputedStyle(element, pseudoelement(this is optional)). 
    - Element.style is setters and also getters - you gen get and set a value using this.
    - Element.setProperty is a an setters - you can set something using this. 
    - getComputedStyle() - is a getter. You can only read element using this method. 

 ```js
// Let's grab our h3 
const getComputed = document.querySelector('.getComputed');
const stylesOfHeading3 = getComputedStyle(getComputed).getPropertyValue('color');
 
 ```   
