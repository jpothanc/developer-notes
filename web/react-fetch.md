# Fetch API

The Fetch API simplifies HTTP requests in JavaScript, but lacks built-in support for cancelling requests. Utilizing the AbortController interface addresses this limitation, allowing for the cancellation of fetch requests, enhancing resource management and user experience.

### Simple Fetch

```javascript
async function simpleFetchGet(url: string, signal?: AbortSignal): Promise<any> {
  const response = await fetch(url, { signal });

  if (!response.ok) {
    throw new Error(`Error: ${response.status}`);
  }

  const data = await response.json();
  return data;
}
```

### Using Generics

```javascript
async function simpleFetchGet<T>(
  url: string,
  signal?: AbortSignal
): Promise<T> {
  const response = await fetch(url, { signal });

  if (!response.ok) {
    throw new Error(`Error: ${response.status}`);
  }

  const data: T = await response.json();
  return data;
}
```

### Using Fluent Syntax

```javascript
function simpleFetchGet(url: string, signal?: AbortSignal): Promise<any> {
  return fetch(url, { signal }).then((response) => {
    if (!response.ok) {
      throw new Error(`Error: ${response.status}`);
    }
    return response.json();
  });
}
```

### Using Fluent Syntax in React Components Directly

```javascript

const [users, setUsers] = useState<User[]>([]);

useEffect(() => {
  const controller = new AbortController();
  const signal = controller.signal;

  fetch(url, { signal })
    .then((response) => {
      if (!response.ok) {
        throw new Error('Network response was not ok');
      }
      return response.json();
    })
    .then((users) => setUsers(users))
    .catch((error) => {
      // Handle any errors here
      console.error('Error fetching data:', error);
    });

  return () => {
    controller.abort();
  };
}, []);


```

### Using simpleFetchGet in React

```javascript
//given the user type
interface User {
  id: number;
  name: string;
  username: string;
  email: string;
}
....
const [users, setUsers] = useState<User[]>([]);
const [error, setError] = useState<string | null>(null);
const [loading, setLoading] = useState<boolean>(true);
const USERS_API_URL = 'https://jsonplaceholder.typicode.com/users';
useEffect(() => {
    const controller = new AbortController();
    const { signal } = controller;

    const fetchUsers = async () => {
      setLoading(true);
      setError(null);

     //using promise which returns any
      /*await simpleFetchGet(USERS_API_URL, signal)
      .then((data) => {
        const users: User[] = data; // Cast the data to User[]
        setUsers(users);
      })*/

      //using generics
      await simpleFetchGet<User[]>(USERS_API_URL, signal)
        .then((data) => {
          setUsers(data);
        })
        .catch((err: any) => {
          if (err.name === 'AbortError') {
            console.log('Fetch request was aborted!');
          } else {
            console.error('Fetch error:', err);
            setError(err.message);
          }
        })
        .finally(() => {
          setLoading(false);
        });
    };

    fetchUsers();

    // Cleanup function to abort the request
    return () => {
      controller.abort();
    };
  }, []);
```
