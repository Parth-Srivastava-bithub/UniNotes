* 🔍 **Kya hota hai?**
* 👁️ **Kaise dikhta hai?**
* ❓ **Kyu use karte hain?**
* 🧒 **Real-life analogy (5 saal ke bacche jaisi language)**

---

## 🌱 1. **Spring Core Basics**

🔍 **Kya hai?**
Spring ka core part mainly **IoC (Inversion of Control)** aur **DI (Dependency Injection)** pe based hai. Ye Spring ke foundation concepts hain.

👁️ **Kaise dikhta hai?**
Application me multiple classes hoti hain, aur unke dependencies (jaise database access, service classes) Spring khud handle karta hai.

❓ **Kyu use hota hai?**
Taaki:

* Code loosely coupled ho
* Reuse ho sake
* Maintenance easy ho

🧒 **Example:**
Tumhara school bag mummy pack karti hai — tum bas school jaate ho. Tumhe pata bhi nahi hota kaunsa box me kya hai. Spring bhi aise hi code ke liye saman ready karta hai.

---

## 🔄 2. **Spring Dependency Injection (DI)**

🔍 **Kya hai?**
Jab ek object doosre object pe depend karta hai, toh Spring us dependency ko “inject” karta hai.

👁️ **Kaise dikhta hai?**

* Field injection (direct field me)
* Constructor injection
* Setter injection

❓ **Kyu use hota hai?**

* Manual object creation se bachne ke liye
* Testing easy ho jati hai (mock cheeze inject kar sakte ho)

🧒 **Example:**
Tum painting karte ho, mummy ne already brush, colors, water sab ready rakha hota hai. Tumhe kuch lana nahi padta. Same, class ko kuch chahiye toh Spring deta hai.

---

## 🔁 3. **Spring Inversion of Control (IoC)**

🔍 **Kya hai?**
Normally hum objects banate hain. IoC me Spring objects banata hai aur provide karta hai.

👁️ **Kaise dikhta hai?**
Spring Container (like ApplicationContext) sab object manage karta hai.

❓ **Kyu use hota hai?**

* Application ke logic pe focus rakh sakein
* Object lifecycle manage ho easily

🧒 **Example:**
Tum Santa Claus ho — sabko gifts dene ka plan tha, lekin Santa hi tumhare liye gift le aaya. Tumhe kuch nahi karna, bus use lena hai.

---

## ✨ 4. **AOP (Aspect Oriented Programming)**

🔍 **Kya hai?**
App me kuch kaam baar-baar har jagah karna padta hai (jaise logging, security). AOP inhe main code se alag rakhta hai.

👁️ **Kaise dikhta hai?**

* Aspect (logic)
* Advice (kab chale)
* Pointcut (kaha chale)
* Join point (actual jagah)

❓ **Kyu use hota hai?**

* Repeated code avoid karne
* Code clean aur modular banane

🧒 **Example:**
Jaise mummy har kaam ke baad bole “Well done!” — har bar ye bolne ki jagah, koi aur kare toh tumhara kaam asaan ho jaata hai.

---

## 📦 5. **Bean Scopes**

**Bean** = Spring ke dwara banaya gaya object
**Scope** = Ye object kab aur kitni baar banta hai

---

### 🔹 a) Singleton

🔍 **Kya hai?**
Spring default scope. Sirf **ek hi object** banta hai poore app ke liye.

👁️ **Kaise dikhta hai?**
Har bar same instance milega.

❓ **Kyu use?**

* Memory efficient
* Jab shared resource chahiye ho

🧒 **Example:**
Ghar me ek hi fridge hai — sab usi ko use karte hain.

---

### 🔹 b) Prototype

🔍 **Kya hai?**
Har baar **naya object** banta hai jab bhi bean chahiye.

❓ **Kyu use?**
Jab har user/activity ke liye fresh object chahiye ho.

🧒 **Example:**
Ghar me sabko alag toothbrush milta hai — sabka apna.

---

### 🔹 c) Request

🔍 **Kya hai?**
Har HTTP request ke liye naya bean.

