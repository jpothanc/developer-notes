# Collection classes


`Collection Interface`:This is one of the root interfaces in the collection hierarchy.

| Collection Type | Interface   | Key Implementations                               | Characteristics                                                                           | Performance                                   | Concurrency                                               |
|-----------------|-------------|--------------------------------------------------|-------------------------------------------------------------------------------------------|-----------------------------------------------|------------------------------------------------------------|
| List            | List        | ArrayList, LinkedList, Vector, Stack             | Ordered collection, allows duplicates, provides positional access.                        | Random access fast (ArrayList), slow insertions/deletions (LinkedList) | Vector, Stack are synchronized                             |
| Set             | Set         | HashSet, LinkedHashSet, TreeSet                  | No duplicates, provides various ordering options (insertion-order, natural ordering).     | Fast access (HashSet), ordered access (TreeSet) | Not synchronized; use `ConcurrentSkipListSet` for a concurrent version |
| Queue           | Queue       | LinkedList, PriorityQueue, ArrayDeque            | Holds elements prior to processing, typically ordered by FIFO (First In, First Out).      | Good at enqueue/dequeue operations            | Not synchronized; use `ConcurrentLinkedQueue` or `BlockingQueue` implementations like `ArrayBlockingQueue`, `LinkedBlockingQueue` for concurrent versions |
| Deque           | Deque       | ArrayDeque, LinkedList                           | Double-ended queue allowing element insertion and removal from both ends.                 | Fast at both ends (ArrayDeque)                | Not synchronized; use `ConcurrentLinkedDeque` for a concurrent version |
| Map             | Map         | HashMap, LinkedHashMap, TreeMap, Hashtable       | Key-value pairs, keys are unique, various ordering and threading options.                 | Fast access (HashMap), ordered access (TreeMap) | HashMap, LinkedHashMap not synchronized, Hashtable synchronized; use `ConcurrentHashMap` or `ConcurrentSkipListMap` for concurrent versions |
| Concurrent Map  | ConcurrentMap | ConcurrentHashMap, ConcurrentSkipListMap       | Key-value pairs with thread-safe concurrency features.                                    | High concurrency performance                  | Fully concurrent without locking (ConcurrentHashMap) or part-locked (ConcurrentSkipListMap) |


## Methods of Iterating Over an ArrayList
- Using an Iterator
- Using an Enhanced For-Loop (For-Each Loop)
- Using a Traditional For-Loop
- Using a ListIterator
- Using the forEach() 

| **Method**            | **Pros**                                              | **Cons**                                                   |
|-----------------------|-------------------------------------------------------|------------------------------------------------------------|
| **Iterator**          | - Safely remove elements during iteration.<br>- Good for generic code that works on any Collection. | - Slightly more verbose than for-each loop.<br>- Easy to forget calling `next()` causing infinite loops. |
| **Enhanced For-Loop** | - Concise and easy to use.<br>- Less error-prone as it eliminates the possibility of index out of bounds errors. | - Cannot modify the list (add/remove elements) during iteration.<br>- No access to the index. |
| **Traditional For-Loop** | - Access to the index.<br>- Ability to modify the list by adding or removing elements based on the index. | - Verbose.<br>- Risk of `IndexOutOfBoundsException` if not careful with bounds. |
| **ListIterator**      | - Bidirectional iteration (next and previous).<br>- Add, remove, and replace elements during iteration. | - More complex than simple iteration.<br>- Overhead of understanding additional methods. |
| **forEach() method**  | - Very concise, especially with lambda expressions.<br>- Separates business logic from iteration logic. | - Cannot modify the list directly (e.g., remove elements).<br>- No access to the index. |

```java
// Using an Iterator
Iterator<String> iterator = list.iterator();
while (iterator.hasNext()) {
    String element = iterator.next();
    if (element.equals("delete")) {
        iterator.remove();
    }
}
//Using an Enhanced For-Loop (For-Each Loop)
for (String element : list) {
    System.out.println(element);
}
//Using a Traditional For-Loop
for (int i = 0; i < list.size(); i++) {
    String element = list.get(i);
    if (element.equals("modify")) {
        list.set(i, "modified");
    }
}
//Using a ListIterator
ListIterator<String> listIterator = list.listIterator();
while (listIterator.hasNext()) {
    String element = listIterator.next();
    if (element.equals("modify")) {
        listIterator.set("modified");
    }
}
//Using the forEach()
list.forEach(element -> System.out.println(element));
```
## Manipulating ArrayList, HashSet, and HashMap


| **Operation**        | **ArrayList**                                | **HashSet**                                 | **HashMap**                                                      |
|----------------------|----------------------------------------------|---------------------------------------------|------------------------------------------------------------------|
| **Add**              | `list.add(element);`                         | `set.add(element);`                         | `map.put(key, value);`                                           |
| **Remove**           | `list.remove(element);`<br>`list.remove(index);` | `set.remove(element);`                      | `map.remove(key);`                                               |
| **Check Existence**  | `list.contains(element);`                    | `set.contains(element);`                    | `map.containsKey(key);`<br>`map.containsValue(value);`           |
| **Get**              | `element = list.get(index);`                 | Not applicable (No index-based access)      | `value = map.get(key);`                                          |
| **Update**           | `list.set(index, element);`                  | Replace by removing and adding if needed.   | `map.put(key, newValue);` (Updates value associated with key)    |
| **Size**             | `int size = list.size();`                    | `int size = set.size();`                    | `int size = map.size();`                                         |
| **Clear**            | `list.clear();`                              | `set.clear();`                              | `map.clear();`                                                   |


## Code Snippets

```java
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        ArrayList<Integer> numbers = new ArrayList<>();
        numbers.add(10);
        numbers.add(20);
        numbers.add(30);

        // Using a standard for-loop
        for (int i = 0; i < numbers.size(); i++) {
            System.out.println(numbers.get(i));
        }

        // Using an enhanced for-loop
        for (Integer number : numbers) {
            System.out.println(number);
        }

        // Using Java 8 Stream API
        numbers.stream().forEach(System.out::println);
    }
}

```

```java
import java.util.HashSet;
import java.util.Set;

public class Main {
    public static void main(String[] args) {
        // Initialize the HashSet with some values
        HashSet<Integer> numbers = new HashSet<>();
        //HashSet<Integer> numbers = new HashSet<>(Set.of(10, 20,));
        numbers.add(10);
        numbers.add(20);
        // Loop through the HashSet
        for (Integer number : numbers) {
            System.out.println(number);
        }
    }
}

```

```java
import java.util.Map;
import java.util.HashMap;

public class Main {
    public static void main(String[] args) {
        // Creating and initializing a HashMap
        Map<Integer, String> map = new HashMap<>();
        map.put(1, "one");
        map.put(2, "two");
        map.put(3, "three");

        // Looping over entry set
        for (Map.Entry<Integer, String> entry : map.entrySet()) {
            System.out.println("Key: " + entry.getKey() + ", Value: " + entry.getValue());
        }

        // Looping over key set
        for (Integer key : map.keySet()) {
        System.out.println("Key: " + key + ", Value: " + map.get(key));

        // Looping over value set
        for (Integer key : map.keySet()) {
        System.out.println("Key: " + key + ", Value: " + map.get(key));
}
        // Using forEach (Java 8+)
        map.forEach((key, value) -> System.out.println("Key: " + key + ", Value: " + value));
    }
}

```