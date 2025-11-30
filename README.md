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
---

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
---

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
```
databaseChangeLog:
  - changeSet:
      id: 1
      author: admin
      changes:
        - createTable:
            tableName: users
            columns:
              - column:
                  name: id
                  type: int
              - column:
                  name: name
                  type: varchar(100)
```
Liquibase Dependency:
```xml
<dependency>
    <groupId>org.liquibase</groupId>
    <artifactId>liquibase-core</artifactId>
</dependency>
```
---

## Spring Boot Database – Summary

### H2 Database
- Lightweight, in-memory database.
- Great for testing and quick development.
- Auto-configured by Spring Boot.
- H2 console available at `/h2-console`.
- No installation needed.

---

### MySQL / PostgreSQL Integration
- Spring Boot easily connects to both using JDBC URLs.
- Requires respective dependencies:
  - `mysql-connector-j`
  - `postgresql`
- Configure DB credentials in `application.properties`.
- Common JPA settings:
  - `spring.jpa.hibernate.ddl-auto=update`
  - `spring.jpa.show-sql=true`

---

### Connection Pooling (HikariCP)
- Spring Boot uses **HikariCP** as the default pool.
- Known for high performance.
- Key settings:
  - `maximum-pool-size`
  - `minimum-idle`
  - `connection-timeout`
  - `idle-timeout`

---

### Flyway / Liquibase Migrations
- Tools used for database schema versioning.

### Flyway:
- Migration files named as `V1__description.sql`
- Stored in `db/migration`
- Supports SQL-based migrations.

### Liquibase:
- Uses XML, YAML, JSON, or SQL changelog files.
- Tracks schema changes with `changelog-master`

---

# Spring Boot Security

## 1. Basic Authentication
Basic Authentication uses a username and password encoded in Base64 and sent in the HTTP header.

### How it works:
- Client sends request with header:
  **Authorization: Basic <Base64(username:password)>**
- Spring Security validates credentials.
- If valid → access granted  
- If invalid → `401 Unauthorized`

### Example configuration (in memory users):
```java
@Configuration
@EnableWebSecurity
public class SecurityConfig {

  @Bean
  public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
      http
          .authorizeHttpRequests(auth -> auth.anyRequest().authenticated())
          .httpBasic();
      return http.build();
  }

  @Bean
  public UserDetailsService userDetailsService() {
      UserDetails user = User.builder()
              .username("admin")
              .password(passwordEncoder().encode("1234"))
              .roles("ADMIN")
              .build();

      return new InMemoryUserDetailsManager(user);
  }

  @Bean
  public PasswordEncoder passwordEncoder() {
      return new BCryptPasswordEncoder();
  }
}
```
---

## 2. JWT Authentication

JWT (JSON Web Token) is used for **stateless authentication**.

### How JWT Works:
1. User logs in with **username + password**
2. Server validates credentials and issues a **JWT token**
3. Client sends token in header:
   **Authorization: Bearer <token>**
4. Server validates the token
5. If valid → user is authenticated
6. No session stored on the server (stateless)

### JWT Structure:
  **Header.Payload.Signature**
### Why JWT?
- No session storage needed
- Fast & scalable
- Best for microservices and distributed systems

### JWT Filter Example:
```java
public class JwtFilter extends OncePerRequestFilter {

    @Override
    protected void doFilterInternal(HttpServletRequest request,
                                    HttpServletResponse response,
                                    FilterChain chain)
                                    throws ServletException, IOException {

        String authHeader = request.getHeader("Authorization");

        if (authHeader != null && authHeader.startsWith("Bearer ")) {
            String token = authHeader.substring(7);
            // Validate token & set authentication
        }

        chain.doFilter(request, response);
    }
}
```
---

## 3. Custom UserDetails

Used to load user data from a **database** instead of in-memory.

### Step 1: Create User Entity
```java
@Entity
public class AppUser {
    @Id
    private Long id;
    private String username;
    private String password;
    private String role;
}
```
---

### Step 2: UserDetails Implementation
```java
public class CustomUserDetails implements UserDetails {

    private AppUser user;

    public CustomUserDetails(AppUser user) {
        this.user = user;
    }

    @Override
    public Collection<? extends GrantedAuthority> getAuthorities() {
        return List.of(new SimpleGrantedAuthority("ROLE_" + user.getRole()));
    }

    @Override
    public String getPassword() { 
        return user.getPassword(); 
    }

    @Override
    public String getUsername() { 
        return user.getUsername(); 
    }
}
```
---

### Step 3: Custom UserDetailsService
```java
@Service
public class CustomUserDetailsService implements UserDetailsService {

    @Autowired
    private UserRepository repo;

    @Override
    public UserDetails loadUserByUsername(String username)
            throws UsernameNotFoundException {

        AppUser user = repo.findByUsername(username)
                .orElseThrow(() -> new UsernameNotFoundException("User Not Found"));

        return new CustomUserDetails(user);
    }
}
```
---

## 4. PasswordEncoder

Used to hash passwords before saving into the database.

### Most Common Encoder:
```java
@Bean
public PasswordEncoder passwordEncoder() {
    return new BCryptPasswordEncoder();
}
```
### bWhy use PasswordEncoder?

- Never store plain passwords
- BCrypt automatically applies hashing + salt
- Provides strong security for authentication systems

#### Encoding Example:
```
String hashed = passwordEncoder.encode("1234");
```
---

## 5. Roles & Authorities

### Difference:
- **Role:** High-level permission  
  Example → `ROLE_ADMIN`

- **Authority:** Specific permission  
  Example → `READ_PRIVILEGE`, `WRITE_PRIVILEGE`

### Internal Conversion:
Spring automatically converts:
  **role "ADMIN" → authority "ROLE_ADMIN"**
  
---

