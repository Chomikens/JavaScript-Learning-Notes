# Default Behaviors
Some elements trigger actions by default. For example:
- When you click on a link, browsers will navigate to the address indicated with `href`.
- When you click on a checkbox, browsers check or uncheck the checkbox.
- When you click on a submit button on a form, browsers trigger the `submit event` and redirect you to the page indicated by the action `attribute`.

## Preventing default actions
Sometimes, you want to prevent these default behaviors. You’ll see why and when you’d do so as we build components. For now, learn how to prevent it. To prevent default behaviors, you can use the `preventDefault` method.

```js
Element.addEventListener('click', evt => evt.preventDefault())
```
When the default action is prevented, browsers automatically set the defaultPrevented property to true.

```js
Element.addEventListener('click', evt => {
  evt.preventDefault()
  console.log(evt.defaultPrevented) // true
})
```