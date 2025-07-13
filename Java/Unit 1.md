## 🧭 1. Introduction to Java

### Why Java?

* **Write once, run anywhere**: Imagine you craft a toy marble in India, but it still works perfectly in Japan or Brazil. Java is that toy — once you write code, it runs on almost any computer without changes.
* **Object-Oriented**: Picture organizing your sock drawer by color or type — OOP (Object-Oriented Programming) helps organize code similarly, making it easier to find and manage things.
* **Robust & Secure**: Java checks your homework (code) carefully, preventing many common mistakes and not letting bad code mess things up — like a strict teacher.
* **Rich libraries**: It’s like having a huge toolbox — pre-made tools for doing almost anything: web apps, games, database work, and more.

---

## 📜 2. History of Java

### A Journey with Milestones

Imagine the story of a tree growing over time:

1. **1991 – Oak is planted**: In early 1990s, Sun Microsystems started a project called Oak to control TV set-top boxes.
2. **1995 – Oak becomes Java**: Oak was renamed Java, and the first public version was released. It was like planting a sapling that quickly spread its seeds everywhere.
3. **2000s – The tree grows**: Java got used for websites, servers, mobile apps (Android), and enterprise software — it grew big and wide.
4. **2010 – Oracle buys Sun**: Think of this as transplanting our tree to a new garden owner, Oracle, which continued nurturing it and releasing new versions regularly.
5. **Present**: Java is now ubiquitous — from backend servers in banks to Android apps on your phone and big data solutions.

---

## 🧰 3. JVM, JRE, JDK

Let’s break these down using our **baking a cake** metaphor:

### Java Code = Your cake recipe

You write instructions in Java, just like writing a recipe.

### JDK (Java Development Kit) = Full kitchen

Includes oven, tools, ingredients, and recipe paper — everything you need to *create* and *bake* a cake.

### JRE (Java Runtime Environment) = Oven + basic tools

Enough to *run* a cake (bytecode) that’s already baked. Doesn’t include tools to edit or bake — just to heat and serve.

### JVM (Java Virtual Machine) = The oven

Reads the baked cake (bytecode) and knows how to heat and serve it, regardless of the underlying kitchen (your machine’s OS).

#### Flow:

1. Write code → 2. Compile with `javac` → 3. Bytecode `.class` → 4. JVM reads bytecode → 5. Program runs.

---

## 🛠️ 4. Java Environment

What do you need to start Java?

1. **Install JDK**: Your full kitchen setup.
2. **Choose an IDE or Editor**: Like Visual Studio Code or IntelliJ IDEA — where you write code.
3. **Set environment variables**:

   * `JAVA_HOME` → points to your JDK folder.
   * `PATH` → so you can run `javac` in terminal anywhere.
4. **Libraries and dependencies**: Special tools or recipes others shared — like using a premade frosting instead of making your own.

---

## 📄 5. Java Source File Structure

Java is opinionated about how files are organized:

### Basic structure:

```java
// 1. Package (optional): groups related files together
package myapp;

// 2. Import statements: include tools others wrote
import java.util.Scanner;

// 3. Class definition: must match file name
public class Hello {  
   // 4. main method: program's entry point
   public static void main(String[] args) {
      System.out.println("Hello, world!"); // 5. Output statement
   }
}
```

* Filename: `Hello.java`
* Class name: `Hello`
* Convention: start with uppercase; match filename exactly.

---

## 🧩 6. Compilation Process

Think of it as translating your recipe:

1. **Write**: `Hello.java` (English recipe)
2. **Compile** with `javac` → `Hello.class` (translated into bytecode)
3. **Run** with `java Hello` → JVM reads `.class` and executes

Example commands:

```bash
javac Hello.java   // translation step
java Hello         // execution step
```

Notice:

* `.java` → `.class`
* Class name (without extension) is passed to `java` command.

---

## 📚 7. Java Fundamentals (with detail)

### A. Variables and Data Types

* **Variables**: containers for data.
* Simple types:

  * `int` → whole numbers (e.g., `42`)
  * `double` → decimals (e.g., `3.14`)
  * `boolean` → true/false
  * `char` → single character (e.g., `'A'`)
  * `String` → text (e.g., `"Hello"`)

```java
int age = 30;
double price = 99.99;
boolean isOpen = true;
char grade = 'A';
String name = "Alice";
```

