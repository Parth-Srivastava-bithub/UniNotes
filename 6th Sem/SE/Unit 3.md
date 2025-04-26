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


### 🔁 **Cohesion vs Coupling**

#### ✅ **Cohesion** (Internal bonding within a module)
- **High Cohesion** = Module does one task well (e.g., `AuthenticationModule` just for login/auth).
- **Types**: 
  - *Functional* (best) – all elements contribute to a single task.
  - *Sequential*, *Communicational*, *Procedural*, etc.
- **Why it’s good**: Easier to maintain, test, and reuse.

#### ❌ **Coupling** (How tightly modules depend on each other)
- **Low Coupling** = Modules interact via clean interfaces, not tightly linked.
- **Types**: 
  - *Data* (good) – only data passed.
  - *Control*, *Common*, *Content* (bad).
- **Why it’s bad**: Tight coupling makes changes risky, hard to scale.

🧠 **Goal**: High cohesion, low coupling = Clean, scalable software.

---

### 🏗️ **Design Strategies**

#### 🔝 **Top-Down Design**
- **Start** with overall system -> break into subsystems.
- **Example**: Design full app structure before writing a single function.

**Advantages**:
- Easier to manage big systems.
- Better understanding of final goal.

**Disadvantages**:
- Delayed coding.
- Requires detailed planning first.

#### 🔽 **Bottom-Up Design**
- **Start** with small, reusable modules -> integrate into bigger system.
- **Example**: First make a login module, then design the full auth system.

**Advantages**:
- Modules reusable across systems.
- Early development possible.

**Disadvantages**:
- May lack overall structure in early stages.
- Integration issues if not planned well.

---

### 📏 **Measurements in SE**
- Help quantify software attributes (size, effort, complexity, etc.)

Common ones:
- **LOC (Lines of Code)** – Code size.
- **Function Points** – Features provided.
- **Cyclomatic Complexity** – Decision points in code.

📌 Used for cost estimation, productivity, maintenance, etc.

---

### 📊 **Metrics in SE**
- Measurable indicators used to evaluate and improve software.

**Types**:
- **Product metrics**: Code quality (bugs, size, performance).
- **Process metrics**: Dev speed, efficiency.
- **Project metrics**: Budget, effort, timelines.

**Examples**:
- Defect Density = Bugs / KLOC.
- Code Coverage = % of code tested.
- MTTR = Mean Time To Repair.

🔧 Helps identify bottlenecks and improve software quality.

---

### 🧠 **Four Management Functions in SE**

1. **Planning**  
   - Define scope, goals, deadlines.  
   - Tools: Gantt charts, Agile sprint planning.

2. **Organizing**  
   - Assign roles, resources, tools.  
   - Example: Who handles frontend, backend, testing?

3. **Controlling**  
   - Track progress, compare with plan.  
   - Techniques: Code reviews, status meetings.

4. **Improving**  
   - Analyze results, apply lessons learned.  
   - Use feedback to enhance processes & team performance.

---


### 🧬 **Characteristics of Good Software Metrics**

1. **Qualitative**
   - Metrics should help evaluate *qualities* like reliability, maintainability, reusability, etc., not just quantity.
   - For example: “Customer satisfaction score” is more qualitative than just counting lines of code.

2. **Understandable**
   - Everyone from devs to PMs should easily get what the metric means.
   - A metric like *Cyclomatic Complexity = 15* should clearly signal: “This function is too complex, maybe refactor.”

3. **Applicable**
   - A good metric must fit the context.  
   - Example: *Test coverage* is great during testing but useless during planning phase.

4. **Respectable**
   - Should be industry-trusted and validated by research or practice.
   - Like Function Point Analysis (FPA), used globally for estimating project size.

5. **Economical**
   - Must not take huge effort or cost to calculate.
   - Example: If calculating a metric needs 3 devs working full-time, it’s not worth it.

6. **Language Independent**
   - Metric should work across tech stacks.  
   - Example: *Defect density* (bugs/KLOC) is valid whether code is in Java, Python, or C++.

---

### 🔄 **3 Types of Software Metrics**

#### 1. **Product Metrics**
   - Describe the quality of the product itself (the actual software).
   - 📌 **Examples**:
     - LOC (Lines of Code)
     - Cyclomatic Complexity
     - Number of classes/functions
     - Defect density (bugs per 1000 LOC)
     - Halstead Metrics

#### 2. **Process Metrics**
   - Focus on the **how** of software development — the process behind creating software.
   - 📌 **Examples**:
     - Time taken per task or feature
     - Bug fix rate
     - Review feedback cycle
     - Number of builds per day (CI/CD)

#### 3. **Project Metrics**
   - Deal with the overall project management side — timelines, resources, team.
   - 📌 **Examples**:
     - Effort estimation (hours/days)
     - Schedule variance (planned vs actual dates)
     - Cost overrun
     - Resource utilization

---

### ✅ **Advantages of Software Metrics**

1. **Improves Planning** – Helps forecast project timelines and resources with data.
2. **Better Decision Making** – Identify bottlenecks, refactor need, or testing gaps.
3. **Track Progress & Quality** – Metrics show whether the codebase or team is improving.
4. **Team Accountability** – Makes it easier to identify if something or someone is lagging behind.
5. **Helps with Process Improvement** – Over time, helps build faster and better systems.

---

### ❌ **Disadvantages of Software Metrics**

1. **Wrong Focus = Wrong Decisions**
   - Focusing only on LOC may reward bloated code instead of clean code.

