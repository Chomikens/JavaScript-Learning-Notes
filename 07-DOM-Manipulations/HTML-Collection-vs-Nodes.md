## HTML Collection
An HTMLCollection in the HTML DOM is live; it is **automatically** updated when the underlying document is changed. For this reason it is a good idea to make a copy (e.g., using **Array.from**) to iterate over if adding, moving, or removing nodes.

### Methods:
- To iterate we can use:
    - [`for of`](https://github.com/Chomikens/ZTM-JS/blob/9-loops/loops.md#for-of-es-6)
    - Array.from and then array methods for example [forEach](https://github.com/Chomikens/ZTM-JS/blob/9-loops/loops.md#for-of-es-6)

## NodeList

NodeLists can contain any type of Node and are available in two varieties: live and static. Generally, it is static (e.g., returned by `document.querySelectorAll()`), where DOM changes do not affect the collection's content.

### Methods:
- To iterate we can use:
    - [`for of`](https://github.com/Chomikens/ZTM-JS/blob/9-loops/loops.md#for-of-es-6)
    - Build-in method [forEach](https://github.com/Chomikens/ZTM-JS/blob/9-loops/loops.md#for-of-es-6)
    - For rest array method make it from it array.


