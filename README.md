# Java Interview & Evaluation Questions & Answers

A comprehensive collection of Core Java, Multithreading, Collections, Generics, I/O, Java 8, and JDBC questions with code snippets, multiple-choice options, correct answers, and detailed explanations.

---

## Table of Contents
1. [JDBC & Database Connectivity](#1-jdbc--database-connectivity)
2. [Object-Oriented Programming (OOP) & Inheritance](#2-object-oriented-programming-oop--inheritance)
3. [Multithreading & Concurrency](#3-multithreading--concurrency)
4. [Collections, Generics & Objects](#4-collections-generics--objects)
5. [Java I/O & Serialization](#5-java-io--serialization)
6. [Java 8 Features](#6-java-8-features)
7. [Language Fundamentals & Syntax](#7-language-fundamentals--syntax)

---

## 1. JDBC & Database Connectivity

### Q1. Driver Loading Case-Sensitivity
**Code:**
```java
public class JdbcTest {
    public static void main(String[] args) throws SQLException, ClassNotFoundException {
        Connection con = null;
        Class.forName("Oracle.jdbc.driver.OracleDriver");
        String url = "jdbc:oracle:thin:@localhost:1521:xe";
        con = DriverManager.getConnection(url, "system", "password");
        System.out.println("Success");
    }
}
```
**Options:**
- Null
- ClassNotFoundException
- Success
- SQLException

**Answer:** **`ClassNotFoundException`**  
**Explanation:** Java package names are case-sensitive. The standard package is `oracle.jdbc.driver.OracleDriver` (lowercase `oracle`). Using `"Oracle..."` causes `Class.forName()` to fail immediately and throw `ClassNotFoundException`.

---

### Q2. Purpose of `Class.forName()` in JDBC
**Question:** What is the purpose of the `Class.forName` method when loading a JDBC Driver in Java?  
**Options:**
- a. It instantiates an object of the Driver class.
- b. It initializes the JDBC Driver and registers it with the DriverManager.
- c. It connects to the database server.
- d. It retrieves the metadata of the database.

**Answer:** **`b. It initializes the JDBC Driver and registers it with the DriverManager.`**  
**Explanation:** When `Class.forName()` loads the driver class, the static initialization block runs, creating an instance of the driver and invoking `DriverManager.registerDriver()`.

---

### Q3. Advantage of Batch Processing in JDBC
**Question:** What is the primary advantage of using batch processing in JDBC?  
**Options:**
- a. It reduces the number of database connections.
- b. It improves performance by reducing the number of round-trips to the database.
- c. It simplifies the SQL syntax for complex queries.
- d. It allows parallel execution of unrelated queries.

**Answer:** **`b. It improves performance by reducing the number of round-trips to the database.`**  
**Explanation:** Batch processing (`addBatch()` / `executeBatch()`) groups multiple operations into a single network transmission, cutting down network latency.

---

### Q4. Stored Procedure IN vs OUT Parameters
**Question:** What is the difference between IN and OUT parameters in stored procedures?  
**Options:**
- a. IN parameters are used for input, while OUT parameters are used for output.
- b. OUT parameters are used for input, while IN parameters are used for output.
- c. Both IN and OUT parameters are used for input.
- d. Both IN and OUT parameters are used for output.

**Answer:** **`a. IN parameters are used for input, while OUT parameters are used for output.`**  
**Explanation:** `IN` parameters supply data into the stored procedure; `OUT` parameters return results back to the caller.

---

### Q5. "No Suitable Driver" Error
**Question:** When does the message "No Suitable Driver" occur?  
**Options:**
- a. When the driver is not registered by Class.forName() method
- b. When the user name, password and the database does not match
- c. When the JDBC database URL passed is not constructed properly
- d. When the type 4 driver is used

**Answer:** **`a. When the driver is not registered by Class.forName() method`**  
**Explanation:** If the driver class has not been registered with `DriverManager`, calling `DriverManager.getConnection()` cannot find a driver accepting the URL and throws `SQLException: No suitable driver found`.

---

### Q6. Executing a SELECT Query
**Question:** Which method is used to execute a select SQL query in JDBC?  
**Options:**
- A. executeQuery()
- B. executeUpdate()
- C. execute()
- D. executeStatement()

**Answer:** **`A. executeQuery()`**  
**Explanation:** `executeQuery()` returns a `ResultSet` containing the retrieved data. `executeUpdate()` is used for DML (`INSERT`, `UPDATE`, `DELETE`) or DDL statements.

---

### Q7. `TYPE_SCROLL_SENSITIVE` Constant
**Question:** In JDBC, what does the `TYPE_SCROLL_SENSITIVE` constant represent in the `ResultSet` type?  
**Options:**
- a. It indicates that the result set is scrollable and sensitive to changes made by others.
- b. It represents a forward-only result set.
- c. It represents a read-only result set.
- d. It indicates that the result set is insensitive to changes made by others.

**Answer:** **`a. It indicates that the result set is scrollable and sensitive to changes made by others.`**  
**Explanation:** It allows moving the cursor in both directions (forward/backward) and reflects updates made to the underlying database while open.

---

### Q8. Use Cases for Batch Processing
**Question:** Which of the following scenarios is suitable for using batch processing in JDBC?  
**Options:**
- a. Executing independent queries with no dependencies
- b. Running complex transactions requiring precise order of execution
- c. Handling transactions with rollback and commit operations
- d. Performing ad-hoc queries with dynamic parameters

**Answer:** **`a. Executing independent queries with no dependencies`**  
**Explanation:** Batch processing executes sets of statements without individual dependencies on previous statement return values.

---

### Q9. Managing Transactions Interface
**Question:** Which interface in JDBC is used for managing transactions?  
**Options:**
- a. Statement
- b. ResultSet
- c. Connection
- d. TransactionManager

**Answer:** **`c. Connection`**  
**Explanation:** Transaction methods (`setAutoCommit()`, `commit()`, `rollback()`, `setSavepoint()`) belong to `java.sql.Connection`.

---

### Q10. Definition of Batch Processing
**Question:** What is batch processing in JDBC?  
**Options:**
- a. Processing multiple database queries in parallel
- b. Executing a group of related SQL statements in a single round-trip to the database
- c. Running multiple transactions concurrently
- d. Performing asynchronous database operations

**Answer:** **`b. Executing a group of related SQL statements in a single round-trip to the database`**

---

### Q11. Purpose of `rollbackToSavepoint`
**Question:** What is the purpose of the `rollbackToSavepoint` method in JDBC?  
**Options:**
- a. To roll back the entire transaction
- b. To roll back to the beginning of the transaction
- c. To roll back to a specific savepoint within a transaction
- d. To undo the last database operation

**Answer:** **`c. To roll back to a specific savepoint within a transaction`**

---

### Q12. Advancing ResultSet Cursor
**Question:** Which method in the `ResultSet` interface is used to move the cursor to the next row of the result set?  
**Options:**
- a. moveNext()
- b. next()
- c. forward()
- d. fetchRow()

**Answer:** **`b. next()`**

---

### Q13. Meaning of ODBC
**Question:** What does the acronym "ODBC" stand for in the context of JDBC and database connectivity?  
**Options:**
- a. Oracle Database Connectivity
- b. Object-Database Connectivity
- c. Open Database Connectivity
- d. On-Demand Database Connectivity

**Answer:** **`c. Open Database Connectivity`**

---

### Q14. `setBinaryStream` vs `setBlob`
**Question:** What is the primary advantage of using a `PreparedStatement` with `setBinaryStream` over `setBlob` for handling files in JDBC?  
**Options:**
- a. setBinaryStream is deprecated; setBlob is the preferred method.
- b. setBinaryStream is more efficient for large files as it allows streaming.
- c. setBinaryStream can only handle small files; setBlob is recommended for larger files.
- d. There is no significant difference between them for handling files.

**Answer:** **`b. setBinaryStream is more efficient for large files as it allows streaming.`**  
**Explanation:** `setBinaryStream` streams binary data directly from an `InputStream` into the database without needing to hold the entire file contents in memory.

---

### Q15. PreparedStatement Efficiency
**Question:** Which of the following is efficient than a statement due to the pre-compilation of SQL?  
**Options:**
- A - Statement
- B - PreparedStatement
- C - CallableStatement
- D - None of the above.

**Answer:** **`B - PreparedStatement`**  
**Explanation:** `PreparedStatement` is precompiled by the database engine, allowing parameter substitution and query plan caching for faster subsequent runs.

---

### Q16. Retrieving Result Sets from Stored Procedures
**Question:** How do you retrieve the result set returned by a stored procedure in JDBC?  
**Options:**
- a. Use the getResultSet method of Statement
- b. Use the getResultSet method of CallableStatement
- c. Use the executeQuery method of CallableStatement
- d. Stored procedures cannot return result sets in JDBC.

**Answer:** **`b. Use the getResultSet method of CallableStatement`**

---

### Q17. Transaction Exception without Explicit Rollback
**Question:** What happens if an exception occurs during a transaction and there is no explicit rollback?  
**Options:**
- a. The transaction is automatically rolled back
- b. The transaction is committed
- c. The transaction is suspended
- d. It depends on the database implementation

**Answer:** **`d. It depends on the database implementation`**  
**Explanation:** The JDBC standard does not enforce whether uncommitted transactions roll back or commit on close; it is vendor/driver-dependent.

---

### Q18. Method for DML Statements
**Question:** Which of the following method is used to perform DML statements in JDBC?  
**Options:**
- A. executeResult()
- B. executeQuery()
- C. executeUpdate()
- D. execute()

**Answer:** **`C. executeUpdate()`**

---

## 2. Object-Oriented Programming (OOP) & Inheritance

### Q19. Subclass Access to Private Superclass Fields
**Code:**
```java
class Money {
    private String country = "Canada";
    public String getC() { return country; }
}

class Yen extends Money {
    public String getC() { return super.country; }
}

public class Euro extends Money {
    public String getC(int x) { return super.getC(); }
    public static void main(String[] args) {
        System.out.print(new Yen().getC() + " " + new Euro().getC());
    }
}
```
**Options:**
- Canada
- null Canada
- Canada null
- Canada Canada
- Compilation fails due to an error on line 26.
- Compilation fails due to an error on line 29.

**Answer:** **`Compilation fails due to an error on line 26.`**  
**Explanation:** `country` is marked `private` in `Money`. Subclasses cannot access private members of a parent class directly using `super.country`.

---

### Q20. Method Overriding vs Field Hiding
**Code:**
```java
class Foo {
    public int a = 3;
    public void addFive() { a += 5; System.out.print("f "); }
}

class Bar extends Foo {
    public int a = 8;
    public void addFive() { this.a += 5; System.out.print("b "); }
}

// Invoked with:
Foo f = new Bar();
f.addFive();
System.out.println(f.a);
```
**Options:**
- b 3
- b 8
- b 13
- f 3
- f 8
- f 13
- Compilation fails.
- An exception is thrown at runtime.

**Answer:** **`b 3`**  
**Explanation:**
1. **Methods are polymorphic:** `f.addFive()` invokes `Bar.addFive()` (runtime type), printing `b ` and updating `Bar.a`.
2. **Variables are NOT polymorphic:** `f.a` resolves at compile-time to `Foo.a` (reference type), which remains `3`.

---

### Q21. Explicit Subclass Constructor Invocations
**Code:**
```java
class Super {
    private int a;
    protected Super(int a) { this.a = a; }
}

class Sub extends Super {
    public Sub(int a) { super(a); }
    public Sub() { this.a = 5; } // line 13
}
```
**Question:** Which two, independently, will allow Sub to compile? (Choose two.)  
**Options:**
- Change line 2 to: `public int a;`
- Change line 2 to: `protected int a;`
- Change line 13 to: `public Sub() { this(5); }`
- Change line 13 to: `public Sub() { super(5); }`
- Change line 13 to: `public Sub() { super(a); }`

**Answers:**
- ☑️ **`Change line 13 to: public Sub() { this(5); }`**
- ☑️ **`Change line 13 to: public Sub() { super(5); }`**  
**Explanation:** `Super` has no default zero-argument constructor `Super()`. `Sub()` implicitly calls `super()`, which causes a compile error. Explicitly chaining via `this(5)` or `super(5)` satisfies constructor invocation requirements and avoids accessing the private field `a`.

---

### Q22. Subclassing an Abstract Class
**Code:**
```java
public abstract class Shape {
    private int x;
    private int y;
    public abstract void draw();
    public void setAnchor(int x, int y) {
        this.x = x;
        this.y = y;
    }
}
```
**Question:** Which two classes use the Shape class correctly? (Choose two.)  
**Answers:**
- ☑️ **`public abstract class Circle extends Shape { private int radius; }`**
- ☑️ **`public class Circle extends Shape { private int radius; public void draw() {/* code here */} }`**  
**Explanation:** `Shape` is an abstract class, so subclasses must use `extends` (not `implements`). A subclass must either be declared `abstract` or provide a concrete implementation body `{}` for `draw()`.

---

### Q23. Polymorphic Method Dispatch Across Inheritance Hierarchy
**Code:**
```java
abstract class Vehicle { public int speed() { return 0; } }
class Car extends Vehicle { public int speed() { return 60; } }
class RaceCar extends Car { public int speed() { return 150; } }

RaceCar racer = new RaceCar();
Car car = new RaceCar();
Vehicle vehicle = new RaceCar();
System.out.println(racer.speed() + ", " + car.speed() + ", " + vehicle.speed());
```
**Options:**
- 0, 0, 0
- 150, 60, 0
- Compilation fails.
- 150, 150, 150
- An exception is thrown at runtime.

**Answer:** **`150, 150, 150`**  
**Explanation:** In Java, instance methods are virtual. Since all three references refer to instances of `RaceCar` at runtime, the overridden `speed()` in `RaceCar` is executed for all three.

---

### Q24. Object-Oriented Principles in API Design
**Question:** A team of programmers is reviewing a proposed API for a new utility class. After some discussion, they realize that they can reduce the number of methods in the API without losing any functionality. If they implement the new design, which two OO principles will they be promoting?  
**Answers:**
- ☑️ **Looser coupling**
- ☑️ **Higher cohesion**  
**Explanation:** Reducing unnecessary methods sharpens the class's focus on a single responsibility (high cohesion) and minimizes caller dependencies on class internals (loose coupling).

---

### Q25. HAS-A Relationship (Composition)
**Question:** Which Man class properly represents the relationship "Man has a best friend who is a Dog"?  
**Answer:** **`class Man { private Dog bestFriend; }`**  
**Explanation:** Composition (HAS-A) is modeled using an instance variable inside the class.

---

### Q26. Anonymous Inner Class Implementing Interface
**Code:**
```java
interface TestA { String toString(); }
public class Test {
    public static void main(String[] args) {
        System.out.println(new TestA() {
            public String toString() { return "test"; }
        });
    }
}
```
**Answer:** **`Test`** (or **`test`**)  
**Explanation:** The anonymous inner class implements `TestA` and overrides `toString()`. `System.out.println` invokes `toString()`, outputting the returned string.

---

## 3. Multithreading & Concurrency

### Q27. Thread Non-Determinism and Exceptions
**Code:**
```java
public class Threads2 implements Runnable {
    public void run() {
        System.out.println("run.");
        throw new RuntimeException("Problem");
    }
    public static void main(String[] args) {
        Thread t = new Thread(new Threads2());
        t.start();
        System.out.println("End of method.");
    }
}
```
**Question:** Which two can be results? (Choose two.)  
**Answers:**
- ☑️
  ```text
  End of method.
  run.
  java.lang.RuntimeException: Problem
  ```
- ☑️
  ```text
  run.
  java.lang.RuntimeException: Problem
  End of method.
  ```
**Explanation:** Thread execution order is non-deterministic. The main thread's `"End of method."` can execute before or after the child thread executes `"run."` and throws the exception.

---

### Q28. Synchronized Instance Method on a Shared Static Object
**Code:**
```java
class PingPong2 {
    synchronized void hit(long n) {
        for(int i = 1; i < 3; i++)
            System.out.print(n + "-" + i + " ");
    }
}
public class Tester implements Runnable {
    static PingPong2 pp2 = new PingPong2();
    public static void main(String[] args) {
        new Thread(new Tester()).start();
        new Thread(new Tester()).start();
    }
    public void run() { pp2.hit(Thread.currentThread().getId()); }
}
```
**Answer:** **`The output could be 6-1 6-2 5-1 5-2`**  
**Explanation:** `hit()` is synchronized on the single static instance `pp2`. One thread must complete both iterations of its loop before releasing the lock to the other thread, preventing interleaving.

---

### Q29. Deadlock Principles
**Question:** Which two statements are true? (Choose two)  
**Answers:**
- ☑️ **`It is possible for more than two threads to deadlock at once.`**
- ☑️ **`If a piece of code is capable of deadlocking, you cannot eliminate the possibility of deadlocking by inserting invocations of Thread.yield().`**  
**Explanation:** Deadlock dependency cycles can span multiple threads ($> 2$). `Thread.yield()` does not release locks or change locking sequence, so it cannot prevent deadlocks.

---

### Q30. Starting an Already Started Thread
**Code:**
```java
Thread t = new Thread(r);
t.start();
t.start();
```
**Answer:** **`An exception is thrown at runtime.`**  
**Explanation:** Invoking `start()` more than once on the same `Thread` object throws `java.lang.IllegalThreadStateException`.

---

### Q31. Calling `wait()` Without Monitor Ownership
**Code:**
```java
void waitForSignal() {
    Object obj = new Object();
    synchronized (Thread.currentThread()) {
        obj.wait();
        obj.notify();
    }
}
```
**Answer:** **`This code can throw an IllegalMonitorStateException.`**  
**Explanation:** The synchronization lock is acquired on `Thread.currentThread()`, but `wait()` is invoked on `obj`. Calling `obj.wait()` without holding `obj`'s monitor causes an `IllegalMonitorStateException`.

---

## 4. Collections, Generics & Objects

### Q32. Characteristics of `hashCode()`
**Question:** Which two statements are true about the `hashCode` method? (Choose two.)  
**Answers:**
- ☑️ **`The hashCode method for a given class can be used to test for object inequality, but NOT object equality, for that class.`**
- ☑️ **`The hashCode method is used by the java.util.HashSet collection class to group the elements within that set into hash buckets for swift retrieval.`**  
**Explanation:** If two objects have different hash codes, they are guaranteed unequal. However, identical hash codes do not guarantee equality (due to hash collisions). `HashSet` uses hash codes to index elements into buckets for $O(1)$ expected lookup.

---

### Q33. `Comparable<T>` Implementation
**Code:**
```java
public class Score implements Comparable<Score> {
    private int wins, losses;
    // ...
    // insert code here
}
```
**Question:** Which method will complete this class?  
**Answer:** **`public int compareTo(Score other){/*more code here*/}`**  
**Explanation:** Because the class implements generic `Comparable<Score>`, the `compareTo` method must accept a `Score` parameter rather than a raw `Object`.

---

### Q34. Overriding vs Overloading `equals()`
**Code:**
```java
public class Person {
    private String name;
    public Person(String name) { this.name = name; }
    public boolean equals(Person p) {
        return p.name.equals(this.name);
    }
}
```
**Answer:** **`The equals method does NOT properly override the Object.equals method.`**  
**Explanation:** `Object.equals` has the signature `boolean equals(Object obj)`. Defining `equals(Person p)` overloads the method rather than overriding it.

---

### Q35. Heterogeneous Sorting with `Arrays.sort()`
**Code:**
```java
Object[] myObjects = {
    new Integer(12),
    new String("foo"),
    new Integer(5),
    new Boolean(true)
};
Arrays.sort(myObjects);
```
**Answer:** **`A ClassCastException occurs in line 29.`**  
**Explanation:** `Arrays.sort(Object[])` requires all elements to be mutually comparable by casting them to `Comparable`. Comparing an `Integer` to a `String` throws a `ClassCastException` at runtime.

---

### Q36. Refactoring Pre-Generics Code
**Code:**
```java
public static int sum(List list) {
    int sum = 0;
    for ( Iterator iter = list.iterator(); iter.hasNext(); ) {
        int i = ((Integer)iter.next()).intValue();
        sum += i;
    }
    return sum;
}
```
**Question:** What three changes allow the class to be used with generics and avoid an unchecked warning? (Choose three.)  
**Answers:**
- ☑️ **Remove line 14.**
- ☑️ **Replace line 13 with `"for (int i : intList) {"`.**
- ☑️ **Replace the method declaration with `"sum(List<Integer> intList)"`.**  
**Explanation:** Converts the method to `sum(List<Integer> intList)` and replaces manual iterator traversal/casting with an enhanced `for (int i : intList)` loop utilizing auto-unboxing.

---

### Q37. Garbage Collection and `finalize()`
**Question:** Which statement is true?  
**Answer:** **`The finalize() method for a given object is called no more than once by the garbage collector.`**  
**Explanation:** The JVM guarantees that `finalize()` will never be called more than once on any given object, even if the object resurrects itself during finalization.

---

## 5. Java I/O & Serialization

### Q38. Serialization and Inheritance
**Code:**
```java
class Food implements Serializable { int good = 3; }
class Fruit extends Food { int juice = 5; }
public class Banana extends Fruit {
    int yellow = 4;
    public static void main(String [] args) {
        Banana b = new Banana(); 
        Banana b2 = new Banana();
        b.serializeBanana(b);
        b2 = b.deserializeBanana();
        System.out.println("restore " + b2.yellow + b2.juice + b2.good);
    }
}
```
**Answer:** **`restore 453`**  
**Explanation:** `Food` implements `Serializable`. Since `Fruit` and `Banana` extend `Food`, they inherit serializability. All fields (`yellow=4`, `juice=5`, `good=3`) are preserved and restored.

---

### Q39. Renaming File / Directory
**Code:**
```java
File dir = new File("dir");
dir.mkdir();
File f1 = new File(dir, "f1.txt");
try {
    f1.createNewFile();
} catch (IOException e) { ; }
File newDir = new File("newDir");
dir.renameTo(newDir);
```
**Answer:** **`The file system has a directory named newDir, containing a file f1.txt.`**  
**Explanation:** `dir.renameTo(newDir)` renames the folder `dir` to `newDir`. The file created inside it moves with the directory.

---

### Q40. Unique Capability of `FileWriter`
**Question:** Which capability exists only in `java.io.FileWriter`?  
**Answer:** **`Writing a line separator to an open stream.`**

---

## 6. Java 8 Features

### Q41. Return Type of Lambda Expressions
**Question:** What is the return type of lambda expression?  
**Options:**
- String
- object
- void
- Function

**Answer:** **`Function`**  
**Explanation:** In standard multiple-choice testing terminology, lambdas represent functional interface implementations and are categorized as functions.

---

### Q42. Features NOT Introduced in Java 8
**Question:** Which of the following is not introduced with Java 8?  
**Options:**
- Stream API
- Serialization
- Spliterator
- Lambda Expression

**Answer:** **`Serialization`**  
**Explanation:** Serialization was introduced in JDK 1.1. Stream API, Spliterator, and Lambda Expressions were introduced in Java 8.

---

### Q43. Stream Types in Java 8
**Question:** What are the two types of Streams offered by java 8?  
**Options:**
- sequential and parallel
- sequential and random
- parallel and random
- random and synchronized

**Answer:** **`sequential and parallel`**

---

### Q44. Iterating Collections in Java 8
**Question:** Which is the new method introduced in java 8 to iterate over a collection?  
**Answer:** **`StringList.forEach()`**  
**Explanation:** `forEach()` was added as a default method on `java.lang.Iterable` in Java 8.

---

### Q45. `Files.lines()`
**Question:** What does `Files.lines(Path path)` do?  
**Answer:** **`It reads all the lines from a file as a Stream`**  
**Explanation:** `Files.lines(Path)` returns a lazy `Stream<String>`.

---

## 7. Language Fundamentals & Syntax

### Q46. Unboxing `null` Wrapper Object
**Code:**
```java
public class Boxer1 {
    Integer i;
    int x;
    public Boxer1(int y) {
        x = i + y;
        System.out.println(x);
    }
    public static void main(String[] args) {
        new Boxer1(new Integer(4));
    }
}
```
**Answer:** **`A NullPointerException occurs at runtime.`**  
**Explanation:** Instance variable `Integer i` defaults to `null`. In `x = i + y;`, the JVM attempts to auto-unbox `i` by calling `i.intValue()`, causing a `NullPointerException`.

---

### Q47. Nested Enums Qualification
**Code:**
```java
class Nav {
    public enum Direction { NORTH, SOUTH, EAST, WEST }
}
public class Sprite {
    // insert code here
}
```
**Answer:** **`Nav.Direction d = Nav.Direction.NORTH;`**  
**Explanation:** Because `Direction` is declared inside `Nav` without static imports, both the enum type and constant must be qualified via `Nav`.

---

### Q48. Varargs Position in Method Signatures
**Code:**
```java
public class Barn {
    public void go(String... y, int x) {
        System.out.print(y[y.length - 1] + " ");
    }
}
```
**Answer:** **`Compilation fails.`**  
**Explanation:** In Java, a varargs parameter (`...`) must always be the last parameter in the method signature.

---

### Q49. Command Line Arguments Indexing
**Code:**
```java
public class Yippee {
    public static void main(String [] args) {
        for(int x = 1; x < args.length; x++) {
            System.out.print(args[x] + " ");
        }
    }
}
// Invocation: java Yippee 1 2 3 4
```
**Answer:** **`2 3 4`**  
**Explanation:** Array indexing begins at 0 (`args[0] = "1"`). The loop starts at `x = 1`, printing `args[1]`, `args[2]`, and `args[3]`.

---

### Q50. Local Variable Scope in Try-Catch-Finally
**Code:**
```java
public static void parse(String str) {
    try {
        float f = Float.parseFloat(str);
    } catch (NumberFormatException nfe) {
        f = 0;
    } finally {
        System.out.println(f);
    }
}
```
**Answer:** **`Compilation fails.`**  
**Explanation:** Variable `f` is declared inside the `try` block, so it is out of scope in the `catch` and `finally` blocks.

---

### Q51. Running Java Classes with Classpath
**Code:**
```java
package com.company.application;
public class MainClass {
    public static void main(String[] args) {}
}
// Located in /apps/com/company/application, CLASSPATH is "."
```
**Question:** Which two java commands entered at the command line will run MainClass? (Choose two.)  
**Answers:**
- ☑️ **`java com.company.application.MainClass if run from the /apps directory`**
- ☑️ **`java -classpath /apps com.company.application.MainClass if run from any directory`**  
**Explanation:** Java requires the fully qualified class name for execution. The root of the package directory tree is `/apps`.

---

### Q52. Javac `-d` Flag
**Command:** `javac -d classes source/Utils.java`  
**Answer:** **`If the compile is successful, Utils.class is added to the classes directory.`**  
**Explanation:** The `-d` option specifies the destination directory for compiled `.class` files.

---

### Q53. Enums in Class Body
**Code:**
```java
public class Rainbow {
    public enum MyColor {
        RED(0xff0000), GREEN(0x00ff00), BLUE(0x0000ff);
        private final int rgb;
        MyColor(int rgb) { this.rgb = rgb; }
        public int getRGB() { return rgb; }
    };
    public static void main(String[] args) {
        // insert code here
    }
}
```
**Answer:** **`MyColor treeColor = MyColor.GREEN;`**  
**Explanation:** Inside `Rainbow`, `MyColor` is directly in scope. Enum constants must be qualified with the enum type (`MyColor.GREEN`).

---

### Q54. String vs StringBuilder Mutation
**Code:**
```java
StringBuilder sb1 = new StringBuilder("123");
String s1 = "123";
// insert code here
System.out.println(sb1 + " " + s1);
// Desired output: "123abc 123abc"
```
**Answer:** **`sb1.append("abc"); s1 = s1.concat("abc");`**  
**Explanation:** `StringBuilder` is mutable (`append()` updates in place), while `String` is immutable (the return value of `concat()` must be reassigned to `s1`).

---

### Q55. DateFormat Parsing
**Code:**
```java
DateFormat df; Date d = new Date(0L); String ds = "December 15, 2004";
```
**Answer:**
```java
try {
    d = df.parse(ds);
} catch (ParseException e) { };
```
**Explanation:** `DateFormat.parse()` parses date strings and throws a checked `ParseException`, requiring a `try-catch` block or throws declaration.

---

### Q56. NumberFormat Formatting
**Code:**
```java
double input = 314159.26;
NumberFormat nf = NumberFormat.getInstance(Locale.ITALIAN);
String b;
```
**Answer:** **`b = nf.format( input );`**  
**Explanation:** The `format()` method formats a numerical primitive/object into a localized string.

---

### Q57. String Concatenation Operator
**Code:**
```java
String str = "420";
str += 42;
System.out.print(str);
```
**Answer:** **`42042`**  
**Explanation:** The `+=` operator with a `String` operand converts `42` to string `"42"` and appends it to `"420"`.

---

### Q58. Finally Without Try Block
**Code:**
```java
Float pi = new Float(3.14f);
if (pi > 3) {
    System.out.print("pi is bigger than 3. ");
} else {
    System.out.print("pi is not bigger than 3. ");
} finally {
    System.out.println("Have a nice day.");
}
```
**Answer:** **`Compilation fails.`**  
**Explanation:** In Java, `finally` can only be attached to a `try` block, never to an `if-else` statement.

---

### Q59. Static Import Syntax
**Code:**
```java
// utils/Repetition.java
package utils;
public class Repetition {
    public static String twice(String s) { return s + s; }
}

// Demo.java
// insert code here
public class Demo {
    public static void main(String[] args) {
        System.out.println(twice("pizza"));
    }
}
```
**Answer:** **`import static utils.Repetition.twice;`**  
**Explanation:** The correct keyword order is `import static`, and method names are referenced without parentheses.

---

### Q60. Legal Main Method Signatures
**Question:** How many of the following five fragments compile when inserted into a class?
1. `public static void main(String...a) {`
2. `public static void main(String.* a) {`
3. `public static void main(String... a) {`
4. `public static void main(String[]... a) {`
5. `public static void main(String...[] a) {`

**Answer:** **`3`**  
**Explanation:** Fragments 1, 3, and 4 are valid Java varargs syntax. Fragments 2 (`.*`) and 5 (`...[]`) are syntax errors.
