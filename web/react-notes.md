# React Notes

- [React App using Vite](#react-app-using-vite)
- [Routing](#Routing)
- [Handling Object State For Complex Types](#handling-object-state-for-complex-types)

# React App Using Vite

Vite is a fast build tool that provides a great developer experience for modern web projects. It's a suitable alternative to Create React App for setting up a React application quickly. Here’s how to create a new React app using Vite.

Make sure you have Node.js installed.

```text
C:\Users\kalje>node -v
v18.15.0
```

```javascript
# Create a new Vite project
C:\Users\kalje>npm create vite@latest
√ Project name: ... vite-project
? Select a framework: » - Use arrow-keys. Return to submit.
>   Vanilla
    Vue
    React
    Preact
    Lit
    Svelte
    Solid
    Qwik
    Others

 Select a framework: » React
? Select a variant: » - Use arrow-keys. Return to submit.
>   TypeScript
    TypeScript + SWC
    JavaScript
    JavaScript + SWC
    Remix ↗
```

# Routing

To implement routing in a React application, you can use the react-router-dom.

```text
npm install react-router-dom
```

```typescript
// App.tsx
import React from "react";
import { BrowserRouter as Router, Route, Routes, Link } from "react-router-dom";
import Home from "./Home";
import About from "./About";
import Contact from "./Contact";

const App = () => {
  return (
    <>
      <Router>
        <nav>
          <ul>
            <li>
              <Link to="/">Home</Link>
            </li>
            <li>
              <Link to="/about">About</Link>
            </li>
          </ul>
        </nav>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/about" element={<About />} />
        </Routes>
      </Router>
    </>
  );
};

export default App;
```

Handling 404 Pages

```text
<Route path="*" element={<NotFound />} />
```

# Handling Object State for Complex Types

Don't create multiple states.

```typescript
type student = {
  firstName: string;
  lastName: string;
  age: number;
};

const StudentRegistration = () => {
  const [studentState, setstudentState] = useState<student>({
    firstName: "",
    lastName: "",
    age: 0,
  });

  function handleFormChange (source: string, value: string) {
    setFormState({
      ...formState,
      [source]:value
    });
  };
```