2. **Misinterpretation**
   - If management doesn’t understand metrics, they may misuse them.
   - E.g., “Code coverage = 90% = perfect software” is a **myth**.

3. **Demotivation**
   - If used punitively, metrics can pressure devs and reduce creativity.

4. **Overhead**
   - Some metrics require tools, manual entry, and effort to maintain (especially in small teams).

5. **False Sense of Control**
   - Metrics might show green status while bugs are still lurking in user behavior or corner cases.

---



## 🧠 **1. Halstead’s Software Science**

### 📜 **Statement (What it is)**
Halstead proposed a way to measure software complexity based on the **number of operators and operands** in a program, not just lines of code.  
The idea: More mental effort = more complex code = higher risk = harder to maintain.

---

### 🧮 **Basic Measures Used**
He defines 4 **primitive quantities** from a codebase:

1. `n₁` = Number of **distinct operators**  
2. `n₂` = Number of **distinct operands**  
3. `N₁` = **Total occurrences** of operators  
4. `N₂` = **Total occurrences** of operands

---

### 📊 **Formulas (Derived Measures)**

From the basic ones, we compute:

- **Program Vocabulary**:  
  `n = n₁ + n₂`

- **Program Length**:  
  `N = N₁ + N₂`

- **Calculated Length (Estimated size)**:  
  `N̂ = n₁ * log₂(n₁) + n₂ * log₂(n₂)`

- **Volume (V)** – Actual size of implementation:  
  `V = N * log₂(n)`

- **Difficulty (D)** – How hard it is to write/understand:  
  `D = (n₁ / 2) * (N₂ / n₂)`

- **Effort (E)** – Mental effort to code:  
  `E = D * V`

- **Time Required to Program (T)**:  
  `T = E / 18` (seconds) – Based on psychologist estimate of human processing rate

- **Estimated Bugs (B)**:  
  `B = V / 3000`

---

### ✅ **Advantages**
- Language-independent (pure math on tokens)  
- Predicts effort, errors, time  
- Helps in maintenance planning  
- Great for embedded, mission-critical systems

---

### ❌ **Disadvantages**
- Assumes linear relationship between tokens and difficulty  
- Doesn’t capture code quality or structure  
- Hard to calculate manually for large programs  
- Ignores comments, logic flow, and readability

---

## 📏 **2. Function Point Based Measures**

### 📌 **What is it?**
Function Points measure the functionality delivered to the user — independent of programming language, size of code, or tools used.  
Focus is on *what the software does*, not how.

---

### 📚 **Main Components (Countable Elements)**
1. **External Inputs (EI)** – User input into the system  
2. **External Outputs (EO)** – Output sent to the user  
3. **External Inquiries (EQ)** – Requests needing input and output  
4. **Internal Logical Files (ILF)** – Internal DB/files used  
5. **External Interface Files (EIF)** – Shared files from other systems

Each component is given a weight (Low/Avg/High), and we sum all for **Unadjusted Function Points (UFP)**.

---

### ➕ **Advantages**
- **Language-independent** and usable in early design phase  
- **Focuses on user perspective** — more meaningful to clients  
- Good for **estimating project effort and cost**  
- Great for **maintenance and enhancement estimation**

---

### ➖ **Disadvantages**
- Requires **experience & judgment** to estimate weightings  
- Not suitable for **purely algorithmic programs** (like compilers, ML models)  
- Can be **subjective** if not standardized properly  
- Time-consuming compared to LOC

---

## 📐 **3. Measurement Parameters (Examples)**

| Parameter | Example |
|----------|--------|
| LOC      | 2,000 lines of code |
| Time     | 3 developer-months |
| Defects  | 8 bugs per KLOC |
| Coverage | 85% unit test coverage |
| Complexity | Cyclomatic Complexity = 12 |
| Function Points | 120 FP (high functionality) |

---

## 🔀 **4. Cyclomatic Complexity**

### 🧩 **Need**
- Measures the **decision complexity** of code — how many **independent paths** exist.
- Higher complexity = harder to test, understand, and maintain.

---

### 🎯 **Objective**
- Find the **minimum number of test cases** needed to test all logic paths.
- Helps reduce risk of untested edge cases.
- Shows if a function/module is becoming too complex.

---

### ⚙️ **Process (Steps to Calculate)**

Let’s say we have a control flow graph (CFG):

1. **Identify nodes and edges** (nodes = code blocks, edges = flow paths)
2. Use the formula:  
   `CC = E - N + 2P`  
   Where:  
   - `E` = number of edges  
   - `N` = number of nodes  
   - `P` = number of connected components (usually 1)

OR (simpler):

If you just count the number of **decision points** (if, while, for, case):  
`CC = D + 1`

---

### 📋 **Example**

```cpp
int max(int a, int b, int c) {
   if (a > b) {
      if (a > c)
         return a;
      else
         return c;
   } else {
      if (b > c)
         return b;
      else
         return c;
   }
}
```

- There are **3 `if` statements** → CC = 3 + 1 = **4**
- Meaning: 4 independent paths → 4 test cases needed to test all logic

---

### ✅ **Advantages**
- Simple and quick
- Directly maps to test case design
- Helps identify overly complex code (CC > 10? REFACTOR IT!)

---

### ❌ **Disadvantages**
- Doesn’t measure actual code quality
- Only considers control flow, not data flow
- Not very useful for declarative or functional programming

---

