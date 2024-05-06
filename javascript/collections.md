# JavaScript Collections

JavaScript provides various collections for storing and managing data, each with specific features and uses.

## Arrays

Arrays are ordered collections that can hold any type of value.

```javascript
// Initialize with data
const arr = [1, 2, 3, 4, 5];
// Initialize without data
const emptyArr = [];

// Append to end
arr.push(6); // [1, 2, 3, 4, 5, 6]

// Prepend to beginning
arr.unshift(0); // [0, 1, 2, 3, 4, 5]

// Remove last element
arr.pop(); // [1, 2, 3, 4]

// Remove first element
arr.shift(); // [2, 3, 4, 5]

// Slice (does not modify original)
const slicedArr = arr.slice(1, 3); // [2, 3]

// Splice (modifies original)
arr.splice(1, 2); // arr is now [1, 4, 5]

// Concatenate
const concatenatedArr = arr.concat([6, 7, 8]); // [1, 4, 5, 6, 7, 8]

// Access by index
const firstElement = arr[0]; // 1

// IndexOf
const index = arr.indexOf(4); // 1

// Includes
const hasElement = arr.includes(4); // true

// Filter
const filteredArr = arr.filter((x) => x > 2); // [4, 5]

// Map
const mappedArr = arr.map((x) => x * 2); // [2, 8, 10]

// Reduce
const sum = arr.reduce((acc, x) => acc + x, 0); // 10
```

## Map

Maps store keyed items and maintain the insertion order of the keys.

```javascript
// With data
const map = new Map([
  ["key1", "value1"],
  ["key2", "value2"],
  ["key3", "value3"],
]);

// Without data
const emptyMap = new Map();

// Add or update entry
map.set("key4", "value4");

// Remove entry
map.delete("key2");

// Check existence
const exists = map.has("key3"); // true

// Size
const size = map.size; // 3

// Clear
map.clear(); // Empties the map

// Iterate over entries
for (const [key, value] of map) {
  console.log(`${key}: ${value}`);
}

// Iterate over keys
for (const key of map.keys()) {
  console.log(key);
}

// Iterate over values
for (const value of map.values()) {
  console.log(value);
}

// Get value
const value = map.get("key1"); // 'value1'

// Convert Map to Array
const mapArr = Array.from(map); // [['key1', 'value1'], ['key3', 'value3'], ['key4', 'value4']]
```

## Set

Sets are collections of unique values.

```javascript
// With data
const set = new Set([1, 2, 3, 4, 5]);

// Without data
const emptySet = new Set();

// Add elements
set.add(6);

// Remove elements
set.delete(2);

// Check existence
const exists = set.has(3); // true

// Size
const size = set.size; // 5

// Clear
set.clear(); // Empties the set

// Iterate over elements
for (const value of set) {
  console.log(value);
}

// Add elements
set.add(6);

// Remove elements
set.delete(2);

// Check existence
const exists = set.has(3); // true

// Size
const size = set.size; // 5

// Clear
set.clear(); // Empties the set

// Iterate over elements
for (const value of set) {
  console.log(value);
}
```

## Objects

Objects represent structured data as collections of key-value pairs.

```javascript
// With data
const user = {
  id: 1,
  name: "Alice",
  email: "alice@example.com",
  age: 28,
};

// Without data
const emptyObj = {};

// Add or update property
user.phone = "555-1234";
user["country"] = "USA";

// Delete property
delete user.age;

// Check existence
const exists = "email" in user; // true

// Clear object
Object.keys(user).forEach((key) => delete user[key]);

// Access by key
const userName = user.name; // 'Alice'
const userEmail = user["email"]; // 'alice@example.com'

// Get keys
const keys = Object.keys(user); // ['id', 'name', 'email', 'phone', 'country']

// Get values
const values = Object.values(user); // [1, 'Alice', 'alice@example.com', '555-1234', 'USA']

// Get entries
const entries = Object.entries(user); // [['id', 1], ['name', 'Alice'], ['email', 'alice@example.com'], ['phone', '555-1234'], ['country', 'USA']]

// Check if key exists
const hasKey = "name" in user; // true

// Iterate over keys
for (const key in user) {
  if (user.hasOwnProperty(key)) {
    console.log(`${key}: ${user[key]}`);
  }
}
```
