# 1. What is Spring Boot?

Spring Boot is a Java framework built on top of the Spring Framework that makes it easy to create stand-alone, production-ready, and microservice-based applications with minimal configuration.

## In simple words:

Spring Boot = Spring Framework + Auto Configuration + Embedded Servers + Opinionated Defaults

It reduces the need for writing boilerplate code and configuration.

# 2. Need for Spring Boot (Why do we use it?)

Traditional Spring applications required lots of manual configuration such as:

- Configuring Spring beans
- Managing dependencies
- Setting up application servers manually
- Creating XML files
- Handling environment setups

## Spring Boot solves these issues by:

- ✅ Providing auto-configuration
- ✅ Giving starter dependencies
- ✅ Embedding servers like Tomcat/Jetty
- ✅ Reducing XML and boilerplate code
- ✅ Simplifying application deployment
- ✅ Making microservices development easier

# 3. Features of Spring Boot
### 1. Auto-Configuration

Automatically configures the application based on the dependencies present in the classpath.

### 2. Spring Boot Starters

Starter packs that include commonly used dependencies (e.g., spring-boot-starter-web, spring-boot-starter-data-jpa).

### 3. Embedded Servers

No need to deploy WAR files. Spring Boot provides embedded servers like:

- Tomcat
- Jetty
- Undertow

### 4. Production-Ready Features (Actuator)

Built-in endpoints to monitor application health, metrics, logs, etc.

### 5. CommandLineRunner / ApplicationRunner

Used to run code after startup.

### 6. Opinionated Defaults

Spring Boot automatically picks default configurations so the developer doesn't need to specify everything.

# 4. How Spring Boot Works (Auto-Configuration Explained)

## Spring Boot uses:

### 1. @EnableAutoConfiguration

This annotation tells Spring Boot to automatically configure beans based on the classpath.

#### Example:

- If spring-boot-starter-web is present, it configures DispatcherServlet, Tomcat, Jackson, etc.

- If spring-boot-starter-data-jpa is present, it configures EntityManager, DataSource, Hibernate, etc.

### 2. SpringFactoriesLoader

Loads auto-configuration classes from:
`META-INF/spring.factories`

### 3. Conditional Annotations

Spring Boot auto-configuration uses conditions like:

- `@ConditionalOnClass`
- `@ConditionalOnMissingBean`
- `@ConditionalOnProperty`

This ensures only necessary beans are created.

#### Result:
Spring Boot only configures what is required based on what you have added. No unnecessary configuration.

# 5. Spring Boot Architecture

Below is a simple explanation of Spring Boot architecture:

### A. Application Layer

#### Contains:

- Controllers
- Services
- Repositories
- Entities

### B. Spring Core Layer

#### Provides:

- IoC Container
- Dependency Injection
- Bean management

### C. Auto-Configuration Layer

Spring Boot auto-configures beans using the classpath and annotations.

### D. Spring Boot Starters

Provides preconfigured dependencies to add common functionality.

### E. Embedded Server Layer

#### Provides:

- Embedded Tomcat
- Jetty
- Undertow

### F. Externalized Configuration

Properties or YAML files (`application.properties` / `application.yml`).

### G. Actuator

For monitoring and management.

## Summary Table 
# Spring Boot Summary Table

| **Concept**      | **Explanation** |
|------------------|-----------------|
| **Spring Boot**  | A framework that simplifies Spring application development |
| **Need**         | Reduces configuration, speeds up development, and supports easy microservices creation |
| **Features**     | Auto-configuration, starter dependencies, embedded server, actuator |
| **Working**      | Uses auto-configuration with conditional checks based on classpath |
| **Architecture** | Application Layer → Spring Core → Auto-Configuration → Starters → Embedded Server → Actuator |

# Spring Boot Annotations

## 1. @SpringBootApplication
- Combination of three annotations:
  - `@Configuration`
  - `@EnableAutoConfiguration`
  - `@ComponentScan`
- Marks the main class of a Spring Boot application.
- Enables auto-configuration and component scanning.

---

## 2. @Configuration
- Indicates that the class contains Spring bean definitions.
- Replacement for XML configuration.
- Used with `@Bean` methods to create beans.

---

