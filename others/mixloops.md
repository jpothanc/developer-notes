## Common Loop Patterns

### `for` Loop

- **C#**
  ```csharp
  int[] numbers = { 1, 2, 3, 4, 5 };
  for (int i = 0; i < numbers.Length; i++)
  {
      Console.WriteLine(numbers[i]);
  }
  ```
- **Java**
  ```java
  int[] numbers = { 1, 2, 3, 4, 5 };
  for (int i = 0; i < numbers.length; i++)
  {
      System.out.println(numbers[i]);
  }
  ```
- **Python**
  ```python
  numbers = [1, 2, 3, 4, 5]
  for num in range(len(numbers)):
      print(numbers[num])
  ```
- **JavaScript**
  ```javascript
  const numbers = [1, 2, 3, 4, 5];
  for (let i = 0; i < numbers.length; i++) {
    console.log(numbers[i]);
  }
  ```

### Enhanced `for` Loop

- **C#**
  ```csharp
  foreach (int num in numbers)
  {
      Console.WriteLine(num);
  }
  ```
- **Java**
  ```java
  for (int num : numbers)
  {
      System.out.println(num);
  }
  ```
- **Python**
  ```python
  for num in numbers:
      print(num)
  ```
- **JavaScript**
  ```javascript
  for (const num of numbers) {
    console.log(num);
  }
  ```

### `while` Loop

- **C#**
  ```csharp
  int index = 0;
  while (index < numbers.Length)
  {
      Console.WriteLine(numbers[index]);
      index++;
  }
  ```
- **Java**
  ```java
  int index = 0;
  while (index < numbers.length)
  {
      System.out.println(numbers[index]);
      index++;
  }
  ```
- **Python**
  ```python
  index = 0
  while index < len(numbers):
      print(numbers[index])
      index += 1
  ```
- **JavaScript**
  ```javascript
  let index = 0;
  while (index < numbers.length) {
    console.log(numbers[index]);
    index++;
  }
  ```

### Functional Methods

- **C#**

  ```csharp
  // Using Array.ForEach method
  Array.ForEach(numbers, num => Console.WriteLine(num));

  // Using LINQ Select method
  var doubled = numbers.Select(x => x * 2);
  foreach (int num in doubled)
  {
      Console.WriteLine(num);
  }
  ```

- **Java**
  ```java
  // Using Streams API forEach method
  Arrays.stream(numbers).forEach(System.out::println);
  ```
- **Python**
  ```python
  # Using list comprehension
  [print(num) for num in numbers]
  ```
- **JavaScript**

  ```javascript
  // Using the forEach method
  numbers.forEach((num) => console.log(num));

  // Using the map method
  numbers.map((num) => console.log(num));
  ```

## Iterating Over Sets

### C#

```csharp
// Using HashSet
HashSet<int> set = new HashSet<int> {1, 2, 3, 4};
foreach (int elem in set) {
    Console.WriteLine(elem);
}
```

### Java

```java
// Using HashSet
Set<Integer> set = new HashSet<>(Arrays.asList(1, 2, 3, 4));
for (int elem : set) {
    System.out.println(elem);
}
```

### Python

```python
# Using set
s = {1, 2, 3, 4}
for elem in s:
    print(elem)

```

### Javascript

```javascript
// Using Set
let set = new Set([1, 2, 3, 4]);
for (let elem of set) {
  console.log(elem);
}
```

## Iterating Over Maps

```csharp
// Using Dictionary
Dictionary<string, int> map = new Dictionary<string, int> {
    {"a", 1}, {"b", 2}, {"c", 3}, {"d", 4}
};
foreach (KeyValuePair<string, int> entry in map) {
    Console.WriteLine($"{entry.Key}: {entry.Value}");
}

```

### Java

```java
// Using HashMap
Map<String, Integer> map = new HashMap<>();
map.put("a", 1);
map.put("b", 2);
map.put("c", 3);
map.put("d", 4);

for (Map.Entry<String, Integer> entry : map.entrySet()) {
    System.out.println(entry.getKey() + ": " + entry.getValue());
}

```

### Python

```python
# Using dictionary
d = {"a": 1, "b": 2, "c": 3, "d": 4}
for key, value in d.items():
    print(f"{key}: {value}")


```

### Javascript

```javascript
// Using Map
let map = new Map([
  ["a", 1],
  ["b", 2],
  ["c", 3],
  ["d", 4],
]);
for (let [key, value] of map) {
  console.log(`${key}: ${value}`);
}
```
