## ❗ What is an **Exception** in Java?

### ✅ **Idea Behind Exception Handling**

An **exception** is a **problem** that occurs during program execution. It's like a **roadblock** — something goes wrong, and Java must deal with it.

> 🧠 **Metaphor:**
> Imagine driving a car. A flat tire (exception) doesn't mean you abandon the car — you stop, fix it, and continue.
> Java does the same with exceptions: **handle** the problem and **continue** safely.

---

## 🆚 Exceptions vs Errors

| Term          | Description                                                                         |
| ------------- | ----------------------------------------------------------------------------------- |
| **Exception** | Problem you **can handle** (e.g., file not found, wrong input)                      |
| **Error**     | Problem you **can’t control or recover from** (e.g., out of memory, stack overflow) |

### Example:

```java
int result = 10 / 0;  // This causes ArithmeticException (dividing by zero)
```

---

## 🧭 Types of Exceptions

1. **Checked Exceptions**:

   * Java **forces you** to handle them.
   * Example: `IOException`, `SQLException`
   * Checked at **compile-time**

2. **Unchecked Exceptions**:

   * Java **doesn't force you** to handle them.
   * Example: `ArithmeticException`, `NullPointerException`
   * Happen during **runtime**

---

## 🔁 Control Flow in Exception Handling

When an exception happens:

1. Java stops running the current code block.
2. It **jumps** to the nearest `catch` block (if available).
3. Executes `finally` block (if present).
4. If not handled, Java crashes and prints an error.

---

## ⚙️ JVM Reaction to Exceptions

If you **don’t handle** an exception, the **Java Virtual Machine (JVM)**:

* Prints an **error message** to the console
* Shows a **stack trace** (what led to the error)
* **Stops the program**

---

## 🧰 Keywords in Exception Handling

### 🔹 `try`

Wraps the code that **might cause** an exception.

### 🔹 `catch`

Handles the exception.

### 🔹 `finally`

Runs **no matter what**, used to close files, release resources, etc.

### 🔹 `throw`

Used to **manually** throw an exception.

### 🔹 `throws`

Used to **declare** that a method might throw an exception.

---

## 🔧 Example: try-catch-finally

```java
public class TryCatchExample {
    public static void main(String[] args) {
        try {
            int result = 10 / 0;  // This will cause ArithmeticException
            System.out.println("This won't print");
        } catch (ArithmeticException e) {
            System.out.println("Error: Can't divide by zero!");
        } finally {
            System.out.println("This always runs.");
        }
    }
}
```

✅ Output:

```
Error: Can't divide by zero!
This always runs.
```

---
 
## 🚀 Using `throw`

You can manually **throw an exception**.

```java
public class ThrowExample {
    public static void main(String[] args) {
        int age = 15;
        if (age < 18) {
            throw new ArithmeticException("You must be 18 or older.");
        }
    }
}
```

---

## 🧾 Using `throws`

If a method might throw a **checked exception**, you must declare it.

```java
public void readFile(String fileName) throws IOException {
    FileReader file = new FileReader(fileName);
}
```

---

## 🔄 In-Built Exceptions in Java

Some commonly used Java exceptions:

| Exception               | Description                 |
| ----------------------- | --------------------------- |
| `ArithmeticException`   | Dividing by zero            |
| `NullPointerException`  | Using a null object         |
| `ArrayIndexOutOfBounds` | Accessing wrong array index |
| `FileNotFoundException` | File doesn't exist          |
| `IOException`           | Problem with input/output   |

---

## 👤 User-Defined Exceptions

You can **create your own** exception class by extending `Exception` or `RuntimeException`.

```java
class AgeException extends Exception {
    public AgeException(String message) {
        super(message);
    }
}

public class Test {
    public static void main(String[] args) throws AgeException {
        int age = 16;
        if (age < 18) {
            throw new AgeException("You are underage!");
        }
    }
}
```

---

## ✅ Checked vs Unchecked Exceptions

| Type         | Checked Exception             | Unchecked Exception                           |
| ------------ | ----------------------------- | --------------------------------------------- |
| Checked At   | Compile-time                  | Runtime                                       |
| Must Handle? | Yes                           | No                                            |
| Examples     | `IOException`, `SQLException` | `ArithmeticException`, `NullPointerException` |
| Parent Class | `Exception`                   | `RuntimeException`                            |

---