### Using Roles:
```java
.authorizeHttpRequests(auth ->
    auth.requestMatchers("/admin/**").hasRole("ADMIN")
)
```
### Using Authorities:
```java
.authorizeHttpRequests(auth ->
    auth.requestMatchers("/read").hasAuthority("READ_PRIVILEGE")
)
```
### Assign roles:
```java
new SimpleGrantedAuthority("ROLE_ADMIN");
```
### Assign custom authorities:
```java
new SimpleGrantedAuthority("READ_PRIVILEGE");
```
---

## Summary (Quick Review)

- Basic Auth: Simple Base64 authentication
- JWT Auth: Stateless token-based authentication
- Custom UserDetails: Load user data from database
- PasswordEncoder: Use BCrypt to hash passwords
- Roles & Authorities: Permission handling for secured endpoints

---

# Spring Boot DevTools

## Auto Restart
- DevTools automatically restarts the application when it detects classpath changes.
- Useful during development for rapid testing.
- Only restarts on **compiled class changes**, not on static files.

### How to enable:
Just add the dependency:
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-devtools</artifactId>
    <optional>true</optional>
</dependency>
```
## Live Reload

- Automatically refreshes the browser when **HTML, CSS, or JS** changes.
- Requires the **LiveReload browser extension**.
- Works with frameworks like:
  - Thymeleaf  
  - React  
  - Angular (with proper setup)

### How it works:
1. DevTools detects a file change  
2. Server restarts or reloads  
3. Browser auto-refreshes automatically  

---

## Caching Disable

Spring Boot DevTools disables template caching during development.

### Ensures live updates for:
- Thymeleaf templates  
- Freemarker  
- JSP  
- Static resources (CSS, JS, images)

You see changes instantly without manually restarting the application.

### Example (Thymeleaf caching disabled):
```
spring.thymeleaf.cache=false
```
DevTools applies this behavior automatically in development mode.

---
# Spring Boot DevTools – Summary

## Live Reload
- Automatically refreshes the browser when HTML, CSS, or JS changes.
- Requires the LiveReload browser extension.
- Works with Thymeleaf, React, and Angular.
- Process:
  1. DevTools detects file change  
  2. Server reloads  
  3. Browser auto-refreshes  

---

## Caching Disable
- DevTools turns off template & static resource caching in development.
- Ensures immediate updates for:
  - Thymeleaf templates
  - Freemarker
  - JSP
  - Static resources (CSS, JS, images)
- Example configuration:
```
spring.thymeleaf.cache=false
```
- DevTools applies this automatically during development.

---

# Spring Boot Logging

## 1. SLF4J
- SLF4J (Simple Logging Facade for Java) is the standard logging API used in Spring Boot.
- It provides a common interface and allows plugging different logging frameworks.
- Spring Boot uses **Logback** as the default implementation.

### Example usage:
```java
private static final Logger logger = LoggerFactory.getLogger(MyClass.class);

logger.info("Info message");
logger.debug("Debug message");
logger.error("Error message");
```
---

## 2. Logback Configuration

Logback is the default logging framework in Spring Boot.

### Custom Logback file:
Create the file:
 ```src/main/resources/logback-spring.xml```

### Example configuration:
```xml
<configuration>
    <appender name="CONSOLE" class="ch.qos.logback.core.ConsoleAppender">
        <encoder>
            <pattern>%d{yyyy-MM-dd HH:mm:ss} - %msg%n</pattern>
        </encoder>
    </appender>

    <root level="INFO">
        <appender-ref ref="CONSOLE" />
    </root>
</configuration>
```
### Features:

- Change log patterns
- Create multiple appenders (Console, File, RollingFile)
- Set log levels for specific packages

---

## 3. Logging Levels

Spring Boot supports the following logging levels:

- TRACE (most detailed)
- DEBUG
- INFO
- WARN
- ERROR
- OFF (disable logging)

### Set logging level in `application.properties`:
```
logging.level.root=INFO
logging.level.com.example=DEBUG
```

### Set logging level in YAML:
```yaml
logging:
  level:
    root: INFO
    com.example: DEBUG
```
---

## 4. Custom Log Files

By default, Spring Boot logs to the console.  
You can configure logs to be written to files.

### Write logs to a file:
 ```
logging.file.name=app.log
```

### Or specify a directory:
```
logging.file.path=logs/
```

### Customize file size, rotation, and history:
```
logging.logback.rollingpolicy.max-file-size=10MB
logging.logback.rollingpolicy.max-history=7
```

### Example Logback file with file appender:
```xml
<appender name="FILE" class="ch.qos.logback.core.rolling.RollingFileAppender">
    <file>logs/app.log</file>
    <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
        <fileNamePattern>logs/app-%d{yyyy-MM-dd}.log</fileNamePattern>
    </rollingPolicy>
    <encoder>
        <pattern>%d{HH:mm:ss} [%thread] %-5level %logger - %msg%n</pattern>
    </encoder>
</appender>

<root level="INFO">
    <appender-ref ref="FILE" />
</root>
```

---

## Custom Log Files – Summary

- Spring Boot logs to the console by default.
- You can enable logging to a file using:
 ```
 logging.file.name=app.log
