# TypeScript - `unknown` over `any`

## `any`
- **Description**: The most permissive type; disables all type checking.
- **Usage**: When you don't know the type of a value and need flexibility.

| Pros                                                                 | Cons                                                            |
| -------------------------------------------------------------------- | --------------------------------------------------------------- |
| Maximum flexibility: Can assign any type and perform any operation.  | No type safety: Allows runtime errors.                          |
| Useful for rapid prototyping and migrating JavaScript to TypeScript. | Reduces TypeScript's compile-time error checking benefits.      |

## `unknown`
- **Description**: A safer alternative to `any`; requires type checks before use.
- **Usage**: When you don't know the type of a value but want to ensure type safety.

| Pros                                                             | Cons                                                        |
| ---------------------------------------------------------------- | ----------------------------------------------------------- |
| Type safety: Forces type checks, reducing runtime errors.        | Requires additional type checks or assertions, adding verbosity. |
| Encourages explicit handling of different types.                 |                                                             |

```javascript
let value: any;
value = 123;
value = "hello";
value.foo(); // No compile-time error, but may fail at runtime

```

```javascript
let value: unknown;
value = 123;
value = "hello";

// Compile-time error if used without type check
// value.foo(); // Error: Object is of type 'unknown'

// Correct usage with type check
if (typeof value === "string") {
  console.log(value.toUpperCase()); // TypeScript knows value is a string here
}

```