### B. Operators

* Math: `+`, `-`, `*`, `/`, `%`
* Comparison: `==`, `!=`, `<`, `>`, `<=`, `>=`
* Logic: `&&`, `||`, `!`

```java
int sum = 5 + 3; // 8
boolean test = (age > 18) && isOpen; // true
```

### C. Control Structures

#### If-else (decision making):

```java
if (age >= 18) {
    System.out.println("Adult");
} else {
    System.out.println("Minor");
}
```

#### Switch (multiple branches):

```java
switch (grade) {
    case 'A': System.out.println("Excellent"); break;
    case 'B': System.out.println("Good"); break;
    default: System.out.println("Keep trying");
}
```

### D. Loops (repetition)

#### For loop:

```java
for (int i = 1; i <= 5; i++) {
    System.out.println("Count: " + i);
}
```

#### While loop:

```java
int i = 1;
while (i <= 5) {
    System.out.println("Count: " + i);
    i++;
}
```

### E. Methods (functions)

Help organize code into reusable blocks:

```java
void greet(String name) {
    System.out.println("Hello, " + name);
}

greet("Bob"); // prints: Hello, Bob
```

### F. Arrays (list of items)

```java
int[] nums = {1, 2, 3, 4, 5};
System.out.println(nums[2]); // prints 3 (0-based index)
```

---

## 🔁 Quick Recap

### Topics covered:

1. **Why use Java** – portable, organized, powerful
2. **History** – from Oak to worldwide standard
3. **JVM/JRE/JDK** – writing, compiling, running explained via kitchen/cake metaphor
4. **Environment setup** – what you need installed and how to configure
5. **Source file structure** – order matters: package → imports → class → main
6. **Compilation process** – from `.java` to `.class`, then run
7. **Fundamental building blocks** – variables, operators, control flow, loops, methods, arrays

---

## 🧩 Programming Structures in Java

### 1. Defining Classes in Java

A **class** is like a blueprint for making **objects**—kind of like a recipe for baking cookies. It defines what attributes and actions the future objects will have:

```java
public class Car {
  String color;
  int year;
  
  void drive() {
    System.out.println("Vroom!");
  }
}
```

* `Car` is the blueprint.
* `color`, `year` are its ingredients (attributes).
* `drive()` is an action you can do (method).

---

### 2. Constructors

A constructor is a **special method** that sets up your object when it’s created. It’s like putting together your cookie dough using a recipe:

```java
public class Car {
  String color;
  int year;
  
  // Constructor
  public Car(String color, int year) {
    this.color = color;
    this.year = year;
  }
}
```

When you write `new Car("Red", 2020)`, it sets the `color` and `year` right away.

---

### 3. Methods

**Methods** are actions your object can perform—like “drive” or “stop”:

```java
public void honk() {
  System.out.println("Beep beep!");
}
```

You can even pass data in and get data out:

```java
public int calculateAge(int currentYear) {
  return currentYear - this.year;
}
```

---

### 4. Access Specifiers

These keywords control who can see your data and methods. It’s like choosing privacy settings:

* **public** – open to everyone
* **private** – only inside the same class
* **protected** – subclasses and package
* no keyword (default) – same package only

```java
private int secret;       // hidden from everyone except Car class
public void showColor();  // visible to all
```

---

### 5. Static Members

**Static** means it belongs to the class itself, not to each object—like a public bulletin board everyone shares:

```java
public static String brand = "Toyota";

public static void printBrand() {
  System.out.println(brand);
}
```

You use them without creating an instance: `Car.printBrand();`

---

### 6. Final Members

**Final** means “constant,” like a locked value your code can’t change:

```java
public final int wheels = 4;
```

Once assigned, `wheels` can’t be modified.

---

### 7. Comments

Use comments to explain code to human readers. They don't affect how the program runs:

```java
// Single-line comment

/*
  Multi-line comment
*/
```

---

### 8. Data Types & Variables

As discussed, Java uses different data types for different kinds of data:

```java
int age = 25;
double salary = 50000.75;
boolean isMarried = false;
char grade = 'B';
String name = "Alice";
```

---

### 9. Operators

* **Arithmetic**: `+`, `-`, `*`, `/`, `%`
* **Comparison**: `==`, `!=`, `<`, `>`
* **Logical**: `&&`, `||`, `!`
* **Assignment**: `=`, `+=`, `-=`

