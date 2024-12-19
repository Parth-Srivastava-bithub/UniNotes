# Unit 2 Solutions

## Heap

![image](https://github.com/user-attachments/assets/704bdd8f-0c84-45ff-9398-698b24b46b0c)

### Complete Binary Tree vs Almost Complete Binary Tree
* A complete binary tree has all levels fully filled except possibly the last, with nodes as far left as possible.
* An almost complete binary tree allows each node to have 0 or 2 children, with the last level potentially having nodes with 0 or 1 child.
* The last level of a complete binary tree is fully filled, unlike an almost complete binary tree where it may be partially filled.
* Nodes in a complete binary tree are aligned to the left, whereas in an almost complete binary tree, they might not be.
* A complete binary tree is a specific type of almost complete binary tree.

### Difference between Complete Binary Tree and Almost Complete Binary Tree

| Criteria | Complete Binary Tree | Almost Complete Binary Tree |
| --- | --- | --- |
| All levels fully filled | Yes | No |
| Last level fully filled | Yes | No |
| Left aligned | Yes | No |
| Nodes with 0 or 2 children | Yes | Yes |
| Nodes with 0 or 1 children | No | Yes |
---

### Heap Tree to Array Conversion


```bash
Index = i
Left_Child = 2*i
Right_Child = 2*i + 2
Parent = i//2
```

```bash
Formula to tree
    i
   / \
 2*i 2*i+1
```


![image](https://github.com/user-attachments/assets/0ef21b0a-c9f2-45b5-b9e6-c133913c7132)


---

### Min Heap and Max Heap


#### Min heap

![image](https://github.com/user-attachments/assets/269ab4c2-2f47-41ba-91e7-fe1f36e5eaf5)


A min heap is a complete binary tree in which each node is smaller than its children, used for efficient sorting and priority queuing.

#### Max heap

![image](https://github.com/user-attachments/assets/39ed68cb-4012-4211-aaa9-b587c63ac047)



A max heap is a complete binary tree in which each node is greater than its children, used for efficient sorting and priority queuing.


![image](https://github.com/user-attachments/assets/155b6d18-b930-4b20-8dbb-5776ae106ce1)


#### Difference between Min Heap and Max Heap

| Criteria | Min Heap | Max Heap |
| --- | --- | --- |
| Root Node | Smallest Element | Largest Element |
| Leaf Nodes | Larger than Parent | Smaller than Parent |
| Priority | Smallest elements have highest priority | Largest elements have highest priority |
| Application | Extract Minimum | Extract Maximum |
---

## Max Heapify Algorithm

![image](https://github.com/user-attachments/assets/1957f2e0-7202-4c25-9f90-9a93667c472a)


### Algorithm

*List of Algorithms*

1. Max Heapify
2. Heap Extract Max
3. Heap Increase Key
4. Heap Delete
5. Heap Insert
---
**For Max Heapify**

```python
MaxHeapify(A, i)
    n = len(A)
    l = 2*i + 1
    r = 2*i + 2
    largest = i
    if l < n and A[l] > A[i]:
        largest = l
    if r < n and A[r] > A[largest]:
        largest = r
    if largest != i:
        A[i], A[largest] = A[largest], A[i]
        MaxHeapify(A, largest)
``` 

***In a pic form for personal use***

![image](https://github.com/user-attachments/assets/695d0767-d9d6-43e1-93b0-d541e692c96d)
---
**For heap extract maximum**

```python
heap_extract_max(A)
    if len(A) == 0:
        return None
    if len(A) == 1:
        return A.pop()
    max = A[0]
    A[0] = A.pop()
    MaxHeapify(A, 0)
    return max
```
---

**For heap increase key**

```python
heap_increase_key(A, i, key)
    A[i] = key
    while i > 0 and A[i] > A[(i-1)//2]:
        A[i], A[(i-1)//2] = A[(i-1)//2], A[i]
        i = (i-1)//2
```

---

**For heap delete**

```python
heap_delete(A, i)
    heap_increase_key(A, i, float('-inf'))
    return heap_extract_max(A)
```
---

**For heap insert**

```python
heap_insert(A, key)
    A.append(float('-inf'))
    heap_increase_key(A, len(A)-1, key)
```
---
## Min Heapify Algorithm

```bash
Just vice versa of Max Heapify
```

#### Min Heapify Algorithm
*List of Algorithms*

1. Min Heapify
2. Heap Extract Min
3. Heap Increase Key
4. Heap Delete
5. Heap Insert
---

```python
MinHeapify(A, i)
    n = len(A)
    l = 2*i + 1
    r = 2*i + 2
    smallest = i
    if l < n and A[l] < A[i]:
        smallest = l
    if r < n and A[r] < A[smallest]:
        smallest = r
    if smallest != i:
        A[i], A[smallest] = A[smallest], A[i]
        MinHeapify(A, smallest)
``` 
***In a pic form for personal use***

![image](https://github.com/user-attachments/assets/4757a59c-a1ef-429f-834a-c6f1dabee534)


---

**For heap extract minimum**

```python
heap_extract_min(A)
    if len(A) == 0:
        return None
    if len(A) == 1:
        return A.pop()
    min = A[0]
    A[0] = A.pop()
    MinHeapify(A, 0)
    return min
```
---

**For heap increase key**

```python
heap_increase_key(A, i, key)
    A[i] = key
    while i > 0 and A[i] < A[(i-1)//2]:
        A[i], A[(i-1)//2] = A[(i-1)//2], A[i]
        i = (i-1)//2
``` 

---

**For heap delete** 

```python
heap_delete(A, i)
    heap_increase_key(A, i, float('inf'))
    return heap_extract_min(A)
```
--- 

**For heap insert**

```python
heap_insert(A, key)
    A.append(float('inf'))
    heap_increase_key(A, len(A)-1, key)
```
---

## HeapSort Algorithm

### Step 1: Treat the Array as a Complete Binary Tree

We first need to visualize the array as a complete binary tree. For an array of size n, the root is at index 0, the left child of an element at index `i` is at `2i + 1`, and the right child is at `2i + 2`.

![image](https://github.com/user-attachments/assets/d90baaa0-d562-4597-b273-6d82247ba66a)


### Step 2: Build a Max Heap

![image](https://github.com/user-attachments/assets/5e86f7f5-7768-4c2f-afe0-e3ef703af76e)


![image](https://github.com/user-attachments/assets/2f2c7147-eb7a-4192-866a-7d4d8b3137ca)


![image](https://github.com/user-attachments/assets/7199df50-97c7-49b6-be15-acfafd0b6f31)


![image](https://github.com/user-attachments/assets/6f3a9a4d-b63e-4981-9fde-e5e5c0907f93)


![image](https://github.com/user-attachments/assets/984a261d-78b2-4e27-be5c-fcc70c7c8946)


![image](https://github.com/user-attachments/assets/6aaf64d2-338a-4fed-b169-bece5e28a7e8)


![image](https://github.com/user-attachments/assets/e5fb22bb-e476-46f9-a469-c879943be64c)


### Step 3: Sort the array by placing largest element at end of unsorted array.

![image](https://github.com/user-attachments/assets/70fd1ea6-0827-4e97-921c-03d22151ace2)

![image](https://github.com/user-attachments/assets/1addac3f-d35b-47df-8528-c524cee6775f)

![image](https://github.com/user-attachments/assets/379fbe91-e12a-4beb-871a-12bcf6de2439)


![image](https://github.com/user-attachments/assets/fcb90ba9-7571-40bd-8c09-8e1f078cc6c4)

![image](https://github.com/user-attachments/assets/0fd15db5-d95b-4d2b-9591-cc4e5c17fed9)


![image](https://github.com/user-attachments/assets/93389e8b-a3a0-47df-8c7e-eb04e8e05f0e)

### Algorithm

```bash

HeapSort(A){
    BuildMaxHeap(A)
    for i in range(len(A)-1, 0, -1):
        A[0], A[i] = A[i], A[0]
        A.heap_size -= 1
        MaxHeapify(A, i)
}
# Already Covered Before
MaxHeapify(A, i){
    l = 2*i + 1
    r = 2*i + 2
    largest = i
    if l < len(A) and A[l] > A[i]:
        largest = l
    if r < len(A) and A[r] > A[largest]:
        largest = r
    if largest != i:
        A[i], A[largest] = A[largest], A[i]
        MaxHeapify(A, largest)  
}

```


#### Process in simple words

1. First Build a Max Heap
2. Remove the largest element from the heap and place it at the end of the array.
3. Replace smallest element at the Root Node
4. Now do the step 1 again
5. Repeat step 1 to n-1 times

Each time u do step 2, the largest element will be placed at the end of the array.
Continue this process until the array is sorted.

*Time and Space Complexity In Table Form*

| Time Complexity | Space Complexity |
| --- | --- |
| O(nlogn) | O(1) |

---
![image](https://github.com/user-attachments/assets/e60a9e44-68b7-4594-9503-7aa9b68007f0)


## Priority Queue

Priority Queue is a queue data structure where the element with the highest priority is served first. It is implemented using a heap data structure.

Example with metaphors: 
- Suppose you have a queue of emails that need to be sent. The email with the highest priority (such as urgent or important emails) should be sent first.
- Suppose you have a queue of tasks that need to be completed. The task with the highest priority (such as tasks that need to be done as soon as possible) should be completed first.
- Suppose you have a queue of payments that need to be processed. The payment with the highest priority (such as payments that need to be processed as soon as possible) should be processed first.

In summary, priority queues are useful for scheduling tasks or events based on their priority, and they can be implemented using a heap data structure.

![image](https://github.com/user-attachments/assets/12fb1211-7357-4cc6-a443-a7c50cc62d76)

### Working on these Topics

---

## Binomial Tree And Binomial Heap

### What is a Binomial Heap?

Binomial heap is collection of binomial trees that satisfy the following properties:

```bash
What is binomial tree?
Binomial tree is a tree in which the degree of each node is equal to the number of children of the node.
- The binomial tree is an ordered tree defined recursively as follows:

1. A binomial tree of order 0 is a single node.
2. The binomial tree consist of two binomial trees that are linked together by a single node.

# Smallest Binomial Tree

- A binomial tree of order 0 is a single node.


    Connection
       / \
      /   \
    Node  Node
   (k - 1) (k - 1)


```
---
### Example of binomial tree

![image](https://github.com/user-attachments/assets/1679d945-8adb-41ca-82fa-9e2f2e4a387d)


```
B1 = B0 + B0
B2 = B1 + B1
B3 = B2 + B2
B4 = B3 + B3
B(N) = B(N-1) + B(N-1)
```

---

### Properties of Binomial Tree

1. There are 2^k binomial nodes
2. Height of a binomial tree is k
3. Their are exactly K(C[i]) nodes at depth i for i = 0 to k
4. The root has degree k, which is greater than that of any other node 
5. If i the children of the root are numbered from left to right by k - 1, k - 2, ..., 0. Child i is the root of subtree B(i)
---
**k(C[i]) is just**

$$
C(k, i) = \binom{k}{i} = \frac{k!}{i!(k-i)!}
$$
---

### Binomial Heap

![image](https://github.com/user-attachments/assets/1f416a10-1ca2-4a07-9183-474929dd8df8)


Binomial heap is a collection of binomial trees that satisfy the following properties:

1. The degree of each node is equal to the number of children of the node.
2. The binomial heap is a min-heap or max-heap.
3. The binomial heap is a self-balancing binary tree.

**No same degree binomial tree can be present in a binomial heap** 


A n-node binomial heap consist of atomost `([log(base 2) n] + 1)` binomial trees.

---
### Mathmatical Properties of Binomial Heap

1. n = B(i) + B(j) + B(k) <br>
   n = 2^i + 2^j + 2^k <br>


```
For an eg:
n = 15 <br>
n = bin(15) = 1111 <br>
1____1____1____1<br>
b3 + b3 + b2 + b1 <br>
8 + 4 + 2 + 1 <br>
Which is 15
```
---

### Stucture of Binomial Heap

![image](https://github.com/user-attachments/assets/080abfc8-98e8-45c5-ba6f-51d756399646)


---

### Properties of a Binomial Heap:
1. **Combination of Binomial Trees**:  
   A binomial heap is made up of **binomial trees**, each following the structure of a binomial tree \(B_k\) (where \(B_k\) has \(2^k\) nodes and height \(k\)).

2. **Degrees in Increasing Order**:  
   The binomial trees are arranged in **increasing order of degree** (left to right).

   **ASCII Art Example**:  
   ```
   B0 → B1 → B3
   (1 node)  (3 nodes)  (8 nodes)
   ```

3. **At Most One Tree Per Degree**:  
   In a valid binomial heap, there is at most **one tree for each degree**.

4. **Heap Property**:  
   - Each binomial tree follows the **min-heap property**: The key of the parent node is smaller than or equal to its child nodes.

5. **Binary Representation Connection**:  
   The structure of a binomial heap corresponds to the binary representation of its size \(n\).  
   - Example: If \(n = 13\) (binary: 1101), the heap will contain trees \(B0, B2, B3\).


## Binomial Heap Union Operation
![image](https://github.com/user-attachments/assets/327e3d9c-6f00-4d4b-a09b-6e25851cd87e)

This explanation relates to how we merge trees of the same degree during the **union operation** in a binomial heap:

---

### **Let’s break it down:**

1. **Terms**:  
   - \(x\): Current tree we are working with.
   - \(n - x\): Next tree of the same degree in the sequence.
   - \(s - n - x\): The tree after these two.

2. **Rule for Merging:**
   - If the first two trees (\(x\) and \(n - x\)) have the **same degree** but the third one (\(s - n - x\)) has a different degree:
     - **Merge the first two** trees. 
     - Add the smaller root of \(x\) and \(n - x\) as the parent of the larger root.

   - If all three trees have the **same degree**, we cannot merge just the first two. In this case:
     - **Carry over the merge** by promoting the degree of all three trees (increment their position).

---

### **How this works during merging:**
- Start by comparing consecutive trees in the merged heap list:
  - If the **first two degrees match**:
    - Merge them.
    - Check the degree of the resulting merged tree with the next tree.
  - If **three consecutive trees have the same degree**, skip merging for now and continue incrementing degrees until they can be resolved.

---

### **Example in Action**:
#### Case 1: First two degrees match, third is different:
Trees: \(B2, B2, B3\)  
- Merge the first two \(B2\) trees into a \(B3\).  
- The resulting heap has \(B3, B3\).

#### Case 2: All three have the same degree:
Trees: \(B2, B2, B2\)  
- Merge the first two into a \(B3\).  
- Now, \(B3, B2\) still exists, so increment the position to maintain balance.

---

### **Why this works:**
This ensures:
- The heap maintains at most **one tree per degree**.
- Merging and balancing are efficient while preserving the **binomial heap properties**.


---

## Inserting a node into Binomial min heap

To insert a node into a binomial min heap:

1. **Create a new heap \( h' \)** with just the new node.
2. **Union** \( h \) and \( h' \): Merge the two heaps, linking trees of the same order and maintaining the min-heap property.
![image](https://github.com/user-attachments/assets/b36139a0-9f40-4281-9280-f94fa8130dd4)



### Visit this link for better understanding 
[Video Link for Better understanding](https://www.youtube.com/watchv=skBDWOxSDl8&list=PL1QH9gyQXfgs7foRxIbIH8wmJyDh5QzAm&index=67&pp=iAQB)



## Extracting the Minimum from Binomial Heap
---

### Steps to Extract the Minimum from a Binomial Heap:

1. **Find the Minimum Root**:  
   Look at the roots of all binomial trees in the heap. Since the minimum of each tree is at its root, the smallest root is the global minimum.

2. **Remove the Minimum Root**:  
   Remove the binomial tree with the smallest root from the heap. Break the tree into its smaller subtrees (if it’s \( B_k \), the subtrees will be \( B_{k-1}, B_{k-2}, ..., B_0 \)).

3. **Reinsert the Subtrees**:  
   Treat the remaining subtrees as a new binomial heap. Merge this heap with the rest of the original heap.

---

### Why Check Roots Only?  
- Each root is the smallest value in its respective binomial tree.  
- The global minimum is guaranteed to be one of the roots, so we don’t need to look deeper.

This image explains very well
![image](https://github.com/user-attachments/assets/7f7e085d-b929-490e-bdc0-e81d18bef8f9)

**Get Min -> break the tree -> reverse join -> get two b heaps -> merge them**


## Deletion of element in Binomial Heap

Going over **deletion in a binomial min-heap** step by step. The key idea is that when deleting a node, we maintain the **min-heap property** by replacing it with the minimum possible value.

---

### Steps for Deletion:

#### 1. **Decrease the Key of the Node to \(-\infty\)**:
   - First, replace the value of the node to be deleted with \(-\infty\) (a value smaller than any other in the heap).
   - Why? This ensures the node "bubbles up" to the root of its binomial tree because it’s now the smallest element.

#### 2. **Extract the Minimum**:
   - Since the node has been replaced with \(-\infty\), it will now be the **minimum element in the heap**.
   - Perform the **Extract Min** operation to remove this node (already explained earlier):
     - Break the tree containing the minimum node into smaller subtrees.
     - Merge these subtrees back into the heap.

---

### Why Replace with Minimum?  
The **min-heap property** requires that each parent node is smaller than its children. By replacing the node with \(-\infty\), we ensure:
- It becomes the minimum and moves to the root of its tree.
- Extracting it is straightforward, maintaining the heap structure.

This approach avoids direct deletion, which would otherwise require complex adjustments to preserve the min-heap structure.

### Cycle to remember
**Replace with \(-\infty\) → Bubble up to root → Remove the root → Break the tree → Reverse subtrees → Merge back into heap.**

## Comparison
Here’s a comparison table for **Binary Heap**, **Binomial Heap**, and **Fibonacci Heap** in terms of their properties and time complexities:

| **Operation**           | **Binary Heap**      | **Binomial Heap**          | **Fibonacci Heap**        |
|--------------------------|----------------------|----------------------------|---------------------------|
| **Structure**           | Complete binary tree | Collection of binomial trees | Collection of trees (unordered) |
| **Insert**              | \( O(\log n) \)     | \( O(\log n) \)            | \( O(1) \) (amortized)   |
| **Find Minimum**        | \( O(1) \)          | \( O(\log n) \)            | \( O(1) \)               |
| **Extract Minimum**     | \( O(\log n) \)     | \( O(\log n) \)            | \( O(\log n) \) (amortized) |
| **Union (Merge)**       | \( O(n) \)          | \( O(\log n) \)            | \( O(1) \) (amortized)   |
| **Decrease Key**        | \( O(\log n) \)     | \( O(\log n) \)            | \( O(1) \) (amortized)   |
| **Delete**              | \( O(\log n) \)     | \( O(\log n) \)            | \( O(\log n) \) (amortized) |
| **Memory Usage**        | Moderate            | Moderate                   | High                     |

---

**Amortized analysis** is a way of averaging the time complexity of operations over a series, where expensive operations are offset by cheaper ones, resulting in a lower average cost per operation.

### Notes:
1. **Binary Heap**:
   - Simple to implement and efficient for most use cases.
   - Does not support efficient merging of heaps.

2. **Binomial Heap**:
   - Supports heap merging efficiently.
   - Slightly slower than binary heap for individual operations like insert and delete.

3. **Fibonacci Heap**:
   - Best for applications requiring frequent **decrease-key** and **union** operations (e.g., Dijkstra’s or Prim’s algorithm).
   - More complex to implement due to lazy consolidation and amortized analysis.
---

## Fibonacci Heap
![image](https://github.com/user-attachments/assets/dea9372b-59f1-4b4a-9eaa-ba92424dd739)

Notes Are Coming...
