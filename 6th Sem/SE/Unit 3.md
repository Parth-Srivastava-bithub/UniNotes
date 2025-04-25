### 🛠️ **Objective of Software Design (SD)**

---

### 1. **Correctness**
**👉 It works as intended.**
> 🧪 Like a calculator adding 2+2 and giving 4, not 5.

🔹 *Example*: If you design a login system, it should allow correct users in and reject wrong passwords. No bugs = correct.

---

### 2. **Completeness**
**👉 All required features are present.**
> 📦 Like ordering a pizza and getting crust, cheese, toppings—not just bread.

🔹 *Example*: If a to-do app allows adding tasks but not marking them done or deleting—it's incomplete.

---

### 3. **Efficiency**
**👉 Uses minimal resources (CPU, memory, time).**
> 🚀 Like using a shortcut to reach your home instead of a long route.

🔹 *Example*: A search function that returns results in 1 sec vs. 10 secs—faster one is efficient.

---

### 4. **Flexibility**
**👉 Easy to update or extend.**
> 🧱 Like LEGO—you can add or change parts without breaking the whole thing.

🔹 *Example*: If your e-commerce app lets you easily add a new payment method—that’s flexible design.

---

### 5. **Consistency**
**👉 Same behavior throughout the system.**
> 🎮 Like pressing “Start” always beginning the game, not sometimes opening settings.

🔹 *Example*: UI buttons having same style and all forms showing errors the same way—consistent.

---

### 6. **Maintainability**
**👉 Easy to fix, improve, or debug.**
> 🧰 Like a car with labeled parts—you can repair it easily.

🔹 *Example*: Code written with clear naming and comments is easier for others (or future you) to fix or upgrade.

---

### ASCII Flowchart (Simple SD Flow)

```
   +---------------------+
   |  Understand Problem |
   +----------+----------+
              |
              v
   +----------+----------+
   |  Identify Requirements |
   +----------+----------+
              |
              v
   +----------+----------+
   |   Design Architecture |
   +----------+----------+
              |
              v
   +----------+----------+
   |   Evaluate Objectives |
   +----------+----------+
              |
              v
   +----------+----------+
   |  Implement & Test   |
   +---------------------+
```

---

## 💎 What is GSD (Good Software Design)?

A **Good Software Design (GSD)** is a design that’s **clear, correct, efficient, and easy to modify**. It solves the problem **without confusion or mess**, even when the system grows big.

---

## 💡 Characteristics of GSD

1. **Correctness**  
   👉 Works exactly as intended. No logic errors.  
   🔹 *Ex: Login accepts correct users only.*

2. **Understandability**  
   👉 Easy to read and follow for any developer.  
   🔹 *Ex: Clear variable names, logical code flow.*

3. **Efficiency**  
   👉 Optimized use of memory, time, and CPU.  
   🔹 *Ex: No unnecessary loops, quick response time.*

4. **Maintainability**  
   👉 Easy to update, fix bugs, or scale.  
   🔹 *Ex: Clean modular code = faster debugging.*

---

## 🌀 Phases of Software Design

---

### 🔗 1. Interface Design  
> Defines how modules/systems **communicate** with each other or the user.

1. Defines **input/output** format clearly.  
2. UI/UX decisions if it's user-facing.  
3. Sets up **API endpoints or module contracts**.  
4. Reduces **dependency issues** between modules.  
5. Makes testing easier by isolating interfaces.

---

### 🏛️ 2. Architectural Design  
> High-level structure of system — like a building plan.

1. Decides **how many components** exist.  
2. Defines **interactions** between them.  
3. Selects architecture style (e.g., MVC, Microservices).  
4. Focuses on **scalability & security**.  
5. Acts as a **blueprint** for developers.

---

### 🔬 3. Detailed Design  
> Low-level view of each module or function.

1. Describes **class-level logic** & function details.  
2. Includes **algorithms** used inside modules.  
3. Covers **data structures** and flow.  
4. Adds **error handling** logic.  
5. Helps in actual coding directly (step-by-step design).

---

## 💡 **Software Design Principles**

---

