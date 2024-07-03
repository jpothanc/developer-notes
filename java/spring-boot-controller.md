# Spring Boot Controller

```java
import io.swagger.v3.oas.annotations.tags.Tag;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@Tag(name = "greeting", description = "the greeting API")
@RequestMapping("/api/v1/greet")
@RestController
public class GreetingController {

    //Captures query string parameters from the request.
    //curl "http://localhost:8080/greet?name=John"
    @Operation(summary = "Say hello")
    @GetMapping("/greet")
    public ResponseEntity<String> greet(@RequestParam String name) {
          var response = "Hello, " + name;
          return ResponseEntity.ok(response);
    }

    //Used to map path variables from the request URL to method arguments.
    //curl "http://localhost:8080/users/123"
    @GetMapping("/users/{userId}")
    public ResponseEntity<String> getUser(@PathVariable Long userId) {
        var response = "User ID: " + userId;
        return ResponseEntity.ok(response);
    }

    //Binds the HTTP request body to a method parameter. Typically used for JSON or XML payloads.
    //curl -X POST "http://localhost:8080/users" -H "Content-Type: application/json" -d '{"name":"John","age":30}'
    @PostMapping("/users")
    public ResponseEntity<String> createUser(@RequestBody User user) {
      var response = "User created: " + user.getName();
      return ResponseEntity.ok(response);
0   }

    //Accesses specific request headers by name.
    //curl -H "User-Agent: CustomUserAgent" "http://localhost:8080/header"
    @GetMapping("/header")
    public ResponseEntity<String> getHeader(@RequestHeader("User-Agent") String userAgent) {
          var response = "User-Agent: " + userAgent;
          return ResponseEntity.ok(response);
    }

    //Captures form response and exposes it as an object in the model for the view.
    //curl -X POST "http://localhost:8080/submit" -d "name=John&age=30"
    @PostMapping("/submit")
    public ResponseEntity<String> handleFormSubmission(@ModelAttribute User user) {

          var response = "Form submitted: " + user.getName();
          return ResponseEntity.ok(response);
    }



}

```

## Reactive Web Programming with Spring

# Reactive Web Programming with Spring

## Introduction

- **Reactive Programming**: Emphasizes asynchronous and non-blocking data streams.
- **Spring WebFlux**: Reactive web framework in Spring for building scalable and efficient applications.

## Key Concepts

### Mono

- **Definition**: Represents a reactive type in Spring for emitting at most one item.
- **Use Case**: Ideal for scenarios where you expect zero or one result, such as fetching a single resource asynchronously.

### Flux

- **Definition**: Represents a reactive type in Spring for emitting zero to N items.
- **Use Case**: Suitable for streaming multiple results or continuous data, enabling asynchronous data processing.

### **Schedulers**:

Manage the execution of reactive streams across threads.

- **Schedulers.immediate()** : Executes tasks immediately on the current thread, without scheduling.

- **Schedulers.single()** : Uses a single thread for executing tasks sequentially, ensuring
  non-blocking behavior without context switches.

- **Schedulers.parallel()** : Maintains a fixed pool of threads to execute tasks concurrently.
  Optimized for CPU-bound operations or parallel processing.

- **Schedulers.elastic()** : Dynamically creates threads as needed. Suitable for I/O-bound operations
  where tasks may block temporarily.

## Dependencies

- **spring-boot-starter-webflux**: Includes necessary dependencies for Spring WebFlux.
- **reactor-core**: Core library for reactive programming with Project Reactor.

## Benefits

- **Scalability**: Handles concurrent requests efficiently.
- **Performance**: Reduces resource consumption with non-blocking I/O.

## Considerations

- **Error Handling**: Use `onErrorResume` and `onErrorReturn` to handle errors in reactive streams.
- **Testing**: Utilize `StepVerifier` for testing reactive components.

## Conclusion

Reactive web programming with Spring WebFlux enables high-performance, asynchronous applications suitable for modern web development.

```java
import org.springframework.web.bind.annotation.*;
import reactor.core.publisher.Mono;

@RestController
public class UserController {

    //Mono is used to handle asynchronous, potentially non-blocking operations
    @GetMapping("/queryUsers")
    public Mono<ResponseEntity<QueryResponse>> getUsers(@ModelAttribute QueryRequest request) {

        return Mono.fromFuture(() -> userService.queryUser(request))
                .map(ResponseEntity::ok)
                .onErrorResume(NoSuchElementException.class,
                    e -> QueryResponse.notFound(request, e.getMessage(), HttpStatus.NOT_FOUND))
                .onErrorResume(Exception.class,
                     e -> QueryResponse.badRequest(request, e.getMessage(), HttpStatus.BAD_REQUEST));
    }

    @GetMapping("/{userId}")
    public Mono<ResponseEntity<User>> getUserById(@PathVariable String userId) {
        //converting synchronous operations into asynchronous ones
        return Mono.fromCallable(() -> userService.getUserById(userId))
                   .subscribeOn(Schedulers.elastic())
                   .map(user -> ResponseEntity.ok(user))
                   .switchIfEmpty(Mono.just(ResponseEntity.notFound().build()))
                   .onErrorResume(e -> Mono.just(ResponseEntity.status(HttpStatus.INTERNAL_SERVER_ERROR).build()));
    }
}
```
