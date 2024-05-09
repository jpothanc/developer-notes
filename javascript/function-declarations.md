## TypeScript Function Declarations

1. **Function Declaration:**

```typescript
function add(x: number, y: number): number {
  return x + y;
}
```

2. **Function Expression:**

```typescript
const subtract = function (x: number, y: number): number {
  return x - y;
};
```

3. **Arrow Function Expression:**

```typescript
const multiply = (x: number, y: number): number => {
  return x * y;
};
```

4. **Shorthand Arrow Function Expression:**

```typescript
const divide  = (x: number, y: number): number =>  return x / y;
```

5. **Function Constructor:**

```typescript
const modulo = new Function("x", "y", "return x % y");

// Call
const result5 = modulo(10, 3);
console.log(result5); // Output: 1
```

6. **Function with Optional Parameters:**

```typescript
function greet(name: string, greeting?: string): void {
  if (greeting) {
    console.log(`${greeting}, ${name}!`);
  } else {
    console.log(`Hello, ${name}!`);
  }
}
```

7. **Function with Default Parameters:**

```typescript
function greet(name: string, greeting: string = "Hello"): void {
  console.log(`${greeting}, ${name}!`);
}
```

8. **Function Overloads:**

```typescript
function combine(x: string, y: string): string;
function combine(x: number, y: number): number;
function combine(x: any, y: any): any {
  return x + y;
}
```

0. **Function Type:**

```typescript
type MathOperation = (x: number, y: number) => number;

const power: MathOperation = (x, y) => Math.pow(x, y);

// Call
const result10 = power(2, 3);
console.log(result10); // Output: 8
```