## 🧪 Summary Cheat Sheet

| Keyword   | Use                            |
| --------- | ------------------------------ |
| `try`     | Wrap risky code                |
| `catch`   | Handle exception               |
| `finally` | Always runs                    |
| `throw`   | Manually throw an exception    |
| `throws`  | Declare a method may throw one |

---

## 👨‍💻 Practice Example: User Input with Exception Handling

```java
import java.util.Scanner;

public class SafeDivision {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        try {
            System.out.print("Enter numerator: ");
            int num = sc.nextInt();
            System.out.print("Enter denominator: ");
            int den = sc.nextInt();

            int result = num / den;
            System.out.println("Result: " + result);
        } catch (ArithmeticException e) {
            System.out.println("You can't divide by zero.");
        } catch (Exception e) {
            System.out.println("Invalid input.");
        } finally {
            System.out.println("Closing scanner.");
            sc.close();
        }
    }
}
```

---

## 📥📤 What is I/O in Java?

I/O stands for **Input and Output** — it's how a program reads data **from** the outside (keyboard, file, network), or writes data **to** something (console, file, etc.).

---

## 🧠 Metaphor:

Imagine your program as a **person**:

* **Input** is like listening or reading.
* **Output** is like speaking or writing.

---

## 🔁 Java I/O Streams

Java uses something called **streams** to do I/O.

### 🔸 Stream:

A **stream** is like a pipe — it carries **data** from one place to another, one piece at a time.

Java has two main types of streams:

---

## 1️⃣ Byte Streams

### ➡️ Used For:

* **Binary data** (images, audio, video, etc.)
* Raw bytes

### 📦 Classes:

* `InputStream` (for reading)
* `OutputStream` (for writing)

### ✍️ Example: Writing bytes to a file

```java
import java.io.FileOutputStream;

public class ByteWriteExample {
    public static void main(String[] args) {
        try {
            FileOutputStream fos = new FileOutputStream("data.bin");
            fos.write(65);  // Writes 'A'
            fos.close();
            System.out.println("Byte written.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

### 📖 Example: Reading bytes from a file

```java
import java.io.FileInputStream;

