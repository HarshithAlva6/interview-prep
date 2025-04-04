# Java Learning Roadmap

## 1. Learn the Basics
- **Syntax:** Writing valid Java code following proper syntax.
- **Lifecycle of a program:** Java code written in .java, compiled by java compiler(javac) into bytecode and stored in .class file. This is executed by JVM when program runs.
How? Load .class files/binary data into memory, link for verification and prep, and initialise class elements. JVM verifies security compilance and Just-In-Time compilation translates bytecode into native machine code. Executes program and handles system resources. JVM meanwhile handles garbage collection and release resources. Hence "write once, run anywhere" since bytecode can execute on any device with compatible JYM.
- **Data Types:** `int`, `byte`, `short`, `long`, `float`, `double`, `boolean`, `char`.
- **Variables and Scopes:** Instance variables, static variables, local variables.
- **Type Casting:** Implicit (automatic small to large) and explicit (manual large to small) casting.
- **Strings and Methods:** Sequence of characters, and actions to perfrom on them.
- **Math Operations:** Perfrom calculations on numbers.
- **Conditionals:** `if`, `else`, `switch`, ternary (`?:`).
- **Loops:** `for`, `while`, `do-while`.
- **Arrays:** Container objects to store multiple elements.
- **Strings and Methods:** Immutable sequences of characters.
- **Math Operations:** Basic arithmetic operations and the Math class.

## 2. Object-Oriented Programming (OOP)
- **Classes and Objects:** Blueprints for creating objects, i.e., instances of those classes.
- **Attributes and Methods:** Variables holding data and Functions that define behavior of object.
- **Access Specifiers:** `public`, `private`, `protected`, default.
- **Attributes and Methods:** Instance variables and functions.
- **Static Keyword:** Shared among all instances.
- **Final Keyword:** Non-access Modifier ensures value stays constant, or can't be inherited.
- **Nested Classes:** Outer class has inner class, and outer class access possible even if private.
- **Packages**

- **Object lifecycle:** Object creation, initialization, usage, passing , garbage collection.
- **Method Chaining:** Calling multiple methods in a single statement.
- **Enums:** Constants with a fixed set of values.
- **Records:** public record Vehicle(String brand) holds immutable data and helps store and access data by creating Data Transfer Objects(DTO)
- **Inheritance:** Extending existing classes (`extends`). Is-a relationship.
- **Polymorphism:** Overloading (compile-time) and overriding (runtime).
- **Abstraction:** Hiding implementation (abstract classes, interfaces).
- **Encapsulation:** Data hiding using access modifiers.
- **Initializer Block:** Code in {} executed when instance of class created. Performs tasks before constructor is called if its Instance initializer, or run when class is loaded ONCE if static initializer.
- **Static vs. Dynamic Binding:** Determining method execution at compile-time or runtime.
- **Lambda Expressions:** `(param) -> expression` syntax. Short blocks of code to treat functionality as method argument, methods without a name.
- **Object Lifecycle:** Object creation to garbage collection.
- **Pass by Value / Pass by Reference:**Copy of variables value is passed to function. And direct reference to variable is passed.
- **Modules:** Organise code into independent units. Higher level of abstraction than packages.
- **Optionals:** Container object which may or may not contain non-null value. Represent absence of value, and avoid need to return call. Avoid null values and null checks.
- **Dependency Injection:** Objects recieve dependencies from external sources rather than creating them. Calss gets objects 'injected' into them through constructors, interfaces etc. Loose coupling.
- **I/O Operations:** Deal with program interaction with outside world using java.io package.

## 3. Data Structures and Collections
- **Array vs. ArrayList:** Fixed vs. dynamic size.
- **Set, Map:** Unordered, key-value pairs. Extends Collections interface.
- **Queue, Stack, Deque:** FIFO, LIFO, and double-ended queue.
- **Iterator:** Iterating collections safely.
- **Collections Framework:** Utility methods like `sort()`, `binarySearch()`, `fill()`.
- **Generic Collections:** Type-safe collections like `List<T>`.

- **Concurrency:**  Execute tasks simultaneously, which means their execution overlaps in time. Multithreading splits program into threads.
JVM provides a main thread(OS-level), which can be split(like multiple CPU's executing app) Sharing resources and time of a CPU across threads. Context Switching by CPU is slow.
- Virtual Threads: Lightweight, helps improve scalability and concurrency of Java apps that handle concurrent operations. Managed by JVM, dont block, but simply let another thread run, avoiding context switching.
Java Memory Model: How different threads interact with memory. They see writes to shared variables, establish rules for memory synchronization and ordering.
## 4. Exception Handling
- **Checked vs. Unchecked Exceptions:** Compile-time vs. runtime.
- **Errors:** Irrecoverable (e.g., `OutOfMemoryError`).
- **Try-Catch, Finally:** Error handling blocks.
- **Throw and Throws:** Manually throwing exceptions.

## 5. Concurrency and Multithreading
- **Threads:** Multitasking with `Thread` class and `Runnable` interface.
- **Virtual Threads:** Lighter threads introduced in Java 19.
- **Java Memory Model:** Interaction of threads with memory.
- **Volatile Keyword:** Ensures visibility of variable updates across threads.
- **Synchronization and Locks:** Control thread access to shared resources.

## 6. I/O and File Operations
- **File Handling:** `FileReader`, `FileWriter`.
- **Serialization and Deserialization:** Convert objects to bytes for storage or transfer.

## 7. Advanced Java
- **Reflection:** Analyzing classes, interfaces, fields, and methods at runtime.
- **Annotations:** Metadata for classes, methods, and variables. Not a part of program, but just used by compiler to detect errors, and at runtime to modify behavior.
- **Cryptography:** Securing data using Java's crypto package.
- **Date and Time API:** Classes like `LocalDate`, `LocalTime`, `LocalDateTime`.
- **Functional Programming:** Functional interfaces, Stream API.
- **Networking:** Sockets and URL connections.
- **Regular Expressions:** Pattern matching in strings.

## 8. Database Access
- **JDBC:** Database connectivity using SQL.
- **JPA:** Object-relational mapping.
- **Hibernate:** Popular ORM framework.
- **EBean:** Lightweight ORM.
- **Spring Data JPA:** Simplified data access in Spring.

## 9. Web Frameworks
- **Spring Boot:** Recommended for microservices.
- **Play Framework:** High-productivity MVC framework.
- **Quarkus:** Optimized for Kubernetes and serverless.

## 10. Build Tools
- **Maven:** Dependency management (`pom.xml`).
- **Gradle:** Script-based, Java/Groovy-based DSL.
- **Bazel:** Fast, scalable build system.

## 11. Testing
- **Unit Testing:** JUnit, TestNG.
- **Integration Testing:** REST Assured, JMeter.
- **Behavior Testing:** Cucumber-JVM for BDD.
- **Mocking:** Mockito for simulating dependencies.

## 12. Logging Frameworks
- **Logback:** Successor to Log4j.
- **Log4j2:** Popular logging library.
- **SLF4J:** Facade for logging APIs.
- **TinyLog:** Lightweight logging.

Functional Programming -
1. Composition - C ompose individual functions (typically one or more Java Lambda Expressions) into a single function.
2. Interfaces - Has one abstract method, but multiple default or static methods.
3. High Order functions -   