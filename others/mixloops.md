# Iterating Over Arrays in Multiple Languages

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