### 1. **Problem Partitioning / Decomposition**  
👉 Break big problems into smaller ones.  
🔹 *Ex: Instead of designing whole e-commerce site at once, split into cart, payment, login, etc.*

---

### 2. **Abstraction**  
👉 Show only important details, hide complexity.  
🔹 *Ex: You use `.sort()` in Python without knowing internal algo—it’s abstracted.*

---

### 3. **Modularity**  
👉 Divide code into independent modules.  
🔹 *Ex: Login, payment, and search all in separate modules.*

---

### 4. **Top Down and Bottom Up Approach**

- **Top Down:** Start from overall system → break into parts.  
  🔹 *Like designing an entire website structure first, then writing small features.*

- **Bottom Up:** Start from small parts → connect them into a system.  
  🔹 *Write login, payment separately first, then connect them.*

---

## 🔗 **Modularization – 5 Points**

1. Divides system into **independent units**  
2. Each module has **specific responsibility**  
3. Easier to **understand and manage**  
4. Supports **team collaboration**  
5. Promotes **clean, organized codebase**

---

## ✅ **Benefits of Modularization**

- **Testing & Debugging**: Easy to test modules separately and fix bugs faster.  
- **Reusability**: One module can be reused in other projects.  
- **Extensibility**: Easy to add new features without touching other parts.

---

## 🚀 **Advantages**

1. Reduces complexity  
2. Boosts productivity (team can work parallel)  
3. Easier to maintain & scale  
4. Enhances code clarity  
5. Helps in faster development cycle

---

## 🏗️ **Design Structure Class – 5 Points**

1. **Shows system breakdown into modules**  
2. **Defines relationships** (which module controls which)  
3. **Visualizes hierarchy** of control  
4. **Helps in understanding flow of control/data**  
5. **Used in structure charts** during design phase

---

## 🔣 **Symbols in Structure Design**

| Symbol | Meaning |
|--------|---------|
| 🔲 **Module** | Basic unit (function/subsystem) |
| 🔺 **Control Module** | Top-level, controls sub-modules |
| ▭ **Sub Module** | Performs specific task under control module |
| 📚 **Library Module** | Predefined, reusable module |

---

### 🔄 **Other Symbols**

- **▶️ Conditional Call** – Dashed line with condition written  
- **🔁 Loop** – Arrowed loop or curved connector  
- **➡️ Data Flow** – Line with open arrow (label data passed)  
- **🔀 Control Flow** – Line with solid arrow (shows control passed)  
- **💾 Physical Storage** – Rectangle with one side curved (like a DB symbol)

---

## 📧 Structure Chart of Email Storage (ASCII)

```
            +----------------------+
            |   Email Application |
            +----------+-----------+
                       |
     +-----------------+-------------------+
     |                                     |
+----v----+                         +------v------+
| Compose |                         |  Inbox View |
+----+----+                         +------+------+
     |                                     |
+----v----+                         +------v------+
| Storage |<----------------------->|   Retrieve  |
+---------+                         +-------------+
```

## 🧱 **Structure Chart**

### 🌀 **Types**

1. **Transform Centered Structure**  
👉 Follows **input → processing → output** style.  
🔹 *Ex: Sensor data → analyze → display result*

2. **Transaction Centered Structure**  
👉 Based on **type of input (transaction)** deciding the path.  
🔹 *Ex: ATM → withdrawal OR balance check → different flow*

---

### ✅ **Benefits**

- Better **code organization**  
- Easy to **test and debug**  
- Clear **hierarchy & responsibility**  
- Improves **team collaboration**  
- Supports **top-down design**

---

## 📝 **Pseudocode Example (ATM)**

```
Start
  Get user input
  IF input = "balance" THEN
    Show balance
  ELSE IF input = "withdraw" THEN
    Ask amount
    Dispense cash
  ENDIF
End
```

---

## 🔁 **Flowchart (ATM)**

