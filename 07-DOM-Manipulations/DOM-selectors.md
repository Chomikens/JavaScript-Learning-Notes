# DOM selectors 

- ## `getElementsByTagName('tagname')`
    - Return: [HTML Collection](https://github.com/Chomikens/ZTM-JS/blob/10-domSelectors/DOMselectors/selectors.md#html-collection)
    - Example: 
```js
 const paragraph = document.getElementsByTagName('p')
```

- ## `getElementsByClassName('classname')`
    - Return: HTML Collection
    - Example: 
 ```js
 const paragraph = document.getElementsByClassName('is-active')
 ```

 - ## `getElementById('id')`
    - Return: Single Element Object
    - Example: 
 ```js
 const paragraph = document.getElementById('intro')
 ```

 - ## `querySelector('.class #id tag')`
    - Return: first Element within the document that matches the specified selector, or group of selectors. If no matches are found, `null` is returned. 
    - Complex selectos: Yes, but why :P? 
    - Example: 
 ```js
 const paragraph = document.querySelector('p.class')
 ```


 - ## `querySelectorAll('.class #id tag')`
    - Return: [NodeList](https://github.com/Chomikens/ZTM-JS/blob/10-domSelectors/DOMselectors/selectors.md#nodelist)
    - Complex selectos: Yes, but why :P? 
    - Example: 
 ```js
 const paragraph = document.querySelectorAll('p.class')
 ```