👁️ **Kaise dikhta hai?**
Web app me use hota hai — har request par naya object milta hai.

🧒 **Example:**
Tum pizza order karte ho, tumhara order alag, kisi aur ka alag.

---

### 🔹 d) Session

🔍 **Kya hai?**
User session ke dauran ek bean — jab tak login hai, tab tak same object.

🧒 **Example:**
Tumhara school ID card jab tak tum class me ho — tumhara hi hai.

---

### 🔹 e) Application

🔍 **Kya hai?**
Poore application ke liye ek object — sab user ke liye same.

🧒 **Example:**
School me ek hi bell system — sab ke liye wahi.

---

### 🔹 f) WebSocket

🔍 **Kya hai?**
Real-time communication ke liye — ek socket connection ka object.

🧒 **Example:**
Phone call jab tak chalu hai — ek hi line se tum baat karte ho.

---

## 🔧 6. **Autowiring**

🔍 **Kya hai?**
Spring automatically dependencies ko inject kar deta hai — manual batane ki zarurat nahi.

👁️ **Kaise dikhta hai?**
Just use `@Autowired` and Spring will handle it.

❓ **Kyu use?**

* Code chhota aur clean hota hai
* Spring khud samajh leta hai kaunsa object kahan chahiye

🧒 **Example:**
Mummy bina pooche tumhare plate me tumhara favourite sabzi rakh deti hain — unhe pata hai kya pasand hai.

---

## 🏷️ 7. **Annotations**

🔍 **Kya hai?**
Special markers jo Spring ko batate hain kya kaam karna hai.

👁️ **Kaise dikhta hai?**
Like `@Component`, `@Service`, `@Controller`, etc.

❓ **Kyu use?**

* Config easy ho jata hai
* Code readable aur declarative ban jaata hai

🧒 **Example:**
Copy ke upar likha ho “Homework” — pata chal gaya ye homework ka part hai.

---

## 🔄 8. **Lifecycle Callbacks**

🔍 **Kya hai?**
Bean banne ke baad aur destroy hone se pehle kuch kaam karwana.

👁️ **Kaise dikhta hai?**

* init method
* destroy method
* annotations like `@PostConstruct`, `@PreDestroy`

❓ **Kyu use?**

* Resource open/close karne
* Initialization tasks run karne

🧒 **Example:**
Tumhara toy factory me pehle test hota hai, fir box me daala jaata hai, fir becha jaata hai.

---

## 🛠️ 9. **Bean Configuration Styles**

Teen tareeke hain bean ko define karne ke:

---

### 🔹 a) XML Based

👁️ **Kaise dikhta hai?**
Beans ko XML file me likhte ho.

🧒 *Jaise ek recipe card pe likh do — kya banana hai, kaise banana hai.*

---

### 🔹 b) Annotation Based

👁️ **Kaise dikhta hai?**
Beans pe annotation lagake Spring ko batate ho.

🧒 *Jaise tumhare bag pe tag laga ho “Amit ka bag” — sab samajh jaate hain.*

---

### 🔹 c) Java Config Based

👁️ **Kaise dikhta hai?**
Java class ke through bean banate ho using `@Configuration` and `@Bean`.

🧒 *Jaise mummy ko directly bol do “mujhe paratha banana hai” — vo bana deti hain.*

---

## ✅ FINAL RECAP TABLE

| Concept     | Kya hai?                          | Bacche ka Example                   |
| ----------- | --------------------------------- | ----------------------------------- |
| DI          | Object chahiye to Spring deta hai | Mummy brush, color ready rakhti hai |
| IoC         | Spring control me object creation | Santa gift de raha                  |
| AOP         | Repeated kaam alag se hota hai    | Mummy har kaam ke baad taali bajaye |
| Singleton   | Ek hi object sabke liye           | Ghar ka fridge                      |
| Prototype   | Naya object har bar               | Sabka apna toothbrush               |
| Autowiring  | Auto object injection             | Mummy favourite khana serve kar de  |
| Annotations | Tags for instructions             | “Homework” likha copy pe            |
| Lifecycle   | Init & destroy phases             | Toy test → pack → sell              |
| Bean Config | XML, Annotations, Java config     | Recipe likhna ya                    |