```
    +---------+
    |  Start  |
    +----+----+
         |
    +----v-----+
    | Get Input|
    +----+-----+
         |
+--------v--------+
| Balance OR Withdraw? |
+----+--------+----+
     |        |
+----v--+  +--v-----+
| Show  |  | Withdraw|
|Balance|  | Cash    |
+-------+  +--------+
     |
  +--v--+
  | End |
  +-----+
```

---

## 🧠 **LLD (Low-Level Design)**

### 🧩 **Types**

1. **Modularization**  
👉 Splitting system into smaller modules.

2. **Structure Chart**  
👉 Shows module relationships & hierarchy.

3. **Pseudocode**  
👉 Describes logic of modules in plain English/code-like steps.

---

## ⚡ **Coupling**

Coupling is how **dependent** one module is on another. **Less coupling** = **better design**. Here’s the breakdown:

---

### 🧩 **Types of Coupling**

1. **Uncoupled**  
   👉 No dependency. Modules don’t know about each other.  
   🔹 *Best* — Ideal for highly independent modules.

2. **Loosely Coupled**  
   👉 Some dependency, but not tight. Modules interact with minimal details.  
   🔹 *Good* — Modules are relatively independent but still communicate.

3. **Highly Coupled**  
   👉 Modules are strongly dependent on each other. Changes in one module affect the other.  
   🔹 *Worst* — Bad for maintenance and scalability.

---

### 🛠️ **Main Types of Coupling**

1. **Data Coupling**  
   👉 Modules share **only necessary data**.  
   🔹 *Best* — Minimal dependency, just passing data.

2. **Stamp Coupling**  
   👉 Passing a **complex data structure** (not just individual data).  
   🔹 *Moderate* — More than needed, but not terrible.

3. **Control Coupling**  
   👉 One module **controls** the flow of another (through flags, parameters).  
   🔹 *Bad* — Tight control flow can cause problems.

4. **External Coupling**  
   👉 Modules depend on **external systems** like databases, files.  
   🔹 *Moderate to Bad* — External dependencies can break systems easily.

5. **Common Coupling**  
   👉 Modules share **global data**.  
   🔹 *Worse* — Uncontrolled access to shared data can cause bugs.

6. **Content Coupling**  
   👉 One module **directly modifies** another’s internal content.  
   🔹 *Worst* — This is **tightly coupled** and can easily break the system.

---

## 🔥 **Best to Worst in Coupling**

1. **Best**: Data Coupling
2. **Moderate**: Stamp Coupling, External Coupling
3. **Worst**: Control Coupling, Common Coupling, Content Coupling

---

## 🌐 **Cohesion**

Cohesion is how **related** the functions within a module are. **High cohesion** = **better design**.

---

### 💡 **Types of Cohesion**

1. **Functional Cohesion**  
   👉 All parts of the module work together to achieve **one goal**.  
   🔹 *Best* — Everything in the module is highly related.

2. **Sequential Cohesion**  
   👉 Modules perform tasks in a **specific sequence**.  
   🔹 *Good* — Steps must happen in order.

3. **Communication Cohesion**  
   👉 Modules perform tasks that **operate on the same data**.  
   🔹 *Good* — Related operations but not necessarily in sequence.

4. **Procedural Cohesion**  
   👉 Tasks are related by **order of execution** but aren’t closely related.  
   🔹 *Moderate* — Functions are loosely related.

5. **Temporal Cohesion**  
   👉 Tasks happen at the **same time** but aren’t functionally related.  
   🔹 *Moderate* — Not ideal, but not horrible.

6. **Logical Cohesion**  
   👉 Different tasks in the module that are **logically related** (e.g., input validation).  
   🔹 *Bad* — Tasks grouped together because they share logic, but they aren’t directly related.

7. **Coincidental Cohesion**  
   👉 Tasks with **no relation** are grouped in the same module.  
   🔹 *Worst* — The worst form of cohesion. Modules do random unrelated tasks.

---

## 🚀 **Best to Worst in Cohesion**

1. **Best**: Functional Cohesion
2. **Good**: Sequential Cohesion, Communication Cohesion
3. **Moderate**: Procedural Cohesion, Temporal Cohesion
4. **Bad**: Logical Cohesion
5. **Worst**: Coincidental Cohesion

---

