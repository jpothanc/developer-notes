# Completable Future
A `CompletableFuture` is a class in Java that belongs to the `java.util.concurrent` package.

It is used for asynchronous computation. The code is executed as a non-blocking call in a separate thread, and the result is made available when it is ready.

## Why Use CompletableFuture

- **Asynchronous Execution**: Execute tasks asynchronously without blocking the main thread, improving application responsiveness.
- **Non-Blocking**: Provides a non-blocking API for running tasks, allowing chaining of multiple asynchronous calls.
- **Composability**: Combine multiple `CompletableFuture` instances using methods like `thenApply`, `thenCompose`, `thenCombine`, etc., for complex asynchronous workflows.
- **Exception Handling**: Offers robust exception handling mechanisms, allowing you to handle errors gracefully in asynchronous tasks.
- **Concurrency**: Simplifies working with concurrent tasks, allowing you to run multiple tasks in parallel and combine their results efficiently.
- **Callback Hell**: Helps avoid callback hell (deeply nested callbacks) by providing a more readable and maintainable approach to chaining asynchronous tasks.