## 3. @EnableAutoConfiguration
- Tells Spring Boot to configure beans automatically based on the classpath.
- Example: If Spring Web is present, it configures DispatcherServlet automatically.

---

## 4. @ComponentScan
- Tells Spring to scan the package and sub-packages for components like:
  - `@Component`
  - `@Service`
  - `@Repository`
  - `@Controller`
- Automatically registers detected beans in the Spring container.

---

## 5. @RestController
- Combines:
  - `@Controller`
  - `@ResponseBody`
- Indicates that the class handles RESTful web requests.
- Returns JSON/XML responses directly.

---

## 6. @RequestMapping
- Maps a URL path to a controller class or method.
- Can be used with:
  - `method = RequestMethod.GET`
  - `method = RequestMethod.POST`, etc.
- Example: `@RequestMapping("/users")`

---

## 7. @GetMapping / @PostMapping / @PutMapping / @DeleteMapping
- Shortcut annotations for specific HTTP operations:
  - `@GetMapping` → HTTP GET
  - `@PostMapping` → HTTP POST
  - `@PutMapping` → HTTP PUT
  - `@DeleteMapping` → HTTP DELETE
- Provide cleaner, more readable request mappings.

Example:
```java
@GetMapping("/users")
public List<User> getUsers() { ... }
```
---

## 8. @PathVariable / @RequestParam
- @PathVariable
  - Extracts values from the URL path.
  - Example:
    `/users/10` → `@PathVariable int id`
- @RequestParam
  - Extracts query parameters.
  - Example:
    - `/users?id=10` → `@RequestParam int id`

---

## 9. @RequestBody / @ResponseBody
- @RequestBody
  - Binds the HTTP request body to a method parameter.
  - Converts JSON → Java object.

Example:
```
@PostMapping("/users")
public User addUser(@RequestBody User user) { ... }
```
- @ResponseBody
  - Converts method return value to JSON/XML response.
  - Included implicitly in `@RestController`.

---

# Spring Boot Starter Dependencies

Spring Boot provides several starter dependencies to simplify project setup.  
Each starter is a pre-configured set of libraries for a specific feature.

---

## 1. spring-boot-starter-web
- Used for building web applications and REST APIs.
- Includes:
  - Spring MVC
  - Embedded Tomcat
  - Jackson (JSON support)
- Handles HTTP requests, controllers, JSON serialization.

**Example (Maven):**
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```
---

## 2. spring-boot-starter-data-jpa

Used for database operations using JPA and Hibernate.

Provides:
- Spring Data JPA
- Hibernate ORM
- Transaction management
- Simplifies CRUD operations through repositories.

**Example (Maven):**
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
```
---


## 3. spring-boot-starter-test

Used for unit and integration testing.

Includes:
- JUnit 5
- Mockito
- Spring Test
- AssertJ
- JSONassert

Provides test utilities for Spring Boot apps.

**Example (Maven):**
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-test</artifactId>
    <scope>test</scope>
</dependency>
```
---


## 4. spring-boot-starter-security

Adds Spring Security to the application.

Provides:
- Authentication
- Authorization
- Security filters
- Password encoding

Secures all endpoints by default.

**Example (Maven):**
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
</dependency>
```
---


## 5. spring-boot-starter-validation

Provides validation support.  
Based on Hibernate Validator.

Enables annotations like:
- `@NotNull`
- `@Size`
- `@Email`
- `@Min`
- `@Max`