```
- Or specify a directory for logs:
```
logging.file.path=logs/
```
- Log rotation and history can be customized:
```
logging.logback.rollingpolicy.max-file-size=10MB
logging.logback.rollingpolicy.max-history=7
```
- Logback allows full customization of log files using `logback-spring.xml`.
- Example includes:
- File appender  
- Rolling policy  
- Custom log pattern  

---

# Spring Boot Actuator

## 1. Actuator Endpoints
Actuator provides built-in endpoints to monitor and manage your Spring Boot application.

Common endpoints:
- `/actuator/health` — Shows application health
- `/actuator/info` — Shows custom app info
- `/actuator/metrics` — Exposes application metrics
- `/actuator/env` — Shows environment properties
- `/actuator/beans` — Shows all Spring beans
- `/actuator/mappings` — Shows all request mappings

### Enable all actuator endpoints:
```
management.endpoints.web.exposure.include=*
```

---

## 2. Health Checks
The **health** endpoint shows the current status of the application.

### Basic health check:
 `/actuator/health`

Output:
```
{
"status": "UP"
}
```

### Spring Boot automatically checks:
- Disk space  
- Database connectivity  
- Redis  
- Custom indicators  

### Enable detailed health info:
```
management.endpoint.health.show-details=always
```

---

## 3. Metrics
Actuator collects many useful metrics.

### Common metrics:
- `jvm.memory.used`
- `jvm.cpu.usage`
- `http.server.requests` (number of requests)
- `system.cpu.usage`
- `process.uptime`

### View all metrics:
`/actuator/metrics`

### View a specific metric:
`/actuator/metrics/jvm.memory.used`

### These metrics can be integrated with tools like:
- Prometheus  
- Grafana  
- Micrometer  

---

## 4. Custom Actuator Endpoints
You can create your own actuator endpoints.

### Example: Custom Endpoint
```java
@Component
@Endpoint(id = "custominfo")
public class CustomInfoEndpoint {

    @ReadOperation
    public Map<String, String> customInfo() {
        return Map.of("status", "running", "version", "1.0");
    }
}
```
Access custom endpoint:
`/actuator/custominfo`

---

## Spring Boot Actuator – Summary

### Actuator Endpoints
- Provides built-in monitoring endpoints.
- Common endpoints:
  - `/actuator/health`
  - `/actuator/info`
  - `/actuator/metrics`
  - `/actuator/env`
  - `/actuator/beans`
  - `/actuator/mappings`
- Enable all endpoints:
```
management.endpoints.web.exposure.include=*
```

---

### Health Checks
- Shows application health status (`UP`, `DOWN`).
- Checks components like:
- Disk space
- Database connection
- Custom health indicators
- Show detailed health info:
```
management.endpoint.health.show-details=always
```

---

### Metrics
- Provides runtime metrics such as:
- `jvm.memory.used`
- `system.cpu.usage`
- `http.server.requests`
- `process.uptime`
- View all metrics:
  `/actuator/metrics`

---

### Custom Actuator Endpoints
- You can create your own custom endpoint using:
```java
@Endpoint(id = "custominfo")
@ReadOperation
```
- Access custom endpoint:

`/actuator/custominfo`

# Spring Boot Testing

## 1. JUnit 5
- Default testing framework in Spring Boot.
- Provides annotations for writing unit tests.
- Common annotations:
  - `@Test` — marks a test method
  - `@BeforeEach` — runs before each test
  - `@AfterEach` — runs after each test
  - `@DisplayName` — custom test name

### Example:
```java
@Test
void testAddition() {
    assertEquals(4, 2 + 2);
}
```
---

## 2. Mockito

Used for mocking dependencies in unit tests.  
Helps test classes in isolation by mocking services, repositories, etc.

### Common Annotations:
- `@Mock` — creates a mock object  
- `@InjectMocks` — injects mocks into the target class  
- `when(...).thenReturn(...)` — define mock behavior  

### Example:
```java
@Mock
UserRepository repo;

@InjectMocks
UserService service;

@Test
void testFindUser() {
    when(repo.findById(1L)).thenReturn(Optional.of(new User(1L, "John")));
    assertEquals("John", service.getUser(1L).getName());
}
```
---

## 3. @SpringBootTest

Loads the **entire Spring Boot application context** for integration testing.  
Suitable for **end-to-end testing**.

### Example:
```java
@SpringBootTest
class ApplicationTests {

    @Test
    void contextLoads() { }
}
```
### Dependency Injection Example:
```java
@Autowired
UserService service;
```
---

## 4. @WebMvcTest

Used to test **only the controller layer**.  
Does **not** load the full Spring context.  
Automatically configures **MockMvc** for controller testing.

### Example:
```java
@WebMvcTest(UserController.class)
class UserControllerTest {

    @Autowired
    private MockMvc mockMvc;

    @Test
    void testGetUsers() throws Exception {
        mockMvc.perform(get("/users"))
               .andExpect(status().isOk());
    }
}
```
---

## 5. TestRestTemplate

Used for **integration testing of REST APIs**.  
It sends **real HTTP requests** to your running Spring Boot application, making it suitable for full end-to-end testing.

### Example:
```java
@SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)
class ApiTest {

    @Autowired
    private TestRestTemplate restTemplate;

    @Test
    void testGetUsers() {
        String response = restTemplate.getForObject("/users", String.class);
        assertNotNull(response);
    }
}
```
---

## TestRestTemplate – Summary

- Used for **integration testing** of REST APIs.
- Sends **real HTTP requests** to the application.
- Works with `@SpringBootTest` using a random or defined port.
- Allows testing:
  - GET, POST, PUT, DELETE endpoints
  - Request/response bodies
  - Status codes

### Key Features:
- Simple to use
- Great for end-to-end API tests
- Works with full Spring context loaded

### Example (simple GET test):
```java
String response = restTemplate.getForObject("/users", String.class);
assertNotNull(response);
```
---

# Spring Boot Microservices

## 1. Service-to-Service Communication
In a microservices architecture, services need to communicate with each other.

### Two ways:
- **Synchronous communication** → REST API calls  
- **Asynchronous communication** → Message queues (Kafka, RabbitMQ)

Common patterns:
- Direct REST call (RestTemplate / WebClient)
- API Gateway
- Service Registry (Eureka)
- Load balancing (Spring Cloud LoadBalancer)

---

## 2. RestTemplate / WebClient

### RestTemplate (Older, Blocking)
- Synchronous (blocking) REST client.
- Easy to use but not recommended for new projects.

#### Example:
```java
RestTemplate restTemplate = new RestTemplate();
String response = restTemplate.getForObject("http://service-a/data", String.class);
```
---

## WebClient (Modern, Non-blocking)

- Asynchronous, non-blocking **reactive REST client**.
- Recommended in Spring Boot 2+ and Spring WebFlux.
- Better performance for microservices due to reactive I/O.

### Example:
```java
WebClient client = WebClient.create();

