### 1. **Functional Interface**

**Kya hota hai?**
Ek interface jisme **sirf 1 kaam (method)** hota hai.

🧒 *Jaise ek remote sirf TV chalu karne ke liye ho.*

**Example:**

```java
@FunctionalInterface
interface MyTask {
    void doWork();
}
```

---

### 2. **Lambda Expression**

**Kya hota hai?**
Short-cut tareeka method likhne ka.

🧒 *Jaise "main pani pi leta hoon" ki jagah bolna "pani" — sab samajh jaate hain.*

**Example:**

```java
MyTask task = () -> System.out.println("Kaam ho gaya!");
```

---

### 3. **Method Reference**

**Kya hota hai?**
Agar method already bana hua hai, to uska naam seedha de do.

🧒 *Jaise mama already chai bana rahe ho, to bolna: “Mujhe bhi wahi chai de do.”*

**Example:**

```java
public class Helper {
    static void greet() {
        System.out.println("Hello!");
    }
}

MyTask task = Helper::greet;
```

---

### 4. **Stream API**

**Kya hota hai?**
List ya data ke upar **pipeline jaise kaam** karna – filter, sort, map, collect.

🧒 *Jaise ek conveyor belt pe mithai aaye, tum bas achhi wali utha lo.*

**Example:**

```java
List<String> names = List.of("Ram", "Shyam", "Anu");
names.stream().filter(n -> n.startsWith("A")).forEach(System.out::println);
```

---

### 5. **Default Methods (Interface ke andar)**

**Kya hota hai?**
Interface ke andar method bana sakte ho **jo already kaam karta ho**.

🧒 *Jaise agar toy khud hi bolta ho “Hello”, tumhe kuch nahi karna.*

**Example:**

```java
interface MyToy {
    default void sayHello() {
        System.out.println("Hello from toy!");
    }
}
```

---

### 6. **Static Method in Interface**

**Kya hota hai?**
Interface me bhi static method bana sakte ho.

🧒 *Jaise ek rule book me likha ho – “Sabko namaste bolna hai.” Ye sabke liye hai.*

**Example:**

```java
interface Greet {
    static void sayHi() {
        System.out.println("Hi Everyone!");
    }
}
```

---

### 7. **Base64 Encode/Decode**

**Kya hota hai?**
Data ko chhupa ke bhejna (Encode), aur fir wapas asli banana (Decode).

🧒 *Jaise secret chitti likhna jisko sirf tum decode kar sakte ho.*

**Example:**

```java
String text = "Hello";
String encoded = Base64.getEncoder().encodeToString(text.getBytes());
String decoded = new String(Base64.getDecoder().decode(encoded));
```

---

### 8. **forEach Method (List ke liye)**

**Kya hota hai?**
List me se ek ek cheez nikaal kar kaam karo.

🧒 *Jaise chocolates ki list ho aur tum har ek ko kha ke bolo “Yummy!”*

**Example:**

```java
List<String> list = List.of("Choco", "Candy");
list.forEach(item -> System.out.println(item));
```

---

### 9. **Try-With-Resources**

**Kya hota hai?**
Koi cheez use karo aur use khud-ba-khud band ho jaaye.

🧒 *Jaise water bottle pee ke khud hi band ho jaaye.*

**Example:**

```java
try (BufferedReader br = new BufferedReader(new FileReader("file.txt"))) {
    System.out.println(br.readLine());
}
```

---

### 10. **Type Annotations**

**Kya hota hai?**
Variables ko aur clearly describe karne ke liye @Annotation laga sakte ho.

🧒 *Jaise tum apna naam likho aur niche likho “Smart Kid”.*

**Example:**

```java
@NonNull String name;
```

---

### 11. **Repeating Annotations**

**Kya hota hai?**
Ek hi annotation ko ek cheez pe baar-baar lagana.

🧒 *Jaise tum ek drawing pe baar baar star bana do – ek se zyada baar.*

**Example:**

```java
@Schedule(day = "Monday")
@Schedule(day = "Tuesday")
void work() {}
```

---

### 1. **Inner Anonymous Class**

**Kya hota hai?**
Ek class jo bina naam ke, turant banai jaati hai — ek hi baar kaam ke liye.

🧒 *Jaise ek robot tumhare liye ek baar kaam karta hai, fir chala jaata hai, naam bhi nahi poochte.*

**Example:**

```java
Runnable r = new Runnable() {
    public void run() {
        System.out.println("Kaam ho gaya by nameless robot");
    }
};
```

---

### 2. **Local Variable Type Inference (`var`)**

**Kya hota hai?**
Java khud samajh jata hai variable ka type — tumhe batana nahi padta.

🧒 *Jaise tum kaho “yeh khelne wali cheez hai” aur mummy khud samajh jayein “ball hai”.*

**Example:**

```java
var name = "Amit"; // Java samajh gaya yeh String hai
var number = 5;    // Java samajh gaya yeh int hai
```

---

### 3. **Switch Expressions**

**Kya hota hai?**
Switch ko ab aur short aur powerful banaya gaya hai – value return karta hai.

🧒 *Jaise tum bolo “Mujhe batao Monday ko kya hota hai?” – aur tumhe direct answer mil jaye.*

**Example:**

```java
String dayType = switch (day) {
    case "Saturday", "Sunday" -> "Holiday";
    default -> "Working Day";
};
```

---

### 4. **`yield` Keyword**

**Kya hota hai?**
Switch expression me result return karne ke liye `yield` likhte hain.

🧒 *Jaise tum bolo “mujhe yeh result dedo” — yield matlab “yeh lo result”.*

**Example:**

```java
String result = switch (value) {
    case 1 -> {
        yield "One";
    }
    default -> {
        yield "Unknown";
    }
};
```

---

### 5. **Text Blocks**

**Kya hota hai?**
Lambi multi-line text likhne ke liye easy syntax (triple quotes).

🧒 *Jaise ek kahani likhne ke liye alag alag line banana asaan ho.*

**Example:**

```java
String message = """
    Hello,
    This is a text block.
    Easy to read!
    """;
```

---

### 6. **Records**

**Kya hota hai?**
Quick tareeka data-holding class banane ka — getters, constructor sab milta auto.

🧒 *Jaise tum ek form bharo – naam, umar – aur computer khud samajh jaye kaun ho tum.*

**Example:**

```java
record Person(String name, int age) {}
```

Use:

```java
Person p = new Person("Amit", 10);
System.out.println(p.name()); // "Amit"
```

---

### 7. **Sealed Classes**

**Kya hota hai?**
Tum restrict kar sakte ho ki kaun kaun class isko extend kar sakti hai.

🧒 *Jaise tum bolo – sirf Ram aur Shyam hi is room me aa sakte hain, aur koi nahi.*

**Example:**

```java
sealed class Animal permits Dog, Cat {}

final class Dog extends Animal {}
final class Cat extends Animal {}
```

---

### Summary (Super Simple Memory Tip):

* 👤 **Anonymous Class** – Naam nahi, kaam done.
* 📝 **var** – Java khud samjhta hai.
* 🔄 **Switch Expression** – Short aur return deta hai.
* 🎁 **yield** – "Lo bhai result".
* 📃 **Text Block** – Multi-line likhna easy.
* 🗃️ **Record** – Fast form wala class.
* 🚪 **Sealed** – Only allowed classes hi andar.

---


