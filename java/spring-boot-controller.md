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
        return "Hello, " + name;
    }

    //Used to map path variables from the request URL to method arguments.
    //curl "http://localhost:8080/users/123"
    @GetMapping("/users/{userId}")
    public ResponseEntity<String> getUser(@PathVariable Long userId) {
    return "User ID: " + userId;
    }

    //Binds the HTTP request body to a method parameter. Typically used for JSON or XML payloads.
    //curl -X POST "http://localhost:8080/users" -H "Content-Type: application/json" -d '{"name":"John","age":30}'
    @PostMapping("/users")
    public ResponseEntity<String> createUser(@RequestBody User user) {
    return "User created: " + user.getName();
0   }

    //Accesses specific request headers by name.
    //curl -H "User-Agent: CustomUserAgent" "http://localhost:8080/header"
    @GetMapping("/header")
    public ResponseEntity<String> getHeader(@RequestHeader("User-Agent") String userAgent) {
        return "User-Agent: " + userAgent;
    }

    //Captures form data and exposes it as an object in the model for the view.
    //curl -X POST "http://localhost:8080/submit" -d "name=John&age=30"
    @PostMapping("/submit")
    public ResponseEntity<String> handleFormSubmission(@ModelAttribute User user) {
        return "Form submitted: " + user.getName();
    }

}

```