String response = client.get()
        .uri("http://service-a/data")
        .retrieve()
        .bodyToMono(String.class)
        .block();
```
---

## 3. Circuit Breaker (Resilience4j)

Circuit breakers prevent cascading failures by **stopping repeated calls to failing services**.

### Why use circuit breakers?
- Avoid overload when a service is down  
- Improve fault tolerance  
- Provide fallback responses  
- Protect the entire microservice chain  

### Add Resilience4j dependency:
```xml
<dependency>
    <groupId>io.github.resilience4j</groupId>
    <artifactId>resilience4j-spring-boot2</artifactId>
</dependency>
```
#### Example:
```java
@CircuitBreaker(name = "serviceA", fallbackMethod = "fallbackResponse")
public String callServiceA() {
    return restTemplate.getForObject("http://service-a/data", String.class);
}

public String fallbackResponse(Exception ex) {
    return "Service A is down";
}
```
---

## 4. Spring Cloud Basics

Spring Cloud provides essential tools for building **scalable, distributed microservices**.

### Important Components:

---

### 1. Service Discovery (Eureka Server)
- Services register themselves dynamically  
- Other services discover them automatically  
- Eliminates hardcoded URLs  
- Enables dynamic scaling of instances  

---

### 2. API Gateway (Spring Cloud Gateway)
Acts as the single entry point for all microservices.

Supports:
- Authentication  
- Logging  
- Rate limiting  
- Path rewriting  
- Centralized routing  
- Cross-cutting concerns (security, monitoring)

---

### 3. Config Server
Used for **centralized configuration management** across microservices.

Features:
- Stores configuration in:
  - Git (most common)
  - File system
  - HashiCorp Vault  
- Microservices load config at startup  
- Supports dynamic refresh using:
  `/actuator/refresh`
 
---

### 4. Load Balancing (Spring Cloud LoadBalancer)
- Distributes requests across multiple service instances  
- Replaces Netflix Ribbon (deprecated)  
- Provides **client-side load balancing**  
- Works well with Eureka and Feign clients  

---

### 5. Feign Client
Declarative REST client for easy service-to-service communication.

#### Example:
```java
@FeignClient(name = "service-a")
public interface ServiceAClient {

  @GetMapping("/data")
  String getData();
}
```
---

# Spring Boot with Kafka / RabbitMQ

## 1. Producer / Consumer Setup

### Kafka Producer
Used to send messages to a Kafka topic.

```java
@Autowired
private KafkaTemplate<String, String> kafkaTemplate;

public void sendMessage(String msg) {
    kafkaTemplate.send("my-topic", msg);
}
```
### Kafka Consumer
Listens to messages from a Kafka topic.
```java
@KafkaListener(topics = "my-topic", groupId = "group1")
public void listen(String message) {
    System.out.println("Received: " + message);
}
```
### RabbitMQ Producer
Sends messages to a queue or exchange.
```java
@Autowired
private RabbitTemplate rabbitTemplate;

public void sendMessage(String msg) {
    rabbitTemplate.convertAndSend("myQueue", msg);
}
```
### RabbitMQ Consumer
Listens to messages from RabbitMQ.
```java
@RabbitListener(queues = "myQueue")
public void receive(String message) {
    System.out.println("Received: " + message);
}
```
## 2. Message Listener

### Kafka Listener
Triggered automatically when a message arrives.
```java
@KafkaListener(topics = "orders", groupId = "order-group")
public void consumeOrder(String message) {
    System.out.println("Order Received: " + message);
}
```
### RabbitMQ Listener
Used to consume messages asynchronously.
```java
@RabbitListener(queues = "orderQueue")
public void processOrder(String order) {
    System.out.println("Order Received: " + order);
}
```
## 3. Configuration
### Kafka Configuration (application.properties)
```
spring.kafka.bootstrap-servers=localhost:9092
spring.kafka.consumer.group-id=myGroup
spring.kafka.consumer.auto-offset-reset=earliest
spring.kafka.consumer.key-deserializer=org.apache.kafka.common.serialization.StringDeserializer
spring.kafka.consumer.value-deserializer=org.apache.kafka.common.serialization.StringDeserializer
spring.kafka.producer.key-serializer=org.apache.kafka.common.serialization.StringSerializer
spring.kafka.producer.value-serializer=org.apache.kafka.common.serialization.StringSerializer
```

### RabbitMQ Configuration (application.properties)
```
spring.rabbitmq.host=localhost
spring.rabbitmq.port=5672
spring.rabbitmq.username=guest
spring.rabbitmq.password=guest
```
### Queue/Exchange/Binding Configuration:
```java
@Bean
public Queue queue() {
    return new Queue("myQueue", false);
}
```
## Spring Boot with Kafka / RabbitMQ – Summary

### Producer / Consumer Setup

#### Kafka
- **Producer:** Sends messages using `KafkaTemplate`.
- **Consumer:** Listens to topics using `@KafkaListener`.

#### RabbitMQ
- **Producer:** Sends messages using `RabbitTemplate`.
- **Consumer:** Listens to queues using `@RabbitListener`.

---

### Message Listener

#### Kafka Listener
- Automatically triggered when a message arrives in a topic.
- Uses:
  ```java
  @KafkaListener(topics = "topicName")
  ```
#### RabbitMQ Listener
- Consumes messages from a queue.
- Uses:
 ```java
