# Data Logic in JavaScript

## Regular Expressions (Regex)
Regular expressions are patterns used to match character combinations in strings. In JavaScript, you can create a regex using either the `RegExp` constructor or a regex literal.

**Example:**
```javascript
const regex = /\d+/; // Matches one or more digits
```

## Arrays
Arrays are used to store multiple values in a single variable. JavaScript arrays can hold various types of data and come with useful methods to manipulate them.

**Example:**
```javascript
let fruits = ['apple', 'banana', 'cherry'];
console.log(fruits.length); // Output: 3
```

## Dates
JavaScript provides the `Date` object for handling dates and times. You can create a new date object using the `new Date()` constructor.

**Example:**
```javascript
let now = new Date();
console.log(now.toISOString()); // Output: ISO format of the current date and time
```