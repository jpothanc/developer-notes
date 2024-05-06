# Python Collections

Python provides various collections for storing and managing data, each with specific features and uses.

## Arrays

Arrays are ordered collections that can hold any type of value.

```python
# With data
const arrayWithData = [1, 2, 3, 4, 5];

# Empty
const emptyArray = [];

# Adding elements
arrayWithData.push(6);          # [1, 2, 3, 4, 5, 6]
arrayWithData.unshift(0);       # [0, 1, 2, 3, 4, 5, 6]
arrayWithData.splice(3, 0, 99); # [0, 1, 2, 99, 3, 4, 5, 6]

# Removing elements
arrayWithData.pop();            # [0, 1, 2, 99, 3, 4, 5]
arrayWithData.shift();          # [1, 2, 99, 3, 4, 5]
arrayWithData.splice(2, 1);     # [1, 2, 3, 4, 5]

# Finding elements
const found = arrayWithData.find(element => element === 4); # 4
const index = arrayWithData.indexOf(3); # 2

# Iterating
arrayWithData.forEach(element => console.log(element));
const mappedArray = arrayWithData.map(element => element * 2); # [2, 4, 6, 8, 10]

# Other operations
const filteredArray = arrayWithData.filter(element => element > 2); # [3, 4, 5]
const reducedValue = arrayWithData.reduce((acc, curr) => acc + curr, 0); # 15
const sortedArray = arrayWithData.sort((a, b) => a - b); # [1, 2, 3, 4, 5]
const reversedArray = arrayWithData.reverse(); # [5, 4, 3, 2, 1]

```

## Map

Maps store keyed items and maintain the insertion order of the keys.

```python
# With data
const mapWithData = new Map([
  ['key1', 'value1'],
  ['key2', 'value2'],
]);
# Adding/updating elements
mapWithData.set('key3', 'value3');

# Removing elements
mapWithData.delete('key2');

# Accessing values
const value = mapWithData.get('key1'); # 'value1'

# Checking existence
const hasKey = mapWithData.has('key3'); # true

# Iterating
mapWithData.forEach((value, key) => console.log(`${key}: ${value}`));
const mapEntries = Array.from(mapWithData.entries()); # [['key1', 'value1'], ['key3', 'value3']]

# Other operations
mapWithData.clear(); # Map {}

# Empty
const emptyMap = new Map();

```

## Set

Sets are collections of unique values.

```python
# With data
const setWithData = new Set([1, 2, 3, 4, 5]);

# Empty
const emptySet = new Set();

# Adding elements
setWithData.add(6); # Set {1, 2, 3, 4, 5, 6}

# Removing elements
setWithData.delete(3); # Set {1, 2, 4, 5, 6}

# Checking existence
const hasElement = setWithData.has(4); # true

# Iterating
setWithData.forEach(value => console.log(value));
const arrayFromSet = Array.from(setWithData); # [1, 2, 4, 5, 6]

# Other operations
setWithData.clear(); # Set {}


```

## Objects

Objects represent structured data as collections of key-value pairs.

```python
# Initialize with data
const objectWithData = {
  id: 1,
  name: "Alice",
  email: "alice@example.com",
  age: 28,
};

# Initialize without data
const emptyObject = {};

# Add/update property
objectWithData.phone = "123-456-7890"; # { id: 1, name: "Alice", email: "alice@example.com", age: 28, phone: "123-456-7890" }

# Remove property
delete objectWithData.email; # { id: 1, name: "Alice", age: 28, phone: "123-456-7890" }

# Access value by property
const name = objectWithData.name; # "Alice"

# Check if property exists
const hasProperty = "age" in objectWithData; # true

# Convert to arrays
const objectKeys = Object.keys(objectWithData); # ['id', 'name', 'age', 'phone']
const objectValues = Object.values(objectWithData); # [1, "Alice", 28, "123-456-7890"]
const objectEntries = Object.entries(objectWithData); # [['id', 1], ['name', 'Alice'], ['age', 28], ['phone', '123-456-7890']]

# Assign properties from another object
Object.assign(objectWithData, { address: "123 Main St" }); # { id: 1, name: "Alice", age: 28, phone: "123-456-7890", address: "123 Main St" }

# Create object from entries
const newObject = Object.fromEntries(objectEntries); # { id: 1, name: "Alice", age: 28, phone: "123-456-7890" }

# Iterate
for (const [key, value] of Object.entries(objectWithData)) {
  console.log(`${key}: ${value}`);
}


```
