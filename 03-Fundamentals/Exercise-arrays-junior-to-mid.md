## Assignment 1: **Array Manipulation Basics**

**Objective:** Understand basic array operations: adding, removing elements, and iterating through arrays.

**Description:** You're tasked with creating a feature for a to-do list application. This feature should allow users to add new tasks, remove completed tasks, and display all current tasks.

**Requirements:**

1.  Create an array named `tasks`.
2.  Implement a function `addTask(task)` that adds a new task to the `tasks` array.
3.  Implement a function `removeTask(task)` that removes a task from the `tasks` array.
4.  Implement a function `displayTasks()` that logs all tasks in the `tasks` array to the console.

**Expected Outcome:** After adding and removing tasks, `displayTasks()` should accurately reflect the current state of the `tasks` array.


## Solution for: Array Manipulation Basics

```js

/**
 * Initializes a task management application.
 * 
 * @param {string[]} initialTasks - An array of initial tasks.
 * @returns An object containing functions to manage tasks: add a task, delete a task, and display all tasks.
 */
function initializeTaskManager(initialTasks) {
    // Creates a copy of the initial task list to ensure the original array is not modified.
    const tasks = [...initialTasks];
    
    /**
     * Adds a new task to the task list.
     * 
     * @param {string} task - The task to add.
     */
    function addTask(task) {
        tasks.push(task);
    }
    
    /**
     * Deletes a task from the task list. Logs the index of the task being deleted.
     * If the task is not found, no action is taken.
     * 
     * @param {string} task - The task to delete.
     */
    function deleteTask(task) {
        const indexToDelete = tasks.indexOf(task);
        console.log(indexToDelete);
        if (indexToDelete !== -1) {
            tasks.splice(indexToDelete, 1);
        }
    }
  
    /**
     * Displays the current list of tasks.
     */
    function showTasks() {
        tasks.forEach(task => console.log(task));
    }
  
    return {
        addTask,
        deleteTask,
        showTasks,
    };
} 

// Example usage:
const initialTasks = ["laundry", "drink water"]; // Define initial tasks.
const taskManager = initializeTaskManager(initialTasks); // Initialize the task manager with the initial tasks.

// Accessing task manager functions
const { addTask, deleteTask, showTasks } = taskManager;

// Testing the functionality
showTasks(); // Display initial tasks
addTask("walk with dog"); // Add a new task
showTasks(); // Display tasks after adding a new task
deleteTask("walk with dog"); // Delete a task
showTasks(); // Display tasks after deleting a task
addTask("water plants"); // Add another new task
showTasks(); // Display final list of tasks

```


## Assignment 2: **Working with Array Methods**

**Objective:** Leverage array methods such as `map`, `filter`, `reduce`, and `sort` to manipulate array data.

**Description:** Your project is a dashboard that displays information about sales transactions. You need to process an array of transactions to display summaries and insights.

**Requirements:**

1.  Given an array of transaction objects `transactions` (each transaction has `id`, `amount`, and `category`), write functions to do the following:
    -   Calculate the total sales amount.
    -   Find all transactions in a specific category.
    -   Sort transactions based on the amount (ascending).
2.  Use appropriate array methods (`map`, `filter`, `reduce`, `sort`) to implement these functionalities.

**Expected Outcome:** Functions that accurately process transactions to provide the total sales, transactions by category, and sorted transactions.

## Solution:

```js
/**
 * A list of sales transactions.
 * @type {Array<{id: number, amount: number, category: string}>}
 */

const transactions = [
  { id: 1, amount: 60, category: 'Food' },
  { id: 2, amount: 120, category: 'Electronics' },
  { id: 3, amount: 210, category: 'Electronics' },
  { id: 4, amount: 55, category: 'Food' },
  { id: 5, amount: 80, category: 'Clothing' },
  { id: 6, amount: 90, category: 'Clothing' },
  { id: 7, amount: 30, category: 'Food' },
];

**
 * Calculates the total sales from an array of transaction objects.
 * @param {Array<{amount: number}>} transactions - An array of transaction objects.
 * @returns {number} The total sales amount.
 */
function handleTotalSales(transactions) {
   const total = transactions
    .map(transaction => transaction.amount)
    .reduce((total, amount) => total + amount, 0);
   return total;
}

/**
 * Filters transactions by category.
 * @param {Array<{category: string}>} transactions - An array of transaction objects.
 * @param {string} category - The category to filter by.
 * @returns {Array<{id: number, amount: number, category: string}>} An array of transactions filtered by the specified category.
 */
function transactionsByCat(transactions, category) {
    return transactions.filter(transaction => transaction.category === category);
}

/**
 * Finds and summarizes transactions by a specific category.
 * @param {Array<{id: number, amount: number, category: string}>} transactions - An array of transaction objects.
 * @param {string} category - The category to search and summarize.
 * @returns {Object} An object containing summaries of transactions in the specified category.
 */
function findTransactionByCat(transactions, category) {
    const filteredTransactions = transactionsByCat(transactions, category);
    const sortedTransactions = [...filteredTransactions].sort((a, b) => a.amount - b.amount);

    return {
        totalAmount: handleTotalSales(filteredTransactions),
        count: filteredTransactions.length,
        lowestTransaction: `Lowest amount: ${sortedTransactions[0]?.amount} | ID: ${sortedTransactions[0]?.id}`,
        highestTransaction: `Highest amount: ${sortedTransactions[sortedTransactions.length - 1]?.amount} | ID: ${sortedTransactions[sortedTransactions.length - 1]?.id}`,
    };
}

// Example usage:
console.log(findTransactionByCat(transactions, "Food"));
```