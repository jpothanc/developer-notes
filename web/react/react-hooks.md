## `useState` Hook

`useState` is a fundamental hook in React that allows you to add state management to function components. It is used for handling simple state transitions and managing the component's state without writing a class.

### Usage

To use `useState`, you simply declare a state variable and a function to update it:

```javascript
import React, { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Current count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
}
```

## `useEffect` Hook

The `useEffect` hook can be used to perform side effects in your component. When dependencies are specified, the effect runs only when those dependencies change. The cleanup function is used to perform cleanup activities like unsubscribing from events or clearing timers.

### Code Examples

```javascript
import React, { useEffect, useState } from "react";

function Example() {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetch("https://api.example.com/data")
      .then((response) => response.json())
      .then((data) => setData(data));
  }, []); // The empty array means this effect runs once after the initial render

  return (
    <div>
      {data.map((item) => (
        <p key={item.id}>{item.title}</p>
      ))}
    </div>
  );
}
```

```javascript
//Example of `useEffect` with Dependencies and Cleanup
import React, { useEffect, useState } from "react";

function MousePosition() {
  const [position, setPosition] = useState({ x: 0, y: 0 });

  useEffect(() => {
    // Effect function to track mouse position
    const handleMouseMove = (event) => {
      setPosition({
        x: event.clientX,
        y: event.clientY,
      });
    };

    // Subscribe to the mouse move event
    window.addEventListener("mousemove", handleMouseMove);

    // Cleanup function to remove the event listener
    return () => {
      window.removeEventListener("mousemove", handleMouseMove);
    };
  }, []); // Empty dependencies array means this effect runs once after the initial render

  return (
    <div>
      <h1>Mouse Position Tracker</h1>
      <p>X position: {position.x}</p>
      <p>Y position: {position.y}</p>
    </div>
  );
}
```

## `useContext` Hook

`useContext` is a hook in React that lets you subscribe to React context without introducing nesting. It's a simpler and cleaner way to access the context's value compared to the traditional `Context.Consumer`.

### Usage

The `useContext` hook requires a context object (which you can create using `React.createContext`) and returns the current context value, as determined by the closest matching `Provider` above it in the tree.

Here's a basic example to demonstrate its use:

```javascript
import React, { useContext, createContext } from "react";

// Creating a context
const ThemeContext = createContext("light");

function App() {
  // Using useContext to subscribe to the context
  const theme = useContext(ThemeContext);

  return (
    <div
      style={{
        background: theme === "dark" ? "#333" : "#FFF",
        color: theme === "dark" ? "#FFF" : "#333",
      }}
    >
      <h1>Welcome to the Theme Switcher App</h1>
      <p>The current theme is {theme}.</p>
    </div>
  );
}

function Wrapper() {
  // Providing the context value
  return (
    <ThemeContext.Provider value="dark">
      <App />
    </ThemeContext.Provider>
  );
}
```

## `useReducer` Hook

`useReducer` is a hook in React that is used for state management in React components. It is particularly useful when you have complex state logic that involves multiple sub-values or when the next state depends on the previous one. It's an alternative to `useState`, providing more direct control over the state management.

### Usage

The `useReducer` hook takes a reducer function and an initial state as arguments. It returns the current state and a dispatch method, which you can use to update the state.

Here’s a basic example demonstrating its use:

```javascript
import React, { useReducer } from "react";

// Reducer function
const reducer = (state, action) => {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    case "decrement":
      return { count: state.count - 1 };
    default:
      return state;
  }
};

function Counter() {
  // Using useReducer
  const [state, dispatch] = useReducer(reducer, { count: 0 });

  return (
    <div>
      <h1>Count: {state.count}</h1>
      <button onClick={() => dispatch({ type: "increment" })}>Increment</button>
      <button onClick={() => dispatch({ type: "decrement" })}>Decrement</button>
    </div>
  );
}
```

## `useRef` Hook

`useRef` can be used to interact with DOM elements or persist values across renders without causing re-renders.

### Usage

The `useRef` hook is typically used for two main purposes: accessing DOM elements directly and storing mutable data across renders.

### Usage

The `useRef` hook is typically used for two main purposes: accessing DOM elements directly and storing mutable data across renders.

### Code Example

```javascript
import React, { useEffect, useRef } from "react";

function AutoFocusInput() {
  const inputRef = useRef(null);

  useEffect(() => {
    // Automatically focus the input when the component mounts
    if (inputRef.current) {
      inputRef.current.focus();
    }
  }, []);

  return (
    <div>
      <input ref={inputRef} type="text" placeholder="Focus me on load" />
    </div>
  );
}
```

## `useCallback` Hook

`useCallback` is a hook in React that returns a memoized callback function. This hook is useful when passing callbacks to optimized child components that rely on reference equality to prevent unnecessary renders. `useCallback` ensures that the function object remains the same across renders unless its dependencies change, thereby helping in optimizing performance, especially in components with heavy rendering or complex calculations.

### Usage

The `useCallback` hook is used to create a function that will have the same reference between renders unless one of its dependencies changes. It's similar to `useMemo`, but specifically designed for functions.

Here’s a basic example demonstrating its use:

```javascript
import React, { useCallback, useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  // Increment counter callback
  const increment = useCallback(() => {
    setCount((c) => c + 1);
  }, []); // Dependencies array is empty, so this function is created only once

  return (
    <div>
      <h1>Count: {count}</h1>
      <button onClick={increment}>Increment</button>
    </div>
  );
}
```

## `useMemo` Hook

`useMemo` is a React hook that memorizes the output of a function. It's used to optimize performance by avoiding expensive calculations on every render. This hook only recalculates the memoized value when one of its dependencies changes, making it ideal for optimizing components that rely on complex calculations or heavy computations.

### Usage

`useMemo` takes a function and an array of dependencies. The function runs when the component mounts and whenever one of the dependencies changes. The returned value is preserved between renders unless the dependencies update.

Here’s a basic example demonstrating its use:

```javascript
import React, { useMemo, useState } from "react";

function ExpensiveComponent({ number }) {
  const [count, setCount] = useState(0);
  const [themeChange, setThemeChange] = useState(false); 

   const expensiveCalculation = () => {
    console.log("Calculating...");
    return number * 2; // Simulating an expensive operation
  };

  
  const expensiveCalculation = useMemo(() => {
    console.log("Calculating...");
    return number * 2; // Simulating an expensive operation
  }, [number]);

  return (
    <div>
      <h1>Computed Value: {expensiveCalculation}</h1>
      <h2>Count: {count}</h2>
      <button onClick={() => setCount(count + 1)}>Increment Count</button>
       <button onClick={() => setThemeChange(!themeChange)}>Toggle Theme Change</button>
    </div>
  );
}
```