public class ByteReadExample {
    public static void main(String[] args) {
        try {
            FileInputStream fis = new FileInputStream("data.bin");
            int data = fis.read(); // Reads one byte
            System.out.println("Byte read: " + data); // Output: 65
            fis.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

## 2️⃣ Character Streams

### ➡️ Used For:

* **Text data** (like reading/writing `.txt` files)
* Handles **characters**, not raw bytes

### 📦 Classes:

* `FileReader` (for reading)
* `FileWriter` (for writing)

### 📝 Writing text to a file

```java
import java.io.FileWriter;

public class CharWriteExample {
    public static void main(String[] args) {
        try {
            FileWriter fw = new FileWriter("notes.txt");
            fw.write("Hello, world!");
            fw.close();
            System.out.println("Text written.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

### 📖 Reading text from a file

```java
import java.io.FileReader;

public class CharReadExample {
    public static void main(String[] args) {
        try {
            FileReader fr = new FileReader("notes.txt");
            int ch;
            while ((ch = fr.read()) != -1) {
                System.out.print((char) ch); // Converts int to char
            }
            fr.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

## 📊 Byte Stream vs Character Stream Comparison

| Feature      | Byte Stream                           | Character Stream           |
| ------------ | ------------------------------------- | -------------------------- |
| Handles      | Raw bytes (binary)                    | Text (characters)          |
| Base classes | `InputStream` / `OutputStream`        | `Reader` / `Writer`        |
| Use case     | Images, files, network data           | Text files, strings        |
| Examples     | `FileInputStream`, `FileOutputStream` | `FileReader`, `FileWriter` |

---

## 📎 Note on File Paths

When using files, always:

* Give **correct path**
* **Close** your stream (or use `try-with-resources`)
* Handle **exceptions**

---

## 🚀 Summary

| Concept          | What it Does                | Example Class                         |
| ---------------- | --------------------------- | ------------------------------------- |
| Byte Stream      | Read/write binary data      | `FileInputStream`, `FileOutputStream` |
| Character Stream | Read/write text             | `FileReader`, `FileWriter`            |
| Input            | Get data from file/keyboard | `InputStream`, `Reader`               |
| Output           | Send data to file/screen    | `OutputStream`, `Writer`              |

---

## 🧵 What is a **Thread**?

### 🔹 Simple Definition:

A **thread** is like a **separate path** of execution inside your program. Multithreading means your program can **do multiple things at the same time**.

### 🧠 Metaphor:

Imagine you're a chef cooking a big meal:

* One thread is boiling water.
* Another is chopping vegetables.
* Another is baking.

Each task can run **independently**, but together, they **speed up the process**.

---

## 🔄 Thread Life Cycle

A thread goes through **5 main stages**:

| State          | Description                                   |
| -------------- | --------------------------------------------- |
| **New**        | Thread is created but not started yet         |
| **Runnable**   | Thread is ready to run, waiting for CPU       |
| **Running**    | Thread is actually running                    |
| **Blocked**    | Thread is waiting to access a locked resource |
| **Terminated** | Thread has finished or been stopped           |

---

## 👨‍💻 How to Create a Thread in Java

There are **2 main ways**:

### ✅ Method 1: Extend the `Thread` class

```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread running!");
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread t1 = new MyThread();
        t1.start();  // Don't use run(); use start()
    }
}
```

---

### ✅ Method 2: Implement the `Runnable` interface

```java
class MyTask implements Runnable {
    public void run() {
        System.out.println("Runnable running!");
    }
}

public class Main {
    public static void main(String[] args) {
        Thread t2 = new Thread(new MyTask());
        t2.start();
    }
}
```

> 🧠 Why use `Runnable`?
> Because Java doesn’t support **multiple inheritance** — if your class already extends another, use `Runnable`.

---

## ⚙️ Thread Priorities

Each thread can be assigned a **priority** from **1 (MIN)** to **10 (MAX)**.
Java will **prefer** to run threads with higher priority, but doesn’t guarantee it.

```java
t1.setPriority(Thread.MAX_PRIORITY);  // 10
t2.setPriority(Thread.MIN_PRIORITY);  // 1
```

> Default is **5** (`Thread.NORM_PRIORITY`)

---

## 🔒 Synchronizing Threads

When multiple threads access **shared data**, it can lead to errors. **Synchronization** helps prevent **data corruption**.

### 🧠 Metaphor:

Imagine multiple people writing to the same whiteboard at the same time — they can overwrite each other. Synchronization makes them **wait their turn**.

### Example without synchronization:

```java
class Counter {
    int count = 0;

    void increment() {
        count++;
    }
}
```

### With synchronization:

```java
class Counter {
    int count = 0;

    synchronized void increment() {
        count++;
    }
}
```

---

## 🔄 Inter-thread Communication

### 🧠 What is it?

Sometimes threads need to **talk** to each other — like one waits for another to finish or give it a signal.

Java uses these methods for communication:

* `wait()` – thread waits for signal
* `notify()` – wakes up one waiting thread
* `notifyAll()` – wakes up all waiting threads

### 👇 Example (very simple):

```java
class Shared {
    synchronized void printMessage() {
        try {
            wait();  // wait until notified
            System.out.println("Message received!");
        } catch (InterruptedException e) {
            System.out.println(e);
        }
    }

    synchronized void sendMessage() {
        System.out.println("Sending message...");
        notify();  // wake up waiting thread
    }
}
```

---

## ✅ Summary Table

| Topic                          | Description                                           | Example                                 |
| ------------------------------ | ----------------------------------------------------- | --------------------------------------- |
| **Thread**                     | A lightweight path of execution                       | `extends Thread`, `implements Runnable` |
| **Life Cycle**                 | States: New, Runnable, Running, Blocked, Terminated   | -                                       |
| **Thread Priority**            | Prefer running higher-priority threads                | `setPriority(1-10)`                     |
| **Synchronization**            | Prevents multiple threads from corrupting shared data | `synchronized` keyword                  |
| **Inter-thread Communication** | Threads waiting or notifying each other               | `wait()`, `notify()`, `notifyAll()`     |

---

## 💡 Bonus: Running Multiple Threads

```java
class Task extends Thread {
    public void run() {
        for (int i = 1; i <= 5; i++) {
            System.out.println(Thread.currentThread().getName() + ": " + i);
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Task t1 = new Task();
        Task t2 = new Task();

        t1.setName("Thread-A");
        t2.setName("Thread-B");

        t1.start();
        t2.start();
    }
}
```

> 🧠 Both threads run in **parallel** — you’ll see mixed output.

---