@RabbitListener(queues = "queueName")
 ```
### Configuration
#### Kafka (application.properties)
- Set bootstrap server
- Configure producer & consumer serializers
- Set consumer group-id
#### RabbitMQ (application.properties)
- Configure host, port, username, password
- Declare queues, exchanges, and bindings via @Bean

# Spring Boot Exception Handling

## 1. @ControllerAdvice
- Used to handle exceptions **globally** for all controllers.
- Centralizes error handling into one class.
- Eliminates repeated try/catch blocks in controllers.

### Example:
```java
@ControllerAdvice
public class GlobalExceptionHandler { }
```
---

## 2. @ExceptionHandler

Used inside `@ControllerAdvice` to catch specific exceptions and return custom responses.

### Example:
```java
@ExceptionHandler(ResourceNotFoundException.class)
public ResponseEntity<String> handleNotFound(ResourceNotFoundException ex) {
    return ResponseEntity.status(404).body(ex.getMessage());
}
```
## Handling Multiple Exceptions

You can catch multiple exceptions using a single `@ExceptionHandler`.

### Example:
```java
@ExceptionHandler({NullPointerException.class, IllegalArgumentException.class})
public ResponseEntity<String> handleErrors(Exception ex) {
    return ResponseEntity.badRequest().body(ex.getMessage());
}
```
---

## 3. Global Error Format

Spring Boot allows returning a **consistent JSON error structure** for all exceptions, improving clarity and standardizing API error responses.

---

### Example JSON Error Format:
```json
{
  "timestamp": "2024-01-01T10:00:00",
  "status": 404,
  "error": "Not Found",
  "message": "User not found",
  "path": "/api/users/5"
}
```
### Example Custom Error Response Class:
```java
public class ErrorResponse {
    private LocalDateTime timestamp;
    private int status;
    private String error;
    private String message;
    private String path;
}
```
### Global Exception Handler Returning Custom Format:
```java
@ExceptionHandler(ResourceNotFoundException.class)
public ResponseEntity<ErrorResponse> handleNotFound(ResourceNotFoundException ex, HttpServletRequest req) {

    ErrorResponse error = new ErrorResponse(
            LocalDateTime.now(),
            404,
            "Not Found",
            ex.getMessage(),
            req.getRequestURI()
    );

    return ResponseEntity.status(404).body(error);
}
```
---

## Global Error Format – Summary

- A consistent JSON error structure makes API responses more readable and standardized.
- Common fields include:
  - `timestamp`
  - `status`
  - `error`
  - `message`
  - `path`

### JSON Error Example:
```json
{
  "timestamp": "2024-01-01T10:00:00",
  "status": 404,
  "error": "Not Found",
  "message": "User not found",
  "path": "/api/users/5"
}
```
### Custom Error Class:
Holds structured error information for all exceptions.

### Global Handler:
A global `@ExceptionHandler` returns the custom error format for exceptions, ensuring consistent responses across the application.

---

# Spring Boot Filters & Interceptors

## 1. HandlerInterceptor

HandlerInterceptor is used to intercept requests **before** they reach the controller and **after** the request is processed.

### Methods:
- `preHandle()` → runs before controller
- `postHandle()` → runs after controller
- `afterCompletion()` → runs after request completes

### Example:
```java
public class MyInterceptor implements HandlerInterceptor {

    @Override
    public boolean preHandle(HttpServletRequest request,
                             HttpServletResponse response, Object handler) {
        System.out.println("Before Controller: " + request.getRequestURI());
        return true; // continue request
    }

    @Override
    public void postHandle(HttpServletRequest request,
                           HttpServletResponse response,
                           Object handler, ModelAndView modelAndView) {
        System.out.println("After Controller");
    }

    @Override
    public void afterCompletion(HttpServletRequest request,
                                HttpServletResponse response,
                                Object handler, Exception ex) {
        System.out.println("Request Completed");
    }
}
```
## Register Interceptor:
```java
@Configuration
public class WebConfig implements WebMvcConfigurer {
    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(new MyInterceptor());
    }
}
```
---

## 2. OncePerRequestFilter

A filter that ensures the code executes **only once per request**, even during internal forwards or async operations.

### Common Uses:
- Authentication  
- Logging  
- JWT token validation  

### Example:
```java
public class MyFilter extends OncePerRequestFilter {

    @Override
    protected void doFilterInternal(HttpServletRequest request,
                                    HttpServletResponse response,
                                    FilterChain filterChain)
            throws ServletException, IOException {

        System.out.println("Filter Executed: " + request.getRequestURI());
        filterChain.doFilter(request, response);
    }
}
```
### Register Filter:
```java
@Configuration
public class FilterConfig {

    @Bean
    public FilterRegistrationBean<MyFilter> loggingFilter() {
        FilterRegistrationBean<MyFilter> bean = new FilterRegistrationBean<>();
        bean.setFilter(new MyFilter());
        bean.addUrlPatterns("/*");
        return bean;
    }
}

```
---

## 3. Request Logging

Request logging can be implemented using **Filters** or **Interceptors** to track incoming HTTP requests.

### Logging using Filter
A Filter logs the request before passing it down the filter chain.

```java
public class RequestLoggingFilter extends OncePerRequestFilter {

