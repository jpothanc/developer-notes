# Java Collections

Java provides various collections for storing and managing data, each with specific features and uses.

## Arrays

Arrays are ordered collections that can hold any type of value.

```java
// Initialize ArrayList with data
List<Integer> arrayListWithData = new ArrayList<>(Arrays.asList(1, 2, 3, 4, 5));

// Initialize empty ArrayList
List<Integer> emptyArrayList = new ArrayList<>();

// Initialize LinkedList with data
List<Integer> linkedListWithData = new LinkedList<>(Arrays.asList(1, 2, 3, 4, 5));

// Initialize empty LinkedList
List<Integer> emptyLinkedList = new LinkedList<>();
// Adding elements
arrayListWithData.add(6); // [1, 2, 3, 4, 5, 6]
arrayListWithData.add(0, 0); // [0, 1, 2, 3, 4, 5, 6]

// Removing elements
arrayListWithData.remove(Integer.valueOf(3)); // [0, 1, 2, 4, 5, 6]
arrayListWithData.remove(0); // [1, 2, 4, 5, 6]

// Accessing elements
int firstElement = arrayListWithData.get(0); // 1

// Finding elements
int index = arrayListWithData.indexOf(4); // 2

// Checking for existence
boolean hasElement = arrayListWithData.contains(5); // true

// Iterating
for (int element : arrayListWithData) {
    System.out.println(element);
}

// Sorting
Collections.sort(arrayListWithData); // [1, 2, 4, 5, 6]

// Other operations
List<Integer> subList = arrayListWithData.subList(1, 4); // [2, 4, 5]
List<Integer> concatenatedList = new ArrayList<>(arrayListWithData);
concatenatedList.addAll(Arrays.asList(7, 8, 9)); // [1, 2, 4, 5, 6, 7, 8, 9]


```

## Map

Maps store keyed items and maintain the insertion order of the keys.

```java
// Initialize HashMap with data
Map<String, Integer> hashMapWithData = new HashMap<>() {{
    put("one", 1);
    put("two", 2);
    put("three", 3);
}};

// Initialize empty HashMap
Map<String, Integer> emptyHashMap = new HashMap<>();

// Initialize LinkedHashMap with data
Map<String, Integer> linkedHashMapWithData = new LinkedHashMap<>() {{
    put("one", 1);
    put("two", 2);
    put("three", 3);
}};

// Initialize empty LinkedHashMap
Map<String, Integer> emptyLinkedHashMap = new LinkedHashMap<>();

// Initialize TreeMap with data
Map<String, Integer> treeMapWithData = new TreeMap<>() {{
    put("one", 1);
    put("two", 2);
    put("three", 3);
}};

// Initialize empty TreeMap
Map<String, Integer> emptyTreeMap = new TreeMap<>();

// Adding/updating entries
hashMapWithData.put("four", 4); // {one=1, two=2, three=3, four=4}

// Removing entries
hashMapWithData.remove("two"); // {one=1, three=3, four=4}

// Accessing values by key
int value = hashMapWithData.get("one"); // 1

// Checking for existence
boolean hasKey = hashMapWithData.containsKey("three"); // true
boolean hasValue = hashMapWithData.containsValue(4); // true

// Iterating
for (Map.Entry<String, Integer> entry : hashMapWithData.entrySet()) {
    System.out.println(entry.getKey() + ": " + entry.getValue());
}

// Converting to array
String[] keysArray = hashMapWithData.keySet().toArray(new String[0]); // ["one", "three", "four"]
Integer[] valuesArray = hashMapWithData.values().toArray(new Integer[0]); // [1, 3, 4]

// Other operations
hashMapWithData.clear(); // Map is now empty


```

## Set

Sets are collections of unique values.

```java
// Initialize HashSet with data
Set<Integer> hashSetWithData = new HashSet<>(Arrays.asList(1, 2, 3, 4, 5));

// Initialize empty HashSet
Set<Integer> emptyHashSet = new HashSet<>();

// Initialize LinkedHashSet with data
Set<Integer> linkedHashSetWithData = new LinkedHashSet<>(Arrays.asList(1, 2, 3, 4, 5));

// Initialize empty LinkedHashSet
Set<Integer> emptyLinkedHashSet = new LinkedHashSet<>();

// Initialize TreeSet with data
Set<Integer> treeSetWithData = new TreeSet<>(Arrays.asList(1, 2, 3, 4, 5));

// Initialize empty TreeSet
Set<Integer> emptyTreeSet = new TreeSet<>();

// Adding elements
hashSetWithData.add(6); // [1, 2, 3, 4, 5, 6]

// Removing elements
hashSetWithData.remove(3); // [1, 2, 4, 5, 6]

// Checking for existence
boolean hasElement = hashSetWithData.contains(4); // true

// Iterating
for (int element : hashSetWithData) {
    System.out.println(element);
}

// Converting to array
Integer[] arrayFromSet = hashSetWithData.toArray(new Integer[0]); // [1, 2, 4, 5, 6]

// Converting to List
List<Integer> listFromSet = new ArrayList<>(hashSetWithData); // [1, 2, 4, 5, 6]

// Other operations
hashSetWithData.clear(); // Set is now empty
```

## Collections Hierarchy

```plaintext
java.util
├── Collection (Interface)
│   ├── List (Interface)
│   │   ├── AbstractList (Abstract Class)
│   │   │   ├── ArrayList
│   │   │   ├── AbstractSequentialList (Abstract Class)
│   │   │   │   └── LinkedList
│   │   ├── Vector
│   │   │   └── Stack
│   │   └── CopyOnWriteArrayList
│   ├── Set (Interface)
│   │   ├── AbstractSet (Abstract Class)
│   │   │   ├── HashSet
│   │   │   ├── LinkedHashSet
│   │   │   └── EnumSet
│   │   ├── SortedSet (Interface)
│   │   │   └── NavigableSet (Interface)
│   │   │       └── TreeSet
│   │   └── CopyOnWriteArraySet
│   └── Queue (Interface)
│       ├── Deque (Interface)
│       │   ├── ArrayDeque
│       │   └── LinkedList
│       ├── AbstractQueue (Abstract Class)
│       │   └── PriorityQueue
│       └── BlockingQueue (Interface)
│           ├── ArrayBlockingQueue
│           ├── LinkedBlockingQueue
│           ├── PriorityBlockingQueue
│           ├── DelayQueue
│           ├── SynchronousQueue
│           └── LinkedTransferQueue
└── Map (Interface)
    ├── AbstractMap (Abstract Class)
    │   ├── HashMap
    │   │   └── LinkedHashMap
    │   ├── TreeMap
    │   ├── WeakHashMap
    │   ├── IdentityHashMap
    │   └── EnumMap
    ├── SortedMap (Interface)
    │   └── NavigableMap (Interface)
    │       └── TreeMap
    ├── ConcurrentMap (Interface)
    │   └── ConcurrentHashMap
    └── Properties

```
