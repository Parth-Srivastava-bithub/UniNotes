## 🔰 1. **Collection in Java**

🧒 *Socho tumhare paas chocolates ka dabba hai — usme alag alag chocolates (data) store kar sakte ho.*

**Java me bhi, Collection matlab:**

> Data ka group ya box jisme multiple cheeze (objects) store karte ho.

Example:

```java
List<String> names = new ArrayList<>();
names.add("Ram");
names.add("Shyam");
```

---

## 🧺 2. **Collection Framework in Java**

🧒 *Jaise alag alag dabbe milte hain: jisme line me rakh sakte ho, jisme peeche se nikaal sakte ho, jisme duplicate nahi rakh sakte ho…*

> **Framework** = Ready-made tools + rules to store and manage data.

Framework me aata hai:

* Interfaces: List, Set, Queue
* Classes: ArrayList, LinkedList, HashSet, Stack, etc.
* Algorithms: sort, search, etc.

---

## 🌳 3. **Hierarchy of Collection Framework**

```
              Iterable
                 |
             Collection
         ________|________
        |        |        |
      List      Set     Queue
        |        |
  ArrayList   HashSet
  LinkedList  TreeSet
```

🧒 *Jaise ek bada family tree ho — sabka relation samajh aata hai.*

---

## 👣 4. **Iterator Interface**

🧒 *Socho tumhare paas ek remote hai jo ek ek chocolate nikalta hai dabbe se.*

> Iterator = Ek tool jo collection ke andar ek ek item ko access karta hai.

Example:

```java
Iterator<String> it = names.iterator();
while(it.hasNext()) {
    System.out.println(it.next());
}
```

---

## 📦 5. **Collection Interface**

Ye **sabka parent** interface hai. Iske andar basic rules hain sab collections ke liye — jaise `add()`, `remove()`, `size()`.

🧒 *Jaise mummy bole: "Jo bhi dabba lo, usme yeh 3 rule honi chahiye: cheez dalo, nikalo, gin lo."*

---

## 📋 6. **List Interface**

> **List** = Order maintained hota hai, duplicates allowed.

🧒 *Jaise line me bacche khade hain — naam bhi repeat ho sakta hai, lekin order same hai.*

Popular List types:

* ArrayList
* LinkedList
* Vector
* Stack

---

## 📥 7. **ArrayList**

> Fast for searching, slow for insert/delete in middle.

🧒 *Jaise ek badi almari jisme sab kuch ek line me hai. Agar beech me kuch ghusaoge, sab hil jayega.*

Example:

```java
List<String> list = new ArrayList<>();
list.add("A");
list.add("B");
```

---

## 🔗 8. **LinkedList**

> Fast for inserting/removing, slow for searching.

🧒 *Jaise train ke bogie – beech me asani se ek aur bogie jod sakte ho.*

Example:

```java
List<String> list = new LinkedList<>();
list.add("X");
list.add("Y");
```

---

## 🛡️ 9. **Vector**

> Old version of ArrayList, but **Thread-safe** (multiple users = no fight).

🧒 *Jaise ek classroom jahan monitor sabko turn by turn bolne deta hai.*

Example:

```java
Vector<Integer> v = new Vector<>();
v.add(10);
v.add(20);
```

---

## 📚 10. **Stack**

> **LIFO** (Last In First Out)

🧒 *Jaise tumne books rakhe — jo sabse upar rakhi, wahi pehle nikalti hai.*

Example:

```java
Stack<Integer> stack = new Stack<>();
stack.push(1); // daala
stack.push(2);
System.out.println(stack.pop()); // nikla 2
```

---

## 📬 11. **Queue Interface**

> **FIFO** (First In First Out)

🧒 *Jaise line me sab khade hain – jo pehle aaya, wahi pehle jayega.*

Common Queue types:

* PriorityQueue
* LinkedList (also implements Queue)

Example:

```java
Queue<String> queue = new LinkedList<>();
queue.add("Amit");
queue.add("Sumit");
System.out.println(queue.poll()); // "Amit"
```

---

### 🔁 Quick Summary Table

| Interface/Class | Order | Duplicate | Fast For        | Special |
| --------------- | ----- | --------- | --------------- | ------- |
| List            | Yes   | Yes       | Access/Search   |         |
| ArrayList       | Yes   | Yes       | Search          |         |
| LinkedList      | Yes   | Yes       | Insert/Delete   |         |
| Vector          | Yes   | Yes       | Thread-Safe     | Old     |
| Stack           | Yes   | Yes       | LIFO Operations |         |
| Queue           | Yes   | Yes       | FIFO Operations |         |

---

## 🧩 1. **Set Interface**

**Kya hota hai?**

> Set = Aisi list jisme **duplicate cheezein allowed nahi hoti.**

🧒 *Jaise tumhare paas stickers ka album hai — ek hi sticker baar-baar nahi rakhte.*

---

## 🧺 2. **HashSet**

> Fastest Set. Order **maintain nahi hota**, **duplicate** nahi hota.

