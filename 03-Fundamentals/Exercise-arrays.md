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

## Task 
 - Young Readers: Find all people under the age of 30 who have more than 1 favorite book. Return an array of their names.
 - Book Recommendations: Create a function that takes a book name as an argument and returns an array of names of people who have that book as a favorite. If no one has it as a favorite, return an empty array.
 - Age Sorting: Sort the array people by age in ascending order without altering the original array. Display the sorted array.
 - Favorite Books Flat List: Create a single array that contains every favoriteBooks entry from all people, without any duplicates. Sort this list alphabetically.

### Bonus task 
  Create a function that returns an object summarizing the data. The object should include the total number of people, the average age, and a list of all unique books sorted alphabetically.

## Solutions 
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
console.log(uniqueBooks);```