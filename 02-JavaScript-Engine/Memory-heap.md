
# What is the Memory Heap?

[](https://github.com/Chomikens/ZTM-JS/blob/0a-js-engine/memory-heap.md#what-is-the-memory-heap)

-   **Definition**: The memory heap is a large, mostly unstructured region of memory. Unlike the stack, which is organized and managed very strictly by the JavaScript engine, the heap is more like a disorganized storage area where objects are stored.
    
-   **Usage**: When your JavaScript code creates an object (anything from a simple object to arrays, functions, or even complex nested structures), it is stored in the heap. This is because objects can vary in size and structure, and their lifetime can be much longer and more unpredictable than the simple values stored on the stack.
    
-   **Dynamic Allocation**: Memory in the heap is dynamically allocated. This means that when objects are created, the JavaScript engine finds a spot in the heap to store them. This process is handled automatically, and you, as a developer or user, don't need to manually allocate or deallocate memory, unlike in some other programming languages.
    
-   **Garbage Collection**: Since the heap can become filled with objects that are no longer needed, JavaScript engines use a process called garbage collection to clean up. Garbage collection automatically finds objects that are no longer being used by your application and frees up their memory. This helps prevent your application from using more memory than it needs, which could slow down your computer or even cause it to crash.