Example:

```java
int sum = 10 + 5;
boolean isAdult = age >= 18;
isSenior = (age >= 60); // reuse variable
```

---

### 10. Control Flow

* **If-else**:

```java
if (age >= 18) {
  System.out.println("Adult");
} else {
  System.out.println("Minor");
}
```

* **Switch**:

```java
switch (grade) {
  case 'A': ...
  default : ...
}
```

* **Loops**:

  * `for`: repeat when you know how many times
  * `while`: repeat while a condition is true
  * `do-while`: runs at least once, then checks

```java
for (int i = 0; i < 5; i++) { ... }
while (condition) { ... }
do { ... } while (condition);
```

---

### 11. Arrays & Strings

* **Array**: container for multiple items of the same type:

```java
int[] nums = {1, 2, 3};
```

* **String**: a special class for text:

```java
String greeting = "Hello";
System.out.println(greeting.length()); // prints 5
String upper = greeting.toUpperCase();
```

---

## 🏗️ Object-Oriented Programming (OOP)

OOP revolves around using **classes and objects**. Think of it as building with Lego blocks:

### 1. Class & Object

* **Class**: blueprint (like `Car` above)
* **Object**: actual item made from blueprint:

```java
Car myCar = new Car("Blue", 2022);
myCar.drive();
```

---

### 2. Inheritance (Super & Sub Class)

Inheritance lets a class use features of another, like a kid inheriting traits from a parent:

```java
public class Vehicle { ... }
public class Car extends Vehicle { ... }
```

* `Vehicle` = **superclass**
* `Car` = **subclass**

---

### 3. Method Overriding

Subclass can **replace** behavior of a superclass method, like fine-tuning how a car drives:

```java
@Override
public void drive() {
  System.out.println("Car driving!");
}
```

---

### 4. Method Overloading

Same method name, different “recipe” (parameters)—like different pizza sizes with the same name:

```java
void greet() { ... }
void greet(String name) { ... }
```

---

### 5. Encapsulation

Keep your data private and give public ways to access it—like how a bank protects your vault with credit card & PIN:

```java
private int age;

public int getAge() { return age; }
public void setAge(int age) { this.age = age; }
```

---

### 6. Polymorphism

One interface, multiple behaviors—like how “drive” means different things for cars, bikes, and boats:

```java
Vehicle v = new Car();
v.drive();  // Car's drive, not Vehicle's
```

---

### 7. Abstraction

Show only necessary details and hide complexity, just like a car's pedals and steering wheel hide all engine complexity.

---

### 8. Interfaces

Declare a list of behaviors that classes promise to do—like a list of will-do chores:

```java
public interface Drivable {
  void drive();
}

public class Car implements Drivable {
  public void drive() { ... }
}
```

---

### 9. Abstract Class

A class that **can't be instantiated** but can have shared behavior and abstract (must-be-implemented) methods—like a school that no student can be, but still defines rules:

```java
public abstract class Animal {
  abstract void makeSound();  
  void eat() { System.out.println("Eating..."); }
}

public class Dog extends Animal {
  void makeSound() { System.out.println("Bark!"); }
}
```

---

## 🎯 Summary Table

| Concept        | Metaphor                    | Example Snippet                                  |
| -------------- | --------------------------- | ------------------------------------------------ |
| Class/Object   | Blueprint & Product         | `Car myCar = new Car(...);`                      |
| Inheritance    | Parent → Child traits       | `class Car extends Vehicle`                      |
| Override       | Customizing parental method | `@Override drive()`                              |
| Overload       | Same name, different params | `greet()`, `greet(String name)`                  |
| Encapsulation  | Bank vault                  | Private fields with getters/setters              |
| Polymorphism   | Multiple behaviors          | `Vehicle v = new Car(); v.drive();`              |
| Abstraction    | User-friendly interface     | Observe behavior, not inner workings             |
| Interface      | Promise list                | `interface Drivable { ... }`                     |
| Abstract Class | Rulebook with fillables     | `abstract class Animal { abstract makeSound();}` |

---

## 📦 What is a **Package** in Java?

### 🔑 Simple Definition:

A **package** is like a **folder** that holds your related Java files (classes, interfaces, etc.) — it helps keep things organized.

