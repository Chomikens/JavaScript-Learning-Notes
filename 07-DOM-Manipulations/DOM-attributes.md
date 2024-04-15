# DOM attributes 

## Example HTML 

```html
<input type="checkbox" id="scales" name="default" checked />
<input type="checkbox" id="scales1" name="defaultFalse" checked="false" />
<input type="checkbox" id="scales2" name="defaultFalse" checked="true" />
<p class="customP" data-customP="true">Lorem</p>

```
## Introduction do attributes

### HTML attributes dafault behavior 
In HTML, certain attributes like checked, disabled, readonly, etc., are called boolean attributes. The presence of a boolean attribute on an element represents the true value, and the absence of the attribute represents the false value.

For boolean attributes, any value assigned to them, including the strings "true" or "false", is irrelevant. It's the presence or absence of the attribute that matters.

In your examples, the first and second `<input>` elements will be checked because they have the checked attribute present. The checked="false" on the second input does not make it unchecked; it's still considered checked because the checked attribute is present. The third `<input>` will also be checked for the same reason.

### customP attributes 
As you see in our example we can also set customP attributes to element. 


## Get/Set/Remove attributes from DOM

 - ### Get attributes customP and default
To get attributes from DOM we can use `getAttribute('name-of-atributes')`

```js
//Get element 
const customP = document.querySelector('.customP') // Get element by class 
customP.getAttribute('data-customP')
```

 - ### Get only customP attributes 
To get customP attributes from DOM we can use `element.dataset.nameOfAttribute`

```js
//Get element 
const customP = document.querySelector('.customP') // Get element by class 
customP.dataset.customP // Look that here we dont include data before name 
```

- ### Set attributes customP and default
To set attributes from DOM we can use `setAttribute('name-of-atributes', 'value')`

```js
//Get element 
const customP = document.querySelector('.customP') // Get element by class 
customP.setAttribute('data-customP-new', true)
customP.setAttribute('checked', true)
```

- ### Set only customP attributes 
To set customP attributes from DOM we can use `element.dataset.nameOfAttribute`

```js
//Get element 
const customP = document.querySelector('.customP') // Get element by class 
customP.dataset.customPCammelCase = true;
```

### Remove attributes customP and default
To remove attributes from DOM we can use `element.removeAttribute('name-of-atrribute')`