**Example (Maven):**
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-validation</artifactId>
</dependency>
```
---

# Spring Boot Auto-Configuration

## What is Auto-Configuration?
Spring Boot auto-configuration automatically configures your application based on the dependencies available in the classpath.  
It removes the need for manual XML or Java configuration.

---

## How Auto-Configuration Works Internally

### 1. @EnableAutoConfiguration
This annotation (inside @SpringBootApplication) starts the auto-configuration process.

---


### 2. Auto-Configuration Class List
Spring Boot loads auto-configuration classes from:
- META-INF/spring.factories  
- or  
- META-INF/spring/org.springframework.boot.autoconfigure.AutoConfiguration.imports

These files contain a list of auto-configuration classes like:
- WebMvcAutoConfiguration  
- DataSourceAutoConfiguration  

---


### 3. Conditional Checks
Each auto-configuration class uses conditional annotations to decide whether to load or not.

---


### 4. Apply Only What Is Needed
If Spring Web is present → configure DispatcherServlet + Tomcat  
If Spring Data JPA is present → configure DataSource + Hibernate

---

## Conditional Annotations

- **@ConditionalOnClass** – Load only if a class exists in classpath  
- **@ConditionalOnMissingBean** – Load only if no existing bean is defined  
- **@ConditionalOnProperty** – Load if a property is set  
- **@ConditionalOnBean** – Load if another bean exists  
- **@ConditionalOnWebApplication** – Load only in web apps  

These annotations allow Spring Boot to load only required components.

---

## Custom Auto-Configuration

### Step 1: Create a configuration class
```java
@Configuration
public class MyAutoConfig {

    @Bean
    @ConditionalOnMissingBean
    public MyService myService() {
        return new MyService();
    }
}
```
### Step 2: Register the class
Create a file:
```
META-INF/spring/org.springframework.boot.autoconfigure.AutoConfiguration.imports
```

Add your class:
```
com.example.MyAutoConfig

```
Spring Boot will load it automatically.

---


## Excluding Auto-Configuration

### 1. Exclude using @SpringBootApplication
```
@SpringBootApplication(exclude = {
    DataSourceAutoConfiguration.class
})
public class MyApplication { }
```

---


### 2. Exclude in application.properties
```
spring.autoconfigure.exclude=\
org.springframework.boot.autoconfigure.jdbc.DataSourceAutoConfiguration
```

---


### 3. Exclude using @EnableAutoConfiguration
```
@EnableAutoConfiguration(exclude = SecurityAutoConfiguration.class)
```

---


## Summary

- Spring Boot configures your app automatically.
- Uses @EnableAutoConfiguration + a list of auto-config classes.
- Conditional annotations decide what loads.
- You can create custom auto-configuration.
- You can exclude unwanted auto-config.

# Spring Boot Configuration

## 1. application.properties / application.yml

Spring Boot uses these two files to store application settings.

### application.properties (key-value format)
```
server.port=8081
spring.datasource.username=root
spring.datasource.password=1234
```

### application.yml (YAML format)
```yaml
server:
  port: 8081

spring:
  datasource:
    username: root
    password: 1234
```

### Both are used to configure:
- Server settings
- Database connections
- Logging
- Security
- Custom variables

---

## 2. Profiles (dev, test, prod)

Profiles allow different settings for each environment.

### Activate a profile
```
spring.profiles.active=dev
```
### Profile-specific files
- application-dev.properties
- application-test.properties
- application-prod.properties

Example:

#### application-dev.yml
```
server:
  port: 8080
logging:
  level:
    root: DEBUG
```
#### application-prod.yml
```
server:
  port: 9000
logging:
  level:
    root: ERROR
```

---

## 3. @ConfigurationProperties

Used to bind a group of configuration values into a Java class.

Example

#### application.yml
```
app:
  name: StudentApp
  version: 1.0
```
### Java Class
```
@Component
@ConfigurationProperties(prefix = "app")
public class AppConfig {
    private String name;
    private String version;
    // getters & setters
}
```

Benefits:

- Type-safe configuration
- Cleaner than many @Value annotations

---

## 4. @Value Annotation

Used to inject a single property value.

#### application.properties
```
app.title=Spring Boot Application

```
Java
```
@Value("${app.title}")
private String title;

```
Default value:
```
@Value("${app.mode:default}")
private String mode;
```

---

## 5. External Config Loading

Spring Boot loads configuration in this order (highest priority first):

Command-line arguments
Environment variables
application.properties / application.yml
Profile-specific files
External config files
Classpath defaults
@PropertySource files
#### Example: External config file

Place a file next to the JAR:
```
custom-config.properties

