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

Using Reactive Core:

```java
import org.springframework.web.bind.annotation.*;
import reactor.core.publisher.Mono;

@RestController
public class UserController {

    //Mono is used to handle asynchronous, potentially non-blocking operations
    //Use dependany reactor-core
    @GetMapping("/queryUsers")
    public Mono<ResponseEntity<QueryResponse>> getUers(@ModelAttribute QueryRequest request) {

        try {
            var response = catalogueService.queryCatalogueItem(request).join();
            return Mono.just(ResponseEntity.ok(response));

        } catch (NoSuchElementException e) {
            return Mono.just(QueryResponse.notFound(request, e.getMessage(), HttpStatus.NOT_FOUND));

        } catch (Exception e) {
            return Mono.just(QueryResponse.badRequest(request, e.getMessage(), HttpStatus.BAD_REQUEST));
        }
    }
}
```
