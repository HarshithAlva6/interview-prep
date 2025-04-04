# Java Reference Guide

## Overview
**Java** – Developed by Sun Microsystems in 1995. It is a class-based, object-oriented programming language.

## Key Concepts
### Objects and Classes
- Objects store state in fields.
- Instance (non-static) variables have unique values for each class instance.
- Class (static) variables have only one copy in existence.
- `final` ensures a variable is constant.
- Local variables exist within methods.
- Parameters are arguments sent to methods.

### Data Types
- **Statically-typed:** Declare first, use next.
- **Primitive types:**
  - `int` (32-bit signed)
  - `byte` (8-bit signed)
  - `short` (16-bit signed)
  - `long` (64-bit signed)
  - `float` (single precision 32-bit)
  - `double` (double precision 64-bit)
  - `boolean` (true/false)
  - `char` (16-bit Unicode)
- **String:** Immutable.
- Primitives have literals (no `new` keyword).

### Arrays
- Arrays are container objects that store elements.
- Useful methods:
  - `binarySearch()`, `equals()`, `fill()`, `sort()`, `toString()`.

### Variables
- `var` lets the compiler decide the data type (only for local variables).

## Control Flow
### Conditional Statements
- `if..else`, `switch`, `?:` (ternary operator).

### Functions
- DRY (Don't Repeat Yourself).
- Define functions, then call them.
- Use **lambda expressions**: `(x) -> x + 1`.
- Functions can be passed as variables.

### Methods
- **Method header:** Access specifier, return type, method name, parameters.
- **Method Overloading:** Methods with different parameters in the same class.
- **Method Overriding:** A subclass provides a specific implementation of a superclass method (`@Override`).
- **Getter & Setter methods:** Access and modify private variables.
- **Date and Time API:** `java.time.*` for `LocalDate`, `Clock`, etc.

### Loops
- `for`, `forEach`, `while`, `do..while`.

## Exception Handling
Handles runtime errors to preserve application flow.
1. **Checked Exceptions**: Compile-time, e.g., `IOException`.
2. **Unchecked Exceptions**: Runtime, e.g., `NullPointerException`.
3. **Errors**: Irrecoverable, e.g., `OutOfMemoryError`.

## Data Structures
- **Arrays**
- **Linked Lists**
- **Stacks**
- **Hash Tables**
- **Queues**
- **Trees**
- **Heaps**
- **Graphs**

## Object-Oriented Programming (OOP)
### Core Concepts
1. **Objects** - State, behavior, instance of a class.
2. **Inheritance** - Acquires parent object fields & methods.
   - **Types:** Single, Multilevel, Hierarchical, Multiple, Hybrid.
   - **IS-A Relationship (parent-child).**
3. **Polymorphism** - Ability to take multiple forms.
   - **Method Overriding** (runtime polymorphism)
   - **Method Overloading** (compile-time polymorphism)
4. **Abstraction** - Hide implementation details.
   - `abstract` classes cannot be instantiated.
   - Interfaces define contracts to be implemented.
5. **Association** - Relationship between classes.
   - **Aggregation**: One-to-one or one-way (independent).
   - **Composition**: Part-of (dependent).

## Packages
- **Namespace** containing classes and interfaces.
- Example: `java.util.ArrayList`.
- Create using `javac -d directory filename`.

## Working with Files & APIs
- **File Handling:** `FileWriter`, `FileReader`.
- **Networking:** `HttpURLConnection`, `HttpClient`.

## Advanced Java
### Java Enterprise Edition (JEE)
- **Java Servlets** - Dynamic, interactive web pages.
- **JSP (Java Server Pages)** - Web application development.
- **Concurrency** - Execute tasks concurrently with synchronization.
- **Multithreading** - Parallel task execution.

### Database Connectivity
- **JDBC (Java Database Connectivity)** - Connects Java to relational databases.
- **JPA (Java Persistence API)** - ORM for database persistence.
- **Spring Data JPA** - Abstraction over JDBC.
- **Hibernate** - ORM framework.

### Spring Framework
- Uses JavaBeans for business logic.
- Creates applications with minimal dependency on framework code.

## Generics
- Provides compile-time type safety.
- Example:
  ```java
  private static <E> void printArray(E[] inputArray)
  ```
- Bounded Type Parameters.

## Streams API
- **Intermediate Operations:** `map()`, `filter()`, `flatMap()`, `sorted()`, etc.
- **Terminal Operations:** `forEach()`, `collect()`, `reduce()`, etc.
- **Short-circuit Operations:** `anyMatch()`, `findFirst()`, etc.

## Java Virtual Machine (JVM)
- Executes Java bytecode.
- Manages memory via **Garbage Collection**.

### Garbage Collection
- Identifies and eliminates unused memory.
- **Steps:** Mark, delete, compact.
- `System.gc()` requests GC.

### Threads
- JVM provides a **main thread**.
- Threads can be created by:
  - Extending `Thread` class.
  - Implementing `Runnable` interface.
- **States:** New → Runnable → Running → Blocked/Dead.
- **Priority Levels:** 1 to 10 (10 is highest).

## Build Tools
### Gradle
- Open-source build automation tool.
- Java/Groovy-based DSL.
- Uses **DAG (Directed Acyclic Graph)** for task execution.

### Maven
- XML-based project management (`pom.xml`).
- Handles dependencies.

### Ant
- Uses `build.xml`.

## Spring Framework
- **Dependency Injection (DI)** container.
- **Spring Boot**: Auto-configurable Spring framework for microservices.
- Supports:
  - **Reactive programming** (async, non-blocking architecture).
  - **Cloud, serverless applications**.

## Frameworks Comparison
### Play
- High-productivity web application framework.
- Uses **MVC pattern**.
- **Reactive** from the start.

### Spark
- Micro-framework for REST API development.
- Used for Kotlin & Java apps.
- Syntax: `verb(path, callback)`.

### Quarkus
- Kubernetes-native Java stack.
- Optimized for containers, serverless, and cloud.


## ORM (Object-Relational Mapping)
Object-Relational Mapping (ORM) maps Java objects to database entities, providing a high-level abstraction to prevent SQL injection and maintain data integrity.

1. **JPA (Jakarta Persistence API)** - Manages relational data using interfaces. Supports OOP principles, metadata annotations, and SQL-like query languages (e.g., `EntityManagerFactory`, `EntityManager`).
2. **Spring Data JPA** - Simplifies Data Access Layer implementation. Uses `JPARepository` interface for defining custom access methods.
3. **Hibernate** - Open-source ORM tool that maps object-oriented models to databases. Supports:
   - First-level caching (Session-specific, enabled by default).
   - Second-level caching (SessionFactory level, requires external caching provider like EhCache).
4. **Ebean** - Java-based ORM tool supporting standard JPA annotations with a simpler API. Sessionless and does not require manual transaction handling.

## Logging Frameworks
Logging frameworks trace errors, capture logs, and record failures.

1. **LogBack** - Successor of Log4j, offering better performance, flexible configuration, and improved file archiving.
2. **Log4j2** - Efficient logging library with improved performance compared to its predecessor.
3. **Slf4j (Simple Logging Façade for Java)** - Acts as an abstraction layer, enabling switching logging frameworks at deployment time.
4. **Tinylog** - Lightweight, open-source logging framework for JVM languages.

## Memory Management
Java memory management involves automatic garbage collection (GC) to free unused objects. Memory is divided into:
- **Heap** - Stores objects managed by GC.
- **Stack** - Stores local variables and method calls for each thread.
- **Method Area** - Stores class metadata and static variables shared across threads.
- **PC Register** - Tracks execution location in each thread.
- **Native Stack** - Handles native code execution.

## Collection Framework
Provides an architecture for storing and manipulating object groups. Includes:
- **Interfaces**: `Set`, `List`, `Queue`, `Deque`
- **Classes**: `ArrayList`, `LinkedList`, `PriorityQueue`, `HashSet`

## Serialization
Serialization converts objects into byte streams for storage or network transmission. Platform-independent, using `writeObject()` (serialization) and `readObject()` (deserialization) with `ObjectOutputStream`.
- **Marshaling** - Transmitting object data over networks in distributed systems.

## Networking Sockets
Sockets enable two-way communication between networked programs. Each socket is bound to a port for TCP layer identification.

## JDBC (Java Database Connectivity)
JDBC is an API for interacting with databases. Lacks ORM, requiring manual handling of mapping, lazy loading, and transaction management.

1. **JDBi3** - Open-source Java library using lambda expressions for a higher-level interface.
2. **JDBC Template** - Simplifies JDBC operations by internally handling queries, iterating results, and translating JDBC exceptions.

## H2 Database
An embedded database for fast prototyping. Configuration settings are stored in the `application.properties` file.

## Testing in Java
Testing ensures code reliability by preventing regressions.

### Unit Testing
1. **JUnit** - Popular unit testing framework (e.g., `assertEquals` from `org.junit.jupiter.api.Assertions`).
2. **TestNG** - Inspired by JUnit and NUnit, introducing more functionalities (e.g., `@Test`, `@BeforeClass`).

### Integration Testing
1. **Rest Assured** - Validates RESTful web services in Java.
2. **JMeter** - Load testing tool analyzing performance across web services, middleware, TCP, and Java objects.

### Behavior Testing
1. **Cucumber-JVM** - Supports Behavior-Driven Development (BDD) using Given-When-Then syntax in Gherkin.

### Mocking
Mocks remove external dependencies in unit tests, creating a controlled testing environment.
1. **Mockito** - A powerful framework for mocking dependencies in Java.