```
Run:
```
java -jar app.jar --spring.config.location=custom-config.properties
```

Spring Boot will load it automatically.

---

## Summary

### application.properties / application.yml
- Used to configure application settings.
- `.properties` → key-value format.
- `.yml` → structured YAML format.
- Common configurations:
  - Server port
  - Database settings
  - Logging levels
  - Security configs
  - Custom variables

---

### Profiles (dev, test, prod)
- Allow different settings for each environment.
- Activated using:
`spring.profiles.active=dev`


- Profile-specific files:
- `application-dev.properties`
- `application-test.properties`
- `application-prod.properties`

---

## @ConfigurationProperties
- Binds multiple related configurations into a Java class.
- Clean and type-safe.
- Replaces repeated use of @Value.

---

## @Value Annotation
- Injects a single property value.
- Supports default values.
- Example:
```java
@Value("${app.name}")
private String name;
```
### External Config Loading
Spring Boot loads configuration in this priority order:

1. Command-line arguments
2. Environment variables
3. application.properties / application.yml
4. Profile-specific files
5. External config files
6. Classpath defaults
7. @PropertySource files

Allows overriding configurations without modifying the JAR.

# Spring Boot REST API

## 1. Creating Controllers
In Spring Boot, REST APIs are created using `@RestController`.

### Example:
```java
@RestController
@RequestMapping("/api")
public class UserController {

    @GetMapping("/users")
    public List<String> getUsers() {
        return List.of("John", "Emma", "Alex");
    }
}
```
- `@RestController` → returns JSON by default

`@RequestMapping` → sets base URL

`@GetMapping`, `@PostMapping`, etc. → map HTTP methods

---

## 2. ResponseEntity

ResponseEntity is used to return:

- Custom HTTP status codes
- Custom headers
- Body (data)

Example:
```
@GetMapping("/user/{id}")
public ResponseEntity<String> getUser(@PathVariable int id) {
    if (id == 1) {
        return ResponseEntity.ok("John");
    } else {
        return ResponseEntity.status(404).body("User Not Found");
    }
}
```
You can also set headers:
```
return ResponseEntity.ok()
        .header("Custom-Header", "Value")
        .body("Data");
```
---

## 3. Global Exception Handling

Centralized error-handling for REST APIs.

- No need to write try/catch in every controller.
- Handled using `@ControllerAdvice`.

---

## 4. @ControllerAdvice

Used with @ExceptionHandler to catch exceptions globally.

Example:
```
@ControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(ResourceNotFoundException.class)
    public ResponseEntity<String> handleNotFound(ResourceNotFoundException ex) {
        return ResponseEntity.status(404).body(ex.getMessage());
    }
}
```
Now, if any controller throws `ResourceNotFoundException`,
this handler will automatically send a 404 response.

---

## 5. Validation (JSR303)

JSR303 provides built-in validation annotations.

### Common annotations:

- `@NotNull`
- `@Size`
- `@Email`
- `@Min`
- `@Max`
- `@Pattern`
- `@NotBlank`

Example:
```
public class UserRequest {

    @NotBlank
    private String name;

    @Email
    private String email;

