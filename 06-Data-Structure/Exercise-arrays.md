# Exercise on arrays 

```js
/**
 * Array representing a group of people, where each person is an object with properties for their name, age, and a list of their favorite books.
 * @type {Array.<{name: string, age: number, favoriteBooks: Array.<string>}>}
 */
const people = [
    { name: "Alice", age: 25, favoriteBooks: ["The Hobbit", "Catcher in the Rye"] },
    { name: "Bob", age: 30, favoriteBooks: ["1984", "Brave New World", "Slaughterhouse-Five"] },
    { name: "Carol", age: 27, favoriteBooks: ["War and Peace"] },
    { name: "Dave", age: 22, favoriteBooks: ["The Great Gatsby", "To Kill a Mockingbird"] }
];
```

## Exercise 1
 - Young Readers: Find all people under the age of 30 who have more than 1 favorite book. Return an array of their names.
 - Book Recommendations: Create a function that takes a book name as an argument and returns an array of names of people who have that book as a favorite. If no one has it as a favorite, return an empty array.
 - Age Sorting: Sort the array people by age in ascending order without altering the original array. Display the sorted array.
 - Favorite Books Flat List: Create a single array that contains every favoriteBooks entry from all people, without any duplicates. Sort this list alphabetically.

## Solutions 1
 - Young Readers: Find all people under the age of 30 who have more than 1 favorite book. Return an array of their names.

```js
/**
 * Finds young people (under 30 years old) from a given array who have more than one favorite book.
 * @param {Array.<{name: string, age: number, favoriteBooks: Array.<string>}>} arr - The array of people to search through.
 * @returns {Array.<string>} An array of names of the young people who have more than one favorite book.
 */
function findYounPeople (arr) {
  const youngWhoReads = arr.filter(el => el.age < 30 && el.favoriteBooks.length > 1).map(el=>el.name)
  return youngWhoReads 
}

```

- Book Recommendations: Create a function that takes a book name as an argument and returns an array of names of people who have that book as a favorite. If no one has it as a favorite, return an empty array.

```js
/**
 * function that takes a book name as an argument and returns an array of names of people who have that book as a favorite
 * @param {string} nameOfBook - name of searching book, 
 * @param {Array.<{name: string, age: number, favoriteBooks: Array.<string>}>} arr - The array of people to search through.
   @returns {Array.<string>} An array of names that also has this books in favorite.
 */ 

function favoriteBook (nameOfBook, arr) {
    if (typeof nameOfBook !== 'string' || nameOfBook.length === 0) {
        console.log('Please write name of book')
        return [] // Return an empty array if the input is invalid.
        }
        const favoriteBooksPeople = arr
        .filter((el) => el.favoriteBooks.includes(nameOfBook))
        .map(el =>el.name)
        return favoriteBooksPeople
}

console.log(favoriteBook(["1984"], people))
```

- Age Sorting: Sort the array people by age in ascending order without altering the original array. Display the sorted array. 
```js
/**
 * * Sorts an array of people by their age in ascending order without altering the original array.
 * * @param {Person[]} arr - The array of people to sort.
 * @returns {Person[]} A new array sorted by age in ascending order.
 */

function handleAgeSort(arr) {
    const ascendingAge = arr.map(el => el.age).sort((prevAge, nextAge) => {
        return prevAge - nextAge
    })
    return ascendingAge
}

 console.log(handleAgeSort(people))
```

- 

```js
/**
 * Extracts a unique, sorted list of favorite books from an array of people.
 * Each person object in the input array should have a 'favoriteBooks' property that is an array of strings.
 * The function combines all favorite books into a single array, removes duplicates, and sorts the result alphabetically.
 * 
 * @param {Object[]} arr - An array of objects, where each object represents a person and has a 'favoriteBooks' property containing an array of book titles.
 * @returns {string[]} A sorted array of unique book titles found in the input array.
 */
function favoriteBooksUnique(arr) {
    const uniqueBooks = arr
        .map(el => el.favoriteBooks) // Extract the 'favoriteBooks' array from each person object.
        .flat() // Flatten the array of arrays into a single array of books.
        .sort() // Sort the books alphabetically.
        .filter((el, index, arr) =>  el !== arr[index - 1]); // Remove duplicates by filtering out books that are the same as the previous book in the sorted list.

    return uniqueBooks; // Return the array of unique, sorted book titles.
}

// Example usage:
const uniqueBooks = favoriteBooksUnique(peopleDubles);
console.log(uniqueBooks);
```

## Exercise 2:  Chaining Array Methods

Goal: Given an array of integers, create a new array that contains the square of each integer, but only if the original integer was even. Finally, sort the new array in ascending order.

Input: [1, 4, 2, 3, 5, 8, 6]
Output: [4, 16, 36, 64]

## Solution 

```js
/**
 * Processes an array of integers, returning a new array that contains the square of each even integer,
 * sorted in ascending order.
 * 
 * @param {number[]} arr - An array of integers to be processed.
 * @returns {number[]} A new array containing the squares of the even integers from the input array,
 * sorted in ascending order.
 */
function squareWhenEven(arr) {
  const sortedSquare = arr
    .filter(el => el % 2 === 0) // Filter out odd numbers.
    .map(el => el ** 2) // Square each remaining (even) number.
    .sort((a, b) => a - b); // Sort the squared numbers in ascending order.
  
  return sortedSquare;
}

console.log(squareWhenEven([1, 4, 2, 3, 5, 8, 6])); // Example usage.
```

