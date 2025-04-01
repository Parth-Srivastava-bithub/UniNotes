

### 1. **What is a Python Set?**
- **Definition**: Unordered, mutable collection of **unique**, hashable elements (like Java’s `HashSet`).
- **Syntax**: `my_set = {1, 2, 3}` or `my_set = set([1, 2, 3])`.
- **Key Features**:
  - No duplicates (auto-removed).
  - Unordered (no index-based access).
  - Supports mathematical set operations (union, intersection, etc.).

---

### 2. **Java vs Python Set Comparison**
| **Feature**             | **Java** (`HashSet`)                          | **Python** (`set`)                            |
|--------------------------|-----------------------------------------------|-----------------------------------------------|
| **Declaration**          | `Set<Integer> set = new HashSet<>();`         | `my_set = {1, 2, 3}` or `set()`              |
| **Add Element**          | `set.add(4);`                                 | `my_set.add(4)`                              |
| **Remove Element**       | `set.remove(4);`                              | `my_set.remove(4)` or `my_set.discard(4)`    |
| **Check Existence**      | `set.contains(4);`                            | `4 in my_set`                                |
| **Union**                | `set1.addAll(set2);`                          | `set1.union(set2)` or `set1 \| set2`         |
| **Intersection**         | `set1.retainAll(set2);`                       | `set1.intersection(set2)` or `set1 & set2`   |
| **Difference**           | `set1.removeAll(set2);`                       | `set1.difference(set2)` or `set1 - set2`     |
| **Ordered Version**      | `LinkedHashSet` (insertion order)             | No built-in ordered set (use `list` + logic) |
| **Sorted Version**       | `TreeSet` (sorted order)                      | No built-in sorted set (use `sorted(my_set)`) |

---

### 3. **Key Python-Specific Features**
- **Set Comprehensions**: `{x for x in iterable}` (like list/dict comprehensions).
- **Immutable Elements**: You can’t have a set of lists/dicts (elements must be hashable).
- **Mutable Operations**:
  ```python
  my_set.add(5)        # Add element
  my_set.remove(5)     # Raises KeyError if missing
  my_set.discard(5)    # No error if missing
  my_set.pop()         # Remove arbitrary element
  ```

---

### 4. **Common DSA Problems Using Sets**
Python sets are often used to solve problems involving **uniqueness**, **membership checks**, or **set operations**:
1. **Remove duplicates** from a list: `list(set(my_list))` (order not preserved).
2. **Check if two arrays have common elements**: `bool(set1 & set2)`.
3. **Find unique elements** in two sets (symmetric difference): `set1 ^ set2`.
4. **Check subset/superset**: `set1.issubset(set2)` or `set1 <= set2`.
5. **Count distinct elements** in a sliding window (common in strings/arrays).

---

### 5. **Example Code Snippets**
#### a. Basic Operations
```python
A = {1, 2, 3}
B = {3, 4, 5}

print(A | B)  # Union: {1, 2, 3, 4, 5}
print(A & B)  # Intersection: {3}
print(A - B)  # Difference: {1, 2}
```

#### b. Check for Duplicates
```python
def has_duplicates(arr):
    return len(arr) != len(set(arr))
```

#### c. Two-Sum Using a Set (O(n) time)
```python
def two_sum(nums, target):
    seen = set()
    for num in nums:
        if (target - num) in seen:
            return True
        seen.add(num)
    return False
```

---

### 6. **Important Notes for DSA**
- **Membership Check**: `x in set` is **O(1)** in Python (like Java’s `HashSet`).
- **No Order**: Use `sorted(my_set)` to sort, or `list(my_set)` to convert to a list.
- **FrozenSet**: Immutable version of a set (`frozenset`), useful as a dictionary key.

---

### 7. **Java to Python Cheat Sheet**
| **Java Code**                  | **Python Equivalent**          |
|--------------------------------|--------------------------------|
| `set.add(x)`                   | `my_set.add(x)`               |
| `set.contains(x)`              | `x in my_set`                 |
| `set1.addAll(set2)`            | `set1.update(set2)`           |
| `set1.retainAll(set2)`         | `set1.intersection_update(set2)` |
| `set.remove(x)`                | `my_set.remove(x)`            |
| `new HashSet<>(Arrays.asList(1,2,3))` | `{1, 2, 3}`          |

---