    @Min(18)
    private int age;
}
```
### Use @Valid in controller:
```
@PostMapping("/users")
public ResponseEntity<String> createUser(@Valid @RequestBody UserRequest request) {
    return ResponseEntity.ok("User Created");
}
```
If validation fails → Spring automatically returns a 400 Bad Request.

You can catch validation errors globally:
```
@ExceptionHandler(MethodArgumentNotValidException.class)
public ResponseEntity<String> handleValidationErrors(MethodArgumentNotValidException ex) {
    String msg = ex.getBindingResult().getFieldError().getDefaultMessage();
    return ResponseEntity.badRequest().body(msg);
}
```
---

## Spring Boot REST API – Summary

### Creating Controllers
- Use `@RestController` to build REST APIs.
- Map endpoints using:
  - `@GetMapping`
  - `@PostMapping`
  - `@PutMapping`
  - `@DeleteMapping`
- `@RequestMapping` defines base URL.

---

### ResponseEntity
- Used to return:
  - Custom HTTP status
  - Custom headers
  - Response body
- Example usage:
  - `ResponseEntity.ok(body)`
  - `ResponseEntity.status(404).body("Not Found")`

---

### Global Exception Handling
- Centralized error handling for all controllers.
- Created using `@ControllerAdvice`.

---

### @ControllerAdvice
- Works with `@ExceptionHandler`.
- Catches exceptions globally.
- Prevents repeating try/catch in each controller.

---

### Validation (JSR303)
- Used to validate request bodies.
- Common annotations:
  - `@NotNull`
  - `@NotBlank`
  - `@Size`
  - `@Email`
  - `@Min`, `@Max`
- Apply using:
  - `@Valid` in controller method
- Spring returns **400 Bad Request** if validation fails.

---

# Spring Boot with JPA & Hibernate

## 1. Entity Mapping
Entity classes map Java objects to database tables using JPA annotations.

### Common Annotations:
- `@Entity` – marks class as JPA entity
- `@Table` – specifies table name
- `@Id` – primary key
- `@GeneratedValue` – auto ID generation
- `@Column` – custom column mapping
- `@OneToOne`, `@OneToMany`, `@ManyToOne`, `@ManyToMany` – relationships

### Example:
```java
@Entity
@Table(name = "users")
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(nullable = false)
    private String name;
}
```

## 2. Repositories (CrudRepository, JpaRepository)

Spring Data JPA provides built-in repository interfaces.

### CrudRepository
Used for basic CRUD operations.

#### Methods:
- save()
- findById()
- findAll()
- deleteById()

---

### JpaRepository
Extends CrudRepository and adds additional features for pagination and sorting.

#### Extra Methods:
- findAll(Sort sort)
- findAll(Pageable pageable)
- flush()
- saveAndFlush()

#### Example:
```java
public interface UserRepository extends JpaRepository<User, Long> {
}
```
---

## 3. JPQL & Native Queries

### JPQL (Java Persistence Query Language)
- Object-oriented query language.
- Uses **entity names**, not table names.

#### Example:
```java
@Query("SELECT u FROM User u WHERE u.name = :name")
List<User> findByName(@Param("name") String name);
```
### Native SQL Queries

- Uses actual SQL syntax.
- Useful for complex or performance-heavy queries.

Example:
```java
@Query(value = "SELECT * FROM users WHERE age > :age", nativeQuery = true)
List<User> getUsersByAge(@Param("age") int age);
```
---

## 4. Pagination & Sorting
### Pagination:
```java
Pageable pageable = PageRequest.of(0, 5);
Page<User> users = userRepository.findAll(pageable);
```
### Sorting:
```java
List<User> users = userRepository.findAll(Sort.by("name").ascending());
```

### Pagination + Sorting:
```java
Pageable pageable = PageRequest.of(0, 5, Sort.by("age").descending());
Page<User> result = userRepository.findAll(pageable);
```
---

## 5. Transaction Management

Transactions ensure data consistency.
- Spring Boot uses Spring Transaction Management + Hibernate.
- Repository methods are automatically transactional.
- Rollback occurs by default on RuntimeException.

---

## 6. @Transactional

Used to apply transaction boundaries at method or class level.

Example:
```java
@Service
public class UserService {

    @Transactional
    public void updateUser(User user) {
        userRepository.save(user);
    }
}
```
### Features:

- Ensures atomic operations
- Automatically rolls back on RuntimeException
- Custom rollback rules possible

### Custom Example:
```java
@Transactional(rollbackFor = Exception.class)
public void process() {
    // code that must be atomic
}
```
---

## JPA & Hibernate – Summary

### JPQL & Native Queries
- **JPQL**
  - Object-oriented query language.
  - Uses **entity names**, not table names.
  - Example:
    ```java
    @Query("SELECT u FROM User u WHERE u.name = :name")
    List<User> findByName(String name);
    ```

- **Native SQL**
  - Uses real SQL queries.
  - Useful for complex or optimized queries.
  - Example:
    ```java
    @Query(value = "SELECT * FROM users WHERE age > :age", nativeQuery = true)
    List<User> getUsersByAge(int age);
    ```

---

### Pagination & Sorting
- **Pagination**
  ```java
  Pageable p = PageRequest.of(0, 5);
  Page<User> users = repo.findAll(p);
  ```
- **Sorting**
```java
List<User> users = repo.findAll(Sort.by("name").ascending());
```
- **Pagination + Sorting**
```java
Pageable p = PageRequest.of(0, 5, Sort.by("age").descending());
Page<User> result = repo.findAll(p);
```

### Transaction Management

- Ensures data consistency.
- Spring Boot uses Spring Transaction Manager + Hibernate.
- Repository methods are transactional by default.
- Rolls back on RuntimeException automatically.

### @Transactional

- Marks methods or classes as transactional.
- Ensures atomic operations.
- Supports rollback rules.

Example:
```
@Transactional
public void updateUser(User user) {
    repo.save(user);
}
```

Custom rollback:
```
@Transactional(rollbackFor = Exception.class)
public void process() { }
```
---

# Spring Boot Database

## 1. H2 Database
- Lightweight in-memory database.
- Useful for testing and development.
- No installation required.
- Auto-configured by Spring Boot.

### Example configuration (application.properties):
```
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.h2.console.enabled=true
```
Access H2 console:
```
http://localhost:8080/h2-console
```

---

## 2. MySQL / PostgreSQL Integration

### MySQL Configuration:
```
spring.datasource.url=jdbc:mysql://localhost:3306/mydb
spring.datasource.username=root
spring.datasource.password=1234
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