### 🧠 Metaphor:

Imagine a **library**. You don’t keep all books in one giant pile — you put **science books** in one section, **novels** in another.
Java does the same with **packages**: keeping similar code grouped together.

### ✅ Why Use Packages?

* Avoid name conflicts (you can have two classes named `Student` in different packages)
* Keep code organized and readable
* Control access (some classes/methods can be hidden from others)

---

## 🏗️ Defining a Package

Use the `package` keyword at the top of your Java file to define which package it belongs to.

```java
package myapp.utilities;

public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
}
```

* File must be saved in a folder that matches the package name:
  → `myapp/utilities/Calculator.java`

---

## 🛠️ CLASSPATH Setting for Packages

### 🧠 What is CLASSPATH?

Java uses **CLASSPATH** to know **where to find your classes**. It tells the Java compiler and JVM where to look for `.class` files when you compile or run code.

By default, Java looks in the **current directory**. But if your class is in another folder (like a package), you need to set CLASSPATH.

### 🔧 Example:

You have this folder structure:

```
myapp/
  └─ utilities/
       └─ Calculator.java
```

### Compile:

```bash
javac myapp/utilities/Calculator.java
```

### Run:

```bash
java myapp.utilities.Calculator
```

> No need to manually set CLASSPATH if your terminal is already in the parent folder of `myapp`.

But if you move the `.class` files elsewhere or use libraries, you may need to set it like:

```bash
set CLASSPATH=.;C:\MyLibs\
```

---

## 📦 Creating JAR Files (Java ARchive)

### 🧠 What’s a JAR?

A **JAR file** is like a **zip file** that groups your `.class` files (or even whole packages). It lets you share and reuse code easily — like publishing a library.

### 🔨 Steps to Make a JAR:

Let’s say you have:

```
myapp/
  └─ utilities/
       └─ Calculator.class
```

### Create a manifest file (optional):

`manifest.txt`:

```
Main-Class: myapp.utilities.Calculator
```

### Create JAR:

```bash
jar cfm Calculator.jar manifest.txt myapp/utilities/*.class
```

### Use JAR:

To run or compile using this `.jar`:

```bash
java -cp Calculator.jar myapp.utilities.Calculator
```

---

## 📥 Importing Packages

### Normal Import:

```java
import myapp.utilities.Calculator;
```

Now you can directly use:

```java
Calculator c = new Calculator();
```

### Import All Classes from a Package:

```java
import myapp.utilities.*;
```

---

## 🔂 Static Import

### What Is Static Import?

If you want to use **static members (like constants or methods)** without writing the class name each time:

```java
import static java.lang.Math.*;

public class Test {
    public static void main(String[] args) {
        System.out.println(sqrt(16)); // instead of Math.sqrt(16)
    }
}
```

---

## 📛 Naming Conventions for Packages

Java recommends **lowercase**, and **reverse domain name style** for unique package names.

### Example:

If your website is `example.com`, your package should be:

```java
package com.example.myapp;
```

This helps avoid name collisions in global projects.

---

## 📚 Summary Table

| Concept           | Meaning / Use                            | Example                              |
| ----------------- | ---------------------------------------- | ------------------------------------ |
| Package           | Folder that organizes related Java files | `package com.myapp.tools;`           |
| CLASSPATH         | Path to tell Java where to find classes  | `set CLASSPATH=.;C:\MyLibs\`         |
| JAR File          | Bundled `.class` files in zip format     | `jar cfm myLib.jar manifest.txt ...` |
| Import            | Use classes from another package         | `import myapp.utilities.Calculator;` |
| Static Import     | Access static members without class name | `import static java.lang.Math.*;`    |
| Naming Convention | Follow domain-style, lowercase           | `package org.company.project;`       |

---

## ✅ Simple Code Example with Package

**Folder structure:**

```
project/
  └─ math/
       └─ Calculator.java
  └─ Main.java
```

**math/Calculator.java**

```java
package math;

public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
}
```

**Main.java**

```java
import math.Calculator;

public class Main {
    public static void main(String[] args) {
        Calculator calc = new Calculator();
        System.out.println("Sum: " + calc.add(2, 3));
    }
}
```

**How to Compile:**

```bash
javac math/Calculator.java Main.java
```

**How to Run:**

```bash
java Main
```

---