🧒 *Jaise ek box jisme tum sab cheeze daalte ho bina kisi order ke. Bas ek hi cheez baar-baar nahi daal sakte.*

**Example:**

```java
Set<String> set = new HashSet<>();
set.add("Apple");
set.add("Mango");
set.add("Apple"); // Ignore hoga
```

---

## 🧾 3. **LinkedHashSet**

> Same as HashSet, lekin **jo order me daala, usi order me niklega**.

🧒 *Jaise tum ek notebook me likhte ja rahe ho — likhne ka order yaad rahega.*

**Example:**

```java
Set<String> set = new LinkedHashSet<>();
set.add("Cat");
set.add("Dog");
set.add("Cat"); // Ignore
```

---

## 🧭 4. **SortedSet Interface**

> Set jisme elements **sorted (sorted order)** me rehte hain.

🧒 *Jaise tumhare toys size ke hisaab se arranged ho.*

`TreeSet` isme use hota hai.

---

## 🌳 5. **TreeSet**

> SortedSet ka implementation. **Sorted + No Duplicates**

🧒 *Jaise ABCD ke order me arranged items — aur koi repeat nahi.*

**Example:**

```java
Set<Integer> set = new TreeSet<>();
set.add(30);
set.add(10);
set.add(20);
// Output: 10, 20, 30
```

---

## 🗺️ 6. **Map Interface**

> Key-Value pair store karta hai.

🧒 *Jaise tumhara school diary — "Subject" (key) ke against "Homework" (value) likha hota hai.*

---

## 🔢 7. **HashMap Class**

> Fastest Map. Keys unique hoti hain. Order maintain nahi hota.

🧒 *Jaise ek box jisme "Name → Phone number" likh ke rakhte ho, lekin koi specific order nahi.*

**Example:**

```java
Map<String, String> map = new HashMap<>();
map.put("Amit", "1234");
map.put("Ram", "5678");
```

---

## 🔄 8. **LinkedHashMap Class**

> HashMap + Insertion Order

🧒 *Jaise tum diary me likhte ho — jo pehle likha, wo pehle dikhega.*

**Example:**

```java
Map<String, String> map = new LinkedHashMap<>();
map.put("X", "1");
map.put("Y", "2");
// Output: X=1, Y=2
```

---

## 🌳 9. **TreeMap Class**

> Map in **sorted order of keys**

🧒 *Jaise English dictionary — sab words A-Z sorted hote hain.*

**Example:**

```java
Map<Integer, String> map = new TreeMap<>();
map.put(3, "Three");
map.put(1, "One");
// Output: 1=One, 3=Three
```

---

## 🧯 10. **Hashtable Class**

> Old version of HashMap. Thread-safe, slower. No `null` keys/values allowed.

🧒 *Jaise ek locker system jisme sab kuch secure hai, lekin thoda slow hai.*

**Example:**

```java
Hashtable<String, String> ht = new Hashtable<>();
ht.put("A", "Apple");
```

---

## 🔤 11. **Sorting in Java**

> Java me list ya array ko ascending/descending order me arrange kar sakte ho.

### A. **Comparable Interface**

> Tumhare object khud decide karein kaise sort hoga. **Natural order**.

🧒 *Jaise tum bolo: “Main height ke hisaab se line me lagunga.”*

```java
class Student implements Comparable<Student> {
    int marks;
    public int compareTo(Student s) {
        return this.marks - s.marks; // ascending
    }
}
```

---

### B. **Comparator Interface**

> Bahar wala koi decide karein kaise sort hoga. **Custom sort logic**.

🧒 *Jaise teacher bole: “Sab bacche name ke hisaab se line me lag jao.”*

```java
Comparator<Student> byName = (s1, s2) -> s1.name.compareTo(s2.name);
```

---

## ⚙️ 12. **Properties Class**

> Key-value pairs for **configuration files** (usually Strings).

🧒 *Jaise tumhare game ka setting file — sound=on, level=3, etc.*

**Example:**

```java
Properties props = new Properties();
props.setProperty("user", "admin");
props.setProperty("password", "1234");
System.out.println(props.getProperty("user")); // admin
```

---

### 📌 Quick Recap Table:

| Feature       | Key Info                        | Real-Life Analogy                 |
| ------------- | ------------------------------- | --------------------------------- |
| HashSet       | No duplicates, no order         | Toys box with unique toys         |
| LinkedHashSet | No duplicates + maintains order | Notebook with unique entries      |
| TreeSet       | Sorted + no duplicates          | ABCD arranged toys                |
| HashMap       | Key-Value, fast, no order       | Dictionary without order          |
| LinkedHashMap | Key-Value + order               | Diary entries                     |
| TreeMap       | Key-Value + sorted by key       | Sorted dictionary                 |
| Hashtable     | Old, thread-safe map            | Safe but slow locker              |
| Comparable    | Object compares itself          | Baccha khud decide karta hai      |
| Comparator    | External comparison logic       | Teacher decides kaise line lagegi |
| Properties    | Key-value for config            | Game settings                     |

---