## Exercise 3:  Complex Mapping and Filtering
You have an array of orders. Each order is an object with properties customerName, amount, and delivered (boolean). Return a new array containing strings formatted as "{customerName} owes {amount}" but only for orders that haven't been delivered yet.

## Solution 
```js
/**
 * Processes an array of order objects, returning an array of strings for orders not yet delivered.
 * Each string contains the customer's name and the amount they owe, formatted for easy reading.
 *
 * @param {Object[]} arr - An array of order objects to be processed. Each object should have a `customerName`
 * string, an `amount` number, and a `delivered` boolean.
 * @returns {string[]} An array of strings, each representing an undelivered order in the format:
 * "<customerName> owes <amount>". Only orders where `delivered` is false are included.
 */
function handleOrderNotDeliver(arr) {
    const taskToDo = arr
        .filter(el => el.delivered === false) // Select only orders that have not been delivered.
        .map(el => `${el.customerName} owes ${el.amount}`); // Format the message for each.
    return taskToDo;
}

// Example usage
const data = [
  { customerName: "John", amount: 250, delivered: true },
  { customerName: "Sarah", amount: 150, delivered: false },
  { customerName: "Dave", amount: 300, delivered: false }
];
console.log(handleOrderNotDeliver(data)); // Logs: ["Sarah owes 150", "Dave owes 300"]
```

## Exercise 4:  Complex Mapping and Filtering
Goal: Given an array of numbers, find the sum of all even numbers that are greater than 10.
Input: [5, 20, 15, 8, 30, 12]
Output: 62 (20 + 30 + 12)

## Solution 
```js
/**
 * Calculates the sum of all even numbers in an array that are greater than 10.
 * This function iterates over the array to filter out numbers that are either odd
 * or less than or equal to 10. It then sums up the remaining numbers using the
 * reduce method.
 *
 * @param {number[]} arr - An array of numbers to be processed.
 * @returns {number} The sum of all even numbers in the array that are greater than 10.
 */
function handleSumOfEven(arr) {
    const evenSum = arr
        .filter(el => el % 2 === 0 && el > 10) // Filter for even numbers greater than 10.
        .reduce((acc, next) => acc + next, 0); // Sum up the filtered numbers.
    return evenSum;
}

// Example usage
const data = [5, 20, 15, 8, 30, 12];
console.log(handleSumOfEven(data)); // Output: 62
```

## Exercise 5:  Exercise 4: Working with Two Arrays (Intersection)
Goal: Given two arrays of numbers, find the numbers that are present in both arrays. Return the intersection of these arrays sorted in ascending order.

Input:
Array 1: [1, 2, 3, 4, 5]
Array 2: [0, 2, 4, 6, 8]
Output: [2, 4]


## Solution

```js
/**
 * Finds the intersection of two arrays of numbers, returning a new array containing
 * numbers that are present in both input arrays. The resulting array is sorted in ascending order,
 * though this specific implementation relies on the input arrays being pre-sorted for accurate sorting in the output.
 *
 * @param {number[]} firstDataObject - The first array of numbers.
 * @param {number[]} secondDataObject - The second array of numbers.
 * @returns {number[]} An array containing the intersection of the two input arrays,
 * sorted in ascending order. This includes only those numbers that are present in both arrays.
 */
function handleFindSimilar(firstDataObject, secondDataObject) {
    const resultSimilarData = firstDataObject
        .filter((el) => secondDataObject.indexOf(el) !== -1);
    return resultSimilarData.sort((a, b) => a - b); // Ensure the result is sorted, just in case.
}

// Example usage
const firstArray = [1, 2, 3, 4, 5];
const secondArray = [0, 2, 4, 6, 8];
console.log(handleFindSimilar(firstArray, secondArray)); // Output: [2, 4]
```

Exercise 6: Filtering Based on Another Array
Goal: You have two arrays: one representing a list of banned words, and another with words from a paragraph of text. Filter the paragraph array to remove the banned words.

Input:
Banned words: ["clear", "water"]
Paragraph: ["sky", "clear", "blue", "water", "deep"]
Output: ["sky", "blue", "deep"]

## Solution: 
```js
/**
 * Filters out banned words from a paragraph.
 * 
 * @param {string[]} firstDataObject - An array of banned words.
 * @param {string[]} secondDataObject - An array of words representing a paragraph.
 * @returns {string[]} A new array containing only the words from the paragraph that are not banned.
 */
function handleClearBannedWords(firstDataObject, secondDataObject) {
    // Use the .filter() method to create a new array with words that are not banned.
    // The condition for keeping a word in the new array is that it is not found
    // in the array of banned words. This is checked using .indexOf(el) which returns -1
    // if the element is not found in the banned words array.
    const clearParagraph = secondDataObject.filter(el => firstDataObject.indexOf(el) === -1);

    // Return the new array with the filtered words.
    return clearParagraph;
}

// Example usage:
const bannedWords = ["clear", "water"]; // Define an array of banned words.
const sentenceToCensor = ["sky", "clear", "blue", "water", "deep"]; // Define an array representing a paragraph.

// Call the function with the arrays of banned words and the paragraph, and log the result.
console.log(handleClearBannedWords(bannedWords, sentenceToCensor)); // Expected output: ["sky", "blue", "deep"]

```