## Swagger Intergration

Swagger is a set of open-source tools for building, documenting, and consuming RESTful web services.

In the Java ecosystem, Swagger is often used in combination with Spring Boot to generate interactive API documentation and client libraries.

Gradle:

```sh
implementation 'org.springdoc:springdoc-openapi-starter-webmvc-ui:2.5.0'
```

Maven:

```sh
<!-- https://mvnrepository.com/artifact/org.springdoc/springdoc-openapi-starter-webmvc-ui -->
<dependency>
    <groupId>org.springdoc</groupId>
    <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
    <version>2.5.0</version>
</dependency>

```

```java
import io.swagger.v3.oas.models.OpenAPI;
import io.swagger.v3.oas.models.info.Info;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class SwaggerConfig {

    @Bean
    public OpenAPI customOpenAPI() {
        return new OpenAPI()
                .info(new Info()
                        .title("Greeting API")
                        .version("1.0")
                        .description("API for greeting users"));
    }
}
```

```java
import io.swagger.v3.oas.annotations.tags.Tag;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@Tag(name = "greeting", description = "the greeting API")
@RestController
public class GreetingController {

    @Operation(summary = "Say hello")
    @GetMapping("/hello")
    public String hello(@RequestParam String name) {
        return "Hello, " + name;
    }

     @Operation(summary = "Say goodbye")
    @GetMapping("/goodbye")
    public String goodbye(@RequestParam String name) {
        return "Goodbye, " + name;
    }
}

```

Once integrated you can access the API documentation using

```json
http://localhost:8080/swagger-ui.html
http://localhost:8080/v3/api-docs
```

if you wish to override this, add the below in properties file

```properties
springdoc.api-docs.path=/v1/api-docs
springdoc.swagger-ui.path=/swagger.html
```

[Swagger Documentation](https://github.com/springdoc/springdoc-openapi?tab=readme-ov-file#getting-started)

## Deploy and Override Properties in Production

Default application.properties:

```properties
# Default server port
server.port=8080

# Default database connection properties
spring.datasource.url=jdbc:mysql://localhost:3306/mydb
spring.datasource.username=root
spring.datasource.password=secretpassword

```

For production environment: application-prod.properties

```properties
# Override server port for production
server.port=9090

```

This command instructs Spring Boot to load properties in the following order of precedence:

- application-prod.properties: Overrides specific properties (server.port) for development environment.
- application.properties (default bundled in JAR): Provides default configuration for other properties not overridden.

```sh
java -jar your-application.jar --spring.config.location=file:/path/to/application-prod.properties,file:/path/to/application.properties

```
