# Event propagation

 Three phases occur when an event is fired:

- The `capturing` phase
- The `target` phase
- The `bubbling` phase

Together, they’re called `event propagation`.

## Checking phase 
To check phase use `e.eventPhase`


## The capturing phase

Here, JavaScript goes through window, document, followed by every element until it reaches the event target.

![capturing phase ](https://javascript.info/article/bubbling-and-capturing/eventflow.svg  "capturing phase")
[Source: Modern JavaScript](https://javascript.info/)

Event listeners can listen to the capturing phase if you provide it with a third argument, `useCapture`, which is a boolean / option object.
```js
addEventListener(type, listener, {options})
addEventListener(type, listener, useCapture)
```
If `useCapture` is `true`, the callback will be called in the capturing phase. If `useCapture` is `false`, the callback will not be called in the capturing phase.

## The target phase
The target phase comes next. Here, JavaScript reaches the element that fired the event and triggers all event listeners attached to it. The target phase disregards the `useCapture` flag.

## The bubbling phase
The bubbling phase comes last. Here, JavaScript goes through every HTML Element, starting from the target, back to `Window`.

Event listeners without the `useCapture` flag will trigger in this phase.

### Events that bubble
Events that bubble have a `bubbles` property set to `true`. An example is a `click` event:

### Preventing bubbling
If you want to prevent an event from bubbling, you can use `stopPropagation` or `stopImmediatePropagation`.
-   `stopPropagation` prevents events from bubbling upwards
-   `stopImmediatePropagation` prevents events from bubbling upwards, and also prevents subsequent events on the listening element from firing.