    @Override
    protected void doFilterInternal(HttpServletRequest request,
                                    HttpServletResponse response,
                                    FilterChain filterChain)
            throws ServletException, IOException {

        System.out.println("Request: " + request.getMethod() + " " + request.getRequestURI());
        filterChain.doFilter(request, response);
    }
}
```
---

### Logging using Interceptor
An Interceptor logs the request before it reaches the controller.
```java
@Override
public boolean preHandle(HttpServletRequest request,
                         HttpServletResponse response,
                         Object handler) {

    System.out.println("Incoming Request: " + request.getRequestURI());
    return true;
}
```
---

## Request Logging – Summary

- Request logging helps track incoming HTTP requests for debugging, monitoring, or auditing.

### Two Ways to Implement:

---

### 1. Using Filter  
- Executes before the request reaches the controller.  
- Good for global request logging.  

Example action:  
Logs method + request URI.

---

### 2. Using Interceptor  
- Runs before the controller handler method.  
- Useful when logging should apply only to specific controllers or paths.  

Example action:  
Logs incoming request URI.

Both approaches help in monitoring API traffic and understanding request flow.

---

# Spring Boot File Upload & Download

## 1. Multipart (File Upload)
Spring Boot supports file uploads using `MultipartFile`.

### Controller Example (Upload):
```java
@PostMapping("/upload")
public ResponseEntity<String> uploadFile(@RequestParam("file") MultipartFile file) throws IOException {
    String filename = file.getOriginalFilename();
    byte[] bytes = file.getBytes();
    return ResponseEntity.ok("Uploaded: " + filename);
}
```
### application.properties:
```
spring.servlet.multipart.max-file-size=10MB
spring.servlet.multipart.max-request-size=10MB
```
---

## 2. File Storage

Uploaded files can be stored in:
- Local file system  
- Database (not recommended for large files)  
- Cloud storage (AWS S3, Azure Blob, GCP Storage)

### Save File to Local Folder:
```java
@PostMapping("/upload")
public String uploadFile(@RequestParam("file") MultipartFile file) throws Exception {

    Path path = Paths.get("uploads/" + file.getOriginalFilename());
    Files.copy(file.getInputStream(), path, StandardCopyOption.REPLACE_EXISTING);

    return "File saved!";
}
```
### Download File:
```java
@GetMapping("/download/{filename}")
public ResponseEntity<Resource> download(@PathVariable String filename) throws IOException {

    Path path = Paths.get("uploads/" + filename);
    Resource resource = new UrlResource(path.toUri());

    return ResponseEntity.ok()
            .header(HttpHeaders.CONTENT_DISPOSITION, "attachment; filename=" + filename)
            .body(resource);
}
```
---

## 3. Security Considerations

Important security best practices to follow when handling file uploads in Spring Boot:

### 1. Validate File Type
- Allow only safe file types: `.png`, `.jpg`, `.pdf`, `.txt`, etc.
- Block dangerous files such as: `.exe`, `.sh`, `.bat`, `.cmd`, `.php`, `.jsp`.

### 2. Restrict Upload Directory
Never upload files into classpath folders:

- `/static`
- `/templates`
- `/resources`

Always use a safe external folder, e.g.:

- `/uploads`
- `/var/app/uploads`
- Local or cloud storage

### 3. Limit File Size
Prevents large-file denial-of-service attacks:
```
spring.servlet.multipart.max-file-size=10MB
```
### 4. Sanitize Filename
Avoid path traversal attacks such as:
```
../../etc/passwd
```

Use Spring’s safe filename function:

```java
String safeName = StringUtils.cleanPath(file.getOriginalFilename());
```
---

## 5. Disable Execution Permission

- Store uploaded files in a **non-executable directory** so they can never run as scripts.
- Ensure uploaded files cannot be executed by the server (e.g., `.sh`, `.php`, `.jsp`).
- Never store uploaded files **inside the application’s classpath**, such as:
  - Inside the JAR
  - `/static`
  - `/templates`
  - `/resources`
- Always store them in a safe external directory like:
  - `/uploads`
  - `/var/app/uploads`

---

## 6. Use Authentication for File Download

- Protect sensitive or private files from unauthorized access.
- Ensure only **authenticated** and **authorized** users can download files.
- Integrate security layer checks (Spring Security) before sending file content.
- Verify user roles/permissions (e.g., **ADMIN**, **USER**) before allowing download.

Example considerations:
- A user should download **only their own files**.
- Admin users may download all files.

---

## File Upload Security – Summary

### Disable Execution Permission
- Store uploaded files in a **non-executable** directory.
- Prevent uploaded files from running as scripts.
- Never store files inside classpath locations (`/static`, `/templates`, `/resources`, JAR).

### Use Authentication for File Download
- Protect sensitive files from unauthorized access.
- Allow downloads only for authenticated and authorized users.
- Validate user roles/permissions before sending file content.

---

# Spring Boot Scheduling

## 1. @EnableScheduling
- Enables scheduling support in Spring Boot.
- Must be added to the main application class or a configuration class.

### Example:
```java
@SpringBootApplication
@EnableScheduling
public class MyApp { }
```
---

## 2. @Scheduled

Used to run tasks automatically at fixed intervals, with delays, or using cron timings.  
Methods annotated with `@Scheduled` must be in a Spring-managed bean (e.g., `@Component` or `@Service`) and `@EnableScheduling` should be on a configuration or main class.

### Supported types

#### ✔ Fixed Rate (runs every X milliseconds)
```java
@Scheduled(fixedRate = 5000)
public void task() {
    System.out.println("Runs every 5 seconds");
}
```
- fixedRate schedules the next execution relative to the start time of the previous execution.

- If a task takes longer than the rate, executions may overlap (use locking or single-threaded scheduler to avoid overlap).

✔ Fixed Delay (waits after method completion)
```java
@Scheduled(fixedDelay = 3000)
public void task() {
    System.out.println("Runs 3 seconds after previous execution finishes");
}
```
`fixedDelay` schedules the next execution relative to the completion time of the previous execution.

---

✔ Initial Delay
```java
@Scheduled(initialDelay = 2000, fixedRate = 5000)
public void task() {
    System.out.println("Starts after 2 sec, then runs every 5 sec");
}
```
`initialDelay` delays the first execution after application start.

---

## 3. Cron Expressions

Cron expressions allow flexible scheduling using a time-based pattern.

### Cron Format (Spring uses 6 fields):
second minute hour day-of-month month day-of-week

> **Note:** Spring Boot uses a 6-field cron (includes seconds).  
> Traditional Linux cron uses 5 fields (no seconds).

### Examples

#### ✔ Run every day at 10 AM:
```java
@Scheduled(cron = "0 0 10 * * *")
public void dailyTask() {}
```
---

✔ Run every minute:
```java
@Scheduled(cron = "0 * * * * *")
public void everyMinute() {}
```
---

✔ Run every Monday at 9 AM:
```java
@Scheduled(cron = "0 0 9 * * MON")
public void weeklyTask() {}
```
---

✔ Run every 5 seconds:
```java
@Scheduled(cron = "*/5 * * * * *")
public void everyFiveSeconds() {}
```
---

### Tips & Best Practices
✔ Enable Scheduling

Ensure `@EnableScheduling` is present in main application class.
```
@SpringBootApplication
@EnableScheduling
public class App { }
```
---

✔ Avoid Task Overlapping
- Use fixedDelay for long-running tasks.
- Or move heavy operations to another thread pool.
✔ Use a Dedicated Task Scheduler
For multiple concurrent scheduled tasks:
- Configure `ThreadPoolTaskScheduler`.
- Prevent tasks from blocking each other.

✔ Handle Clustered Applications
Prevent multiple instances from running the same job:
- Use distributed locks (Redis, DB lock)
- Use leader election (Spring Cloud Cluster)
- Use external schedulers (Quartz, Kubernetes CronJobs)

✔ Validate Cron Expressions

Use:
- Online cron testers
- Unit tests
   to avoid incorrect schedules.
---

## Cron Expressions – Summary

- Cron expressions define flexible time-based scheduling in Spring Boot.
- Spring uses a **6-field cron format**:  
  `second minute hour day-of-month month day-of-week`
- Allows scheduling tasks at specific times (daily, weekly, periodically, etc.).

### Common Examples
- Daily at 10 AM: `0 0 10 * * *`  
- Every minute: `0 * * * * *`  
- Every Monday at 9 AM: `0 0 9 * * MON`  
- Every 5 seconds: `*/5 * * * * *`

### Best Practices
- Always enable scheduling with `@EnableScheduling`.
- Avoid overlapping tasks (use `fixedDelay` or async execution).
- Use a dedicated `TaskScheduler` for multiple scheduled tasks.
- Prevent duplicate executions in clustered environments.
- Validate cron expressions before using them.

---

# Spring Boot Caching

## 1. @EnableCaching
Enables Spring's caching mechanism.

- Add this to your main class or a configuration class.
- Activates cache annotations like `@Cacheable`, `@CacheEvict`, `@CachePut`.

### Example:
```java
@SpringBootApplication
@EnableCaching
public class MyApp { }
```
---

## 2. @Cacheable

Used to **cache method results**.

- First method call → executes logic + stores result in cache.
- Subsequent calls with the same key → returns cached result (method not executed again).

### Example:
```java
@Cacheable(value = "users", key = "#id")
public User getUser(int id) {
    System.out.println("Fetching from DB...");
    return userRepository.findById(id).orElse(null);
}
```
### Effect:

- First call: Hits database
- Later calls: Returns cached user object

---

## 3. @CacheEvict

Used to **remove data from the cache**, either a specific entry or the entire cache.

### Remove a specific cache entry:
```java
@CacheEvict(value = "users", key = "#id")
public void deleteUser(int id) {
    userRepository.deleteById(id);
}
```
### Remove all entries from a cache:
```java
@CacheEvict(value = "users", allEntries = true)
public void clearCache() {}
```
---

## 4. Redis Caching

Redis is the most popular **in-memory distributed cache** used with Spring Boot.  
It offers extremely fast read/write operations, making it ideal for:

- Caching API responses  
- Session storage  
- Frequently accessed data  
- Reducing database load  

### Add Redis Dependency:
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-redis</artifactId>
</dependency>
```
### application.properties Configuration:
```
spring.redis.host=localhost
spring.redis.port=6379
spring.cache.type=redis
```
This enables Spring Cache to use Redis as the caching provider.