---

## 🚀 1. **Spring Boot Build Systems**

🔹 **Maven** / **Gradle** — Tools jo project ko **build/run/manage** karne me madad karte hain.
🔹 Batate ho:

* Kaun se dependencies chahiye
* App ka structure kya hai
  🔹 Mostly `pom.xml` (Maven) ya `build.gradle` (Gradle) use hota hai.

🧒 *Jaise mummy ka grocery list — kya kya saman lana hai likh rakha hai.*

---

## 🗂️ 2. **Spring Boot Code Structure**

```
src/
 └── main/
     ├── java/       → main code yahan
     └── resources/  → config files (like application.properties)
```

🔹 Ek `@SpringBootApplication` class hoti hai jahan se app start hota hai
🔹 `application.properties` ya `application.yml` me settings hoti hain (port, DB etc.)

---

## 🏃‍♂️ 3. **Spring Boot Runners**

🔹 App start hote hi agar koi kaam karwana ho, toh `CommandLineRunner` ya `ApplicationRunner` use karte hain
🔹 Useful for:

* Data initialize karna
* Logs print karna
* System check karna

🧒 *Jaise school jaate hi pehle attendance hoti hai.*

---

## 📢 4. **Logger**

🔹 Console ya file me logs print karne ke liye
🔹 Alag-alag level: `info`, `debug`, `error`, `warn`
🔹 Helps in debugging aur app monitoring

🧒 *Jaise teacher diary me likh rahi ho: "Homework done", "Absent", "Late".*

---

## 🌐 5. **Building RESTful Web Services**

REST APIs = Web ke zariye data exchange ka tareeka

### 🔸 **@RestController**

Marks a class as REST API handler (no HTML, only JSON/text response)

### 🔸 **@RequestMapping / @GetMapping / @PostMapping / @PutMapping / @DeleteMapping**

Bataate hain kis URL pe kaunsa kaam hona chahiye.

---

## ✉️ 6. **@RequestBody**

🔹 Jab tum **request ke body me JSON** bhejte ho (like student details), use isse receive karte hain.

🧒 *Jaise mummy ko chitti do: "Aaj chocolate chahiye".*

---

## 🔢 7. **@PathVariable**

🔹 URL ke andar se koi value nikalna.

Example: `/student/5` → 5 is path variable.

🧒 *Jaise roll number 5 ka student chahiye.*

---

## ❓ 8. **@RequestParam**

🔹 URL ke `?` ke baad ka data fetch karna.

Example: `/search?name=amit` → name is param

🧒 *Jaise Google pe search box me kuch likhna.*

---

## 🛠️ 9. **GET, POST, PUT, DELETE APIs**

| Method | Purpose                |
| ------ | ---------------------- |
| GET    | Data fetch karna       |
| POST   | Naya data create karna |
| PUT    | Data update karna      |
| DELETE | Data delete karna      |

🧒 *Jaise:
GET = "Show me toys"
POST = "Add new toy"
PUT = "Change toy color"
DELETE = "Throw toy"*

---

## 🌍 10. **Build Web Applications**

Spring Boot sirf APIs nahi, **web pages** bhi bana sakta hai (Thymeleaf, JSP, etc.)

🧒 *Jaise ek website jahan tum form bharte ho, list dekhte ho, data add karte ho.*

---

## 🔚 Final One-Line Summary:

| Concept         | Use                          |
| --------------- | ---------------------------- |
| Build Systems   | Dependencies & project setup |
| Code Structure  | App organization             |
| Runner          | App start pe kaam            |
| Logger          | Debug info                   |
| REST API        | Web communication            |
| @RestController | REST handler class           |
| @RequestBody    | JSON data lena               |
| @PathVariable   | URL se data lena             |
| @RequestParam   | URL ke query se data         |
| GET/POST...     | CRUD operations              |
| Web App         | Pages + APIs dono possible   |

---


