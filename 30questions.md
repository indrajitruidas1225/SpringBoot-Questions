
## 1. What is Spring Boot?

Spring Boot is an extension of the Spring Framework that **reduces boilerplate configuration** and helps create **standalone, production-ready applications quickly**.

### Why Spring Boot?

* No XML configuration
* Embedded servers
* Auto dependency management
* Faster development
---

## 2. Spring Boot vs Spring Framework

### Spring Framework

* Requires manual configuration
* Needs external server
* XML / Java config heavy

### Spring Boot

* Auto configuration
* Embedded server
* Opinionated defaults

👉 **Spring Boot = Spring Framework + Automation**

---

## 3. Main Features of Spring Boot (Explained)

### 1️⃣ Auto-Configuration

Automatically configures beans based on:

* Dependencies
* Classpath
* Properties

Example:

```java
DataSource, DispatcherServlet, Jackson
```

### 2️⃣ Embedded Server

* Runs application as a JAR
* No need for Tomcat installation

### 3️⃣ Starter Dependencies

Predefined dependency groups.

### 4️⃣ Actuator

Production monitoring endpoints.

### 5️⃣ Externalized Configuration

Different configs for dev, test, prod.

---

## 4. Spring Boot Starters (Explained)

Starters are **dependency descriptors**.

### Example

```xml
spring-boot-starter-web
```

Includes:

* Spring MVC
* Tomcat
* Jackson
* Validation

👉 Prevents version mismatch issues.

---

## 5. Creating Spring Boot App using Spring Initializr

### Steps

1. Go to `start.spring.io`
2. Choose project details
3. Select dependencies
4. Generate project

👉 Internally generates:

* Maven/Gradle config
* Main class
* Default structure

---

## 6. `@SpringBootApplication` (DETAILED)

```java
@SpringBootApplication
public class App {}
```

### It combines 3 annotations:

---

### 🔹 `@Configuration`

* Marks class as **configuration class**
* Used to define beans using `@Bean`

```java
@Configuration
public class AppConfig {
    @Bean
    public RestTemplate restTemplate() {
        return new RestTemplate();
    }
}
```

---

### 🔹 `@ComponentScan`

* Scans packages for Spring beans
* Registers:

  * @Component
  * @Service
  * @Repository
  * @Controller

👉 Scans **current package and sub-packages**

---

### 🔹 `@EnableAutoConfiguration`

* Automatically configures beans
* Based on:

  * Classpath
  * Dependencies
  * Properties

Example:
If `spring-boot-starter-web` exists → configures MVC automatically.

---

## 7. `application.properties` / `application.yml`

### Purpose

* Central configuration file
* Controls application behavior

### Examples

```properties
server.port=8081
spring.datasource.url=jdbc:mysql://localhost/db
```

---

## 8. Custom Port Configuration

```properties
server.port=9090
```

👉 Overrides default port 8080.

---

## 9. Spring Boot DevTools (Explained)

### Features

* Auto restart
* Live reload
* Disable cache in dev

👉 Only active in development mode.

---

## 10. Embedded Servers (Explained)

### Common Servers

| Server   | Use              |
| -------- | ---------------- |
| Tomcat   | Default          |
| Jetty    | Lightweight      |
| Undertow | High performance |

👉 Embedded means **inside JAR**.

---

## 11. Spring Boot Actuator (Detailed)

### Purpose

* Monitor application health
* Production management

### Important Endpoints

* `/actuator/health`
* `/actuator/metrics`
* `/actuator/env`

👉 Used by DevOps teams.

---

## 12. Auto-Configuration Internals

Spring Boot uses:

* `spring.factories`
* Conditional annotations

### Example

```java
@ConditionalOnClass(DataSource.class)
```

👉 Loads config only when needed.

---

## 13. `spring-boot-starter-parent` (Explained)

### Role

* Dependency version management
* Plugin configuration
* Java version defaults

👉 Acts as **BOM (Bill of Materials)**.

---

## 14. Property Definition & Storage

### Sources (Priority order)

1. Command line args
2. Environment variables
3. `application.properties`
4. Default values

---

## 15. `@RestController` (Explained)

### Internals

```java
@RestController = @Controller + @ResponseBody
```

* Automatically converts response to JSON
* Uses Jackson

---

## 16. Creating REST API (Explained)

### Key Annotations

* `@GetMapping`
* `@PostMapping`
* `@RequestBody`
* `@PathVariable`

Example:

```java
@GetMapping("/{id}")
public User getUser(@PathVariable int id) {}
```

---

## 17. Stereotype Annotations (DETAILED)

| Annotation  | Layer    | Extra Behavior        |
| ----------- | -------- | --------------------- |
| @Component  | Generic  | Base bean             |
| @Service    | Business | Semantic meaning      |
| @Repository | DAO      | Exception translation |
| @Controller | MVC      | Web layer             |

---

## 18. Dependency Management in Spring Boot

* Starters manage dependencies
* Parent POM manages versions
* No need to specify versions manually

---

## 19. `@Value` Annotation (Explained)

### Purpose

Inject external values.

```java
@Value("${server.port}")
private int port;
```

👉 Supports default values.

---

## 20. Exception Handling (DETAILED)

### Global Handling

```java
@ControllerAdvice
```

### Method Level

```java
@ExceptionHandler(Exception.class)
```

👉 Clean separation of error logic.

---

## 21. `@Configuration` vs `@Component`

* `@Configuration` → full Spring config
* `@Component` → simple bean

👉 `@Configuration` supports proxying.

---

## 22. Externalized Configuration (Explained)

### Supported Sources

* Properties
* YAML
* ENV variables
* Profiles

Example:

```properties
spring.profiles.active=dev
```

---

## 23. Packaging Options

### JAR

* Standalone
* Embedded server

### WAR

* External server deployment

---

## 24. Securing Spring Boot Application

### Spring Security Features

* Authentication
* Authorization
* JWT
* OAuth2

### Default Behavior

* Secures all endpoints
* Basic auth enabled

---

## 25. `@EnableAutoConfiguration` (Deep Dive)

* Uses conditional annotations
* Loads configs only if required
* Improves startup performance

---

## 26. RESTful Web Services (Explained)

### REST Principles

* Stateless
* Resource-based
* HTTP methods

Spring Boot provides:

* Automatic JSON mapping
* Validation
* Error handling

---

## 27. `@Entity` Annotation (Explained)

### Purpose

* Maps class to DB table
* Used by JPA/Hibernate

```java
@Entity
@Table(name="users")
```

---

## 28. Testing Annotations (Detailed)

| Annotation      | Use             |
| --------------- | --------------- |
| @SpringBootTest | Full app test   |
| @WebMvcTest     | Controller test |
| @MockBean       | Mock dependency |
| @DataJpaTest    | Repository test |

---

## 29. `application.yml` (Explained)

### Advantages

* Readable
* Hierarchical
* Supports profiles

```yaml
spring:
  profiles: dev
```

---

## 30. Production Monitoring (DETAILED)

### Tools

* Actuator
* Micrometer
* Prometheus
* Grafana

👉 Used for **metrics, alerts, health checks**.

---
