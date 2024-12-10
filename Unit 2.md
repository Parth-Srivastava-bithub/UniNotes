# Unit 2 Solutions

## Heap

![alt text](image.png)
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


![alt text](image-1.png)

---

### Min Heap and Max Heap


#### Min heap

![Min Heap Image](image-2.png)

A min heap is a complete binary tree in which each node is smaller than its children, used for efficient sorting and priority queuing.

#### Max heap

![Max Heap Image](image-3.png)

A max heap is a complete binary tree in which each node is greater than its children, used for efficient sorting and priority queuing.


![Both Types](image-4.png)

#### Difference between Min Heap and Max Heap

| Criteria | Min Heap | Max Heap |
| --- | --- | --- |
| Root Node | Smallest Element | Largest Element |
| Leaf Nodes | Larger than Parent | Smaller than Parent |
| Priority | Smallest elements have highest priority | Largest elements have highest priority |
| Application | Extract Minimum | Extract Maximum |
---

## Max Heapify Algorithm

![Process of Max Heapify](image-5.png)

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

![Algo Pic](image-6.png)
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

![Algo Pic](image-7.png)

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

![alt text](image-9.png)

### Step 2: Build a Max Heap

![alt text](image-10.png)

![alt text](image-11.png)

![alt text](image-12.png)

![alt text](image-13.png)

![alt text](image-14.png)

![alt text](image-15.png)

![alt text](image-16.png)

### Step 3: Sort the array by placing largest element at end of unsorted array.

![alt text](image-17.png)

![alt text](image-18.png)

![alt text](image-19.png)

![alt text](image-20.png)

![alt text](image-21.png)

![alt text](image-22.png)

---
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
![alt text](image-24.png)

## Priority Queue

Priority Queue is a queue data structure where the element with the highest priority is served first. It is implemented using a heap data structure.

Example with metaphors: 
- Suppose you have a queue of emails that need to be sent. The email with the highest priority (such as urgent or important emails) should be sent first.
- Suppose you have a queue of tasks that need to be completed. The task with the highest priority (such as tasks that need to be done as soon as possible) should be completed first.
- Suppose you have a queue of payments that need to be processed. The payment with the highest priority (such as payments that need to be processed as soon as possible) should be processed first.

In summary, priority queues are useful for scheduling tasks or events based on their priority, and they can be implemented using a heap data structure.

![alt text](image-23.png)

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

![alt text](image-26.png)
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

![alt text](image-29.png)

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

![alt text](image-30.png)

---