### Optional Cache Configuration (Expiry Time):
```
@Bean
public RedisCacheConfiguration cacheConfig() {
    return RedisCacheConfiguration.defaultCacheConfig()
        .entryTtl(Duration.ofMinutes(10)); // cache expiry
}
```
- This sets a 10-minute TTL (time-to-live) for each cached entry.
### Example using Redis Cache:
```
@Cacheable(value = "products", key = "#id")
public Product getProduct(int id) {
    return productRepository.findById(id).orElse(null);
}
```
- First call → fetches from DB + stores in Redis
- Next calls → returns cached object from Redis

---

## Redis Caching – Summary

- Redis is a fast, in-memory distributed cache commonly used with Spring Boot.
- It improves performance by reducing database calls and speeding up data retrieval.

### Key Points:
- Add Redis dependency using `spring-boot-starter-data-redis`.
- Configure Redis in `application.properties`:
```
spring.redis.host=localhost
spring.redis.port=6379
spring.cache.type=redis
```
- Optional: Set cache expiration (TTL) using `RedisCacheConfiguration`.
- Use `@Cacheable` to store method results in Redis:
```java
@Cacheable(value = "products", key = "#id")
```
- First call hits the DB; subsequent calls return cached data

---

# Spring Boot Deployment

## 1. Packaging (JAR / WAR)

### ✔ JAR Packaging (Most Common)
Spring Boot applications are typically packaged as **fat JARs**:

- Contains application code
- Includes all dependencies
- Comes with an **embedded server** (Tomcat/Jetty/Undertow)
- Runs anywhere with Java installed

### How to run:
  java -jar app.jar