MySQL Dependency:
```xml
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-j</artifactId>
</dependency>
```
### PostgreSQL Configuration:
```
spring.datasource.url=jdbc:postgresql://localhost:5432/mydb
spring.datasource.username=postgres
spring.datasource.password=1234
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```
PostgreSQL Dependency:
```xml
<dependency>
    <groupId>org.postgresql</groupId>
    <artifactId>postgresql</artifactId>
</dependency>
```
## 3. Connection Pooling
Spring Boot uses HikariCP as the default connection pool.

#### Benefits:

- Fastest JDBC connection pool
- Low memory usage
- High performance

### Configuration:
```
spring.datasource.hikari.maximum-pool-size=10
spring.datasource.hikari.minimum-idle=5
spring.datasource.hikari.connection-timeout=30000
spring.datasource.hikari.idle-timeout=600000
```
## 4. Flyway / Liquibase Migrations
### Flyway

- Version-based database migration tool.

- Uses SQL files stored in:
  ```
  src/main/resources/db/migration
  ```
#### Example migration file:
```
V1__create_user_table.sql
```
Contents:
```
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100)
);
```
Flyway Dependency:
```xml
<dependency>
    <groupId>org.flywaydb</groupId>
    <artifactId>flyway-core</artifactId>
</dependency>
```
### Liquibase

- XML, YAML, JSON, or SQL based migrations.
- Tracks changes in changelog files.
Example `db.changelog-master.yaml`:


































































































































# Upcoming Notes
8. Spring Boot Database

- H2 Database
- MySQL / PostgreSQL integration
- Connection Pooling
- Flyway/Liquibase migrations

---

9. Spring Boot Security

- Basic Auth
- JWT authentication
- Custom UserDetails
- PasswordEncoder
- Roles & Authorities

---

10. Spring Boot DevTools

- Auto restart
- Live reload
- Caching disable

---

11. Spring Boot Logging

- SLF4J
- Logback configuration
- Logging levels
- Custom log files

---

12. Spring Boot Actuator

- Actuator endpoints
- Health checks
- Metrics
- Custom actuator endpoints

---

13. Spring Boot Testing

- JUnit 5
- Mockito
- @SpringBootTest
- WebMvcTest
- TestRestTemplate
---
14. Spring Boot Microservices

- Service-to-service communication
- RestTemplate / WebClient
- Circuit breaker (Resilience4j)
- Spring Cloud basics
---
15. Spring Boot with Kafka / RabbitMQ

- Producer / Consumer setup
- Message Listener
- Configuration
---
16. Spring Boot Exception Handling

- @ControllerAdvice
- @ExceptionHandler
- Global error format
---
17. Spring Boot Filters & Interceptors

- HandlerInterceptor
- OncePerRequestFilter
- Request logging
---
18. Spring Boot File Upload/Download

- Multipart
- File storage
- Security considerations
---
19. Spring Boot Scheduling

- @EnableScheduling
- @Scheduled
- Cron expressions
---
20. Spring Boot Caching

- @EnableCaching
- @Cacheable
- @CacheEvict
- Redis caching
---
21. Spring Boot Deployment

- Packaging (Jar/War)
- Embedded server
- Deploy to AWS, Docker, Kubernetes
- External config on cloud

---
