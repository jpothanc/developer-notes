# C# Collections

C# provides various collections for storing and managing data, each with specific features and uses.

## Arrays

Arrays are ordered collections that can hold any type of value.

```csharp
// Initialize List with data
var listWithData = new List<int> { 1, 2, 3, 4, 5 };

// Initialize empty List
var emptyList = new List<int>();

// Adding elements
listWithData.Add(6); // [1, 2, 3, 4, 5, 6]
listWithData.Insert(0, 0); // [0, 1, 2, 3, 4, 5, 6]

// Removing elements
listWithData.Remove(3); // [0, 1, 2, 4, 5, 6]
listWithData.RemoveAt(0); // [1, 2, 4, 5, 6]

// Accessing elements
int firstElement = listWithData[0]; // 1

// Finding elements
int index = listWithData.IndexOf(4); // 2

// Checking for existence
bool hasElement = listWithData.Contains(5); // true

// Iterating
foreach (int element in listWithData)
{
    Console.WriteLine(element);
}

// Sorting
listWithData.Sort(); // [1, 2, 4, 5, 6]

// Other operations
var subList = listWithData.GetRange(1, 3); // [2, 4, 5]
var concatenatedList = new List<int>(listWithData);
concatenatedList.AddRange(new int[] { 7, 8, 9 }); // [1, 2, 4, 5, 6, 7, 8, 9]


```

## Map

Maps store keyed items and maintain the insertion order of the keys.

```csharp
// Initialize Dictionary with data
var dictionaryWithData = new Dictionary<string, int>
{
    { "one", 1 },
    { "two", 2 },
    { "three", 3 }
};

// Initialize empty Dictionary
var emptyDictionary = new Dictionary<string, int>();

// Adding/updating entries
dictionaryWithData["four"] = 4; // { "one" = 1, "two" = 2, "three" = 3, "four" = 4 }

// Removing entries
dictionaryWithData.Remove("two"); // { "one" = 1, "three" = 3, "four" = 4 }

// Accessing values by key
int value = dictionaryWithData["one"]; // 1

// Checking for existence
bool hasKey = dictionaryWithData.ContainsKey("three"); // true
bool hasValue = dictionaryWithData.ContainsValue(4); // true

// Iterating
foreach (var entry in dictionaryWithData)
{
    Console.WriteLine($"{entry.Key}: {entry.Value}");
}

// Converting to array
string[] keysArray = dictionaryWithData.Keys.ToArray(); // ["one", "three", "four"]
int[] valuesArray = dictionaryWithData.Values.ToArray(); // [1, 3, 4]

// Other operations
dictionaryWithData.Clear(); // Dictionary is now empty


```

## Set

Sets are collections of unique values.

```csharp
// Initialize HashSet with data
var hashSetWithData = new HashSet<int> { 1, 2, 3, 4, 5 };

// Initialize empty HashSet
var emptyHashSet = new HashSet<int>();

// Adding elements
hashSetWithData.Add(6); // [1, 2, 3, 4, 5, 6]

// Removing elements
hashSetWithData.Remove(3); // [1, 2, 4, 5, 6]

// Checking for existence
bool hasElement = hashSetWithData.Contains(4); // true

// Iterating
foreach (int element in hashSetWithData)
{
    Console.WriteLine(element);
}

// Converting to array
int[] arrayFromSet = hashSetWithData.ToArray(); // [1, 2, 4, 5, 6]

// Converting to List
var listFromSet = new List<int>(hashSetWithData); // [1, 2, 4, 5, 6]

// Other operations
hashSetWithData.Clear(); // HashSet is now empty


```

## Collections Hierarchy

```plaintext
System.Collections
├── ICollection (Interface)
│   ├── IList (Interface)
│   │   ├── List<T>
│   │   └── ArrayList
│   ├── ISet (Interface)
│   │   └── HashSet<T>
│   └── IDictionary (Interface)
│       └── Dictionary<TKey, TValue>
├── IEnumerable (Interface)
│   └── IEnumerator (Interface)
├── Queue (Non-Generic)
├── Stack (Non-Generic)
├── Queue<T> (Generic)
└── Stack<T> (Generic)

System.Collections.Generic
├── ICollection<T> (Interface)
│   ├── IList<T> (Interface)
│   │   └── List<T>
│   ├── ISet<T> (Interface)
│   │   └── HashSet<T>
│   └── IDictionary<TKey, TValue> (Interface)
│       └── Dictionary<TKey, TValue>
├── IEnumerable<T> (Interface)
│   └── IEnumerator<T> (Interface)
├── Queue<T>
└── Stack<T>

System.Collections.Concurrent
├── ConcurrentBag<T>
├── ConcurrentQueue<T>
├── ConcurrentStack<T>
└── ConcurrentDictionary<TKey, TValue>

System.Collections.Specialized
├── NameValueCollection
├── OrderedDictionary
└── StringCollection


```