### Why JAR is preferred:
- Simpler deployment
- No need for external server
- Best for microservices and containers

---

### ✔ WAR Packaging (For External Servers)
Used when deploying to traditional Java application servers:
- Apache Tomcat
- JBoss/WildFly
- WebLogic
- WebSphere

#### Requirements:
1. Set packaging to `war` in `pom.xml`
2. Set Tomcat dependency to *provided*
3. Extend `SpringBootServletInitializer`

```java
@SpringBootApplication
public class App extends SpringBootServletInitializer { }
```
WAR is used mainly in legacy environments.

---

## 2. Embedded Server

Spring Boot includes a pre-configured embedded server so applications can run independently without installing an external server.

### Supported Embedded Servers:
- **Tomcat (default)**
- **Jetty**
- **Undertow**

### Change Embedded Server (Jetty Example):
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-jetty</artifactId>
</dependency>
```
Advantages:

- No external server installation needed
- Faster startup times
- Ideal for microservices
- Very easy to containerize with Docker

---

## 3. Deployment Environments

### A. Deploy on AWS
#### 1. AWS EC2 Deployment

Steps:
- Upload the .jar file to EC2
- Install Java
- Run:
  ```
  java -jar app.jar
  ```
- Use Nginx/Apache as reverse proxy
- Use systemd to keep service running in background

---

#### 2. AWS Elastic Beanstalk

- Upload JAR/WAR
- Handles:
  - Auto-scaling
  - Load balancing
  - Zero-downtime deployments

  ---

#### 3. AWS ECS (Docker-based)

- Package Spring Boot in Docker
- Push image to ECR (AWS container registry)
- Run as ECS service/task in a cluster
- Use ALB (Application Load Balancer)

#### 4. AWS Lambda (Serverless)

- Convert Spring Boot using Spring Cloud Function
- Very cheap → pay-per-execution
- Good for small apps or lightweight APIs

---

### B. Deploy with Docker
#### Dockerfile Example:
```
FROM openjdk:17
COPY target/app.jar app.jar
ENTRYPOINT ["java", "-jar", "/app.jar"]
```
#### Build Docker Image:
```
docker build -t myapp .
```
#### Run Container:
```
docker run -p 8080:8080 myapp
```
### Benefits:

- Same environment everywhere
- Easiest deployment for cloud platforms
- Works well with Kubernetes

---

## C. Kubernetes Deployment

### Deployment YAML:
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: spring-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: spring-app
  template:
    metadata:
      labels:
        app: spring-app
    spec:
      containers:
        - name: spring-app
          image: myapp:latest
          ports:
            - containerPort: 8080
```
---

### Service YAML:
```
apiVersion: v1
kind: Service
metadata:
  name: spring-service
spec:
  type: LoadBalancer
  ports:
    - port: 80
      targetPort: 8080
  selector:
    app: spring-app

```
---

#### Kubernetes Features:

- Auto-scaling (HPA)
- Rolling updates
- Self-healing (restarts failed pods)
- Built-in load balancing
  
---

## 4. External Configuration in Cloud

Spring Boot supports external config so you don't bundle configurations inside the JAR.

### Ways to Provide External Config:

External `application.yml` or `application.properties`
- Environment variables
- Command-line arguments
- Spring Cloud Config Server
- Kubernetes ConfigMaps / Secrets
- AWS Parameter Store / Secrets Manager
- Docker environment variables

### A. External Properties/YAML

Run app using an external config file:
```
java -jar app.jar --spring.config.location=/config/app.yml
```
---

### B. Environment Variables
Example:
```
export SERVER_PORT=9090
```
---

### C. Spring Cloud Config Server

- Stores config in Git
- Microservices fetch config on startup
- Supports live refresh using /actuator/refresh

#### Example (bootstrap.yml):
```
spring:
  cloud:
    config:
      uri: http://config-server:8888
```
---

### D. Kubernetes ConfigMap:
```
apiVersion: v1
kind: ConfigMap
metadata:
  name: spring-config
data:
  application.properties: |
    server.port=8081
```
---

### E. Secrets (Encrypted values)

Used to store:
- Database passwords
- API keys
- Tokens
- Credentials

### Summary (Short)

- JAR → preferred for microservices
- WAR → used for legacy application servers
- Embedded Tomcat → default in Spring Boot
- Docker + Kubernetes → modern deployment standard
- AWS EC2 / ECS / Beanstalk → easy cloud hosting options
- External config → Environment variables, Config Server, ConfigMaps

---

## Spring Boot Deployment – Summary

### Embedded Server
- Spring Boot apps run with an embedded server (Tomcat, Jetty, Undertow).
- No external server installation needed.
- Ideal for microservices and Docker deployment.

---

### Deployment Options

#### ✔ AWS Deployments
- **EC2**: Upload JAR → run with `java -jar`.
- **Elastic Beanstalk**: Easy deployment with autoscaling and load balancing.
- **ECS (Docker)**: Container-based deployment using Docker + ECR + ALB.
- **Lambda**: Serverless deployment using Spring Cloud Function.

#### ✔ Docker Deployment
- Package app using a Dockerfile.
- Run anywhere with consistent environment.
- Works perfectly with Kubernetes.

#### ✔ Kubernetes Deployment
- Use Deployment + Service YAML.
- Supports auto-scaling, rolling updates, and self-healing.
- Ideal for large microservice systems.

---

### External Configuration
Spring Boot allows external config via:
- External `application.yml/properties`
- Environment variables
- Spring Cloud Config Server (Git-backed config)
- Kubernetes ConfigMaps/Secrets
- AWS Parameter Store / Secrets Manager

---

### Quick Takeaways
- **JAR** → best for microservices  
- **WAR** → legacy server deployments  
- **Docker + K8s** → modern cloud-native deployments  
- **External config** → essential for cloud environments  

---
