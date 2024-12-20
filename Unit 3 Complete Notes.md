## Syllabus in one view
1. **Dynamic Programming**  
   - Knapsack Problem  
   - All-Pairs Shortest Paths  
     - Warshall's Algorithm  
     - Floyd's Algorithm  
   - Resource Allocation Problem  

2. **Backtracking**  
   - Travelling Salesman Problem  
   - Graph Coloring  
   - n-Queen Problem  
   - Hamiltonian Cycles  
   - Sum of Subsets  

3. **Branch and Bound**  
   - Travelling Salesman Problem  
   - Other Problem Examples  

## Divide And Conquer (Unit 3)

"Divide and conquer" is an algorithmic technique where a problem is broken down into smaller subproblems, solved independently, and then combined to form the solution.

Here's a simple ASCII visualization:

```
              Problem
                |
    -----------------------------
    |                           |
  Subproblem 1                Subproblem 2
    |                           |
    -------------           -------------
    |           |           |           |
 Subsub1     Subsub2     Subsub3     Subsub4
    |           |           |           |
   Solve       Solve       Solve       Solve
    |           |           |           |
    -------------------------------------
                |
             Combine
                |
             Final Solution
```       Final Solution
```

- **Divide**: Break the problem into smaller subproblems.
- **Conquer**: Solve each subproblem independently.
- **Combine**: Merge the solutions of subproblems to get the final answer.

A classic example is **Merge Sort**.

Here’s a more formal representation of the "Divide and Conquer" algorithm using pseudocode:

```
DAC(P):
  if (small(P))               # Base case: if the problem is small enough to solve directly
    s(P)                       # Solve the problem
  else:
    Divide P into P1, P2, ..., Pk   # Split the problem into smaller subproblems
    Apply DAC(P1), DAC(P2), ..., DAC(Pk)  # Recursively solve each subproblem
    Combine DAC(P1), DAC(P2), ..., DAC(Pk)  # Combine the solutions of the subproblems to form the final solution
```

In the pseudocode:

- **small(P)** checks if the problem is small enough to be directly solved.
- **s(P)** solves the problem when it's small.
- **Divide** breaks the problem into smaller subproblems.
- **DAC(P1), DAC(P2), ..., DAC(Pk)** recursively applies the Divide and Conquer algorithm to each subproblem.
- **Combine** merges the results of subproblems to form the final solution.


### Finding Maximum and Minimum element using Divide and Conquer


#### **Definition:**

The problem of finding the maximum and minimum element in an array can be efficiently solved using the Divide and Conquer approach. The array is recursively divided into smaller subarrays, and each subarray is solved for both the maximum and minimum elements. These results are then combined to get the overall maximum and minimum values.

The Divide and Conquer algorithm works as follows:

1. **Base case**: If the array has one element, that element is both the maximum and minimum.
2. **Divide**: Split the array into two halves.
3. **Conquer**: Recursively find the maximum and minimum of each half.
4. **Combine**: Compare the results from both halves and combine to get the overall maximum and minimum.

#### **ASCII Visualization:**

```
                       [ 4, 2, 9, 7, 5, 1, 8 ]
                                   |
                     -------------------------------
                     |                             |
            [ 4, 2, 9 ]                        [ 7, 5, 1, 8 ]
                |                                    |
          --------------                     -------------------
          |            |                     |                 |
      [ 4, 2 ]      [ 9 ]               [ 7, 5 ]            [ 1, 8 ]
          |            |                     |                 |
       ---------    ---------             ---------        ---------
       |       |    |       |             |       |        |       |
     [4]     [2]   [9]     [9]           [7]     [5]      [1]     [8]
       |       |    |       |             |       |        |       |
      Min:2   Max:4   Min:9  Max:9        Min:5   Max:7    Min:1    Max:8
                     |                                    |
                     -------------------------------------
                                   |
                          Combine Min:1, Max:9
                          Overall Min: 1, Max: 9
```

- **Divide**: Split the array into halves until you have single elements.
- **Conquer**: Find the minimum and maximum for each smaller part.
- **Combine**: Compare the min and max of each part to determine the overall min and max.
### Code
  Here's the Python code to find the maximum and minimum elements in an array using the Divide and Conquer approach:

```python
def find_max_min(arr, low, high):
    # Base case: when there is only one element
    if low == high:
        return arr[low], arr[low]
    
    # Base case: when there are two elements
    if high == low + 1:
        if arr[low] > arr[high]:
            return arr[high], arr[low]
        else:
            return arr[low], arr[high]

    # Divide the array into two halves
    mid = (low + high) // 2
    
    # Recursively find the max and min in both halves
    min1, max1 = find_max_min(arr, low, mid)
    min2, max2 = find_max_min(arr, mid + 1, high)
    
    # Combine the results by comparing the min and max of both halves
    overall_min = min(min1, min2)
    overall_max = max(max1, max2)
    
    return overall_min, overall_max

# Example usage:
arr = [4, 2, 9, 7, 5, 1, 8]
n = len(arr)
min_val, max_val = find_max_min(arr, 0, n-1)

print(f"Minimum: {min_val}, Maximum: {max_val}")
```

### Explanation:

- **Base Case**: 
  - If the subarray has only one element, that element is both the minimum and the maximum.
  - If the subarray has two elements, simply compare them to determine the minimum and maximum.
  
- **Divide**: The array is split into two halves, and the function is called recursively on both halves.

- **Conquer**: For each half, the minimum and maximum are calculated.

- **Combine**: The overall minimum and maximum are determined by comparing the minimums and maximums of both halves.

### Example Output:

For the input array `[4, 2, 9, 7, 5, 1, 8]`, the output will be:

```
Minimum: 1, Maximum: 9
```

#### **Metaphor Story:**

Imagine you're on a treasure hunt, looking for two hidden treasures in a dense forest — the highest peak (maximum) and the deepest valley (minimum). You can't search the whole forest at once, so you decide to divide your search into sections.

1. **Base Case**: If you find a small clearing (just one tree), you immediately know that tree is both the highest and the lowest point for that spot.
   
2. **Divide**: You break the forest into smaller sections, and each section has a few trees to explore.

3. **Conquer**: In each section, you look for the highest and lowest trees. If there are 3 trees, you compare them to find the tallest and shortest.

4. **Combine**: Once you’ve explored each section, you compare the highest and lowest trees from each section to find the overall tallest (maximum) and shortest (minimum) trees in the entire forest.

By breaking the task into smaller parts and combining the results, you find the maximum and minimum efficiently.


---
### Merge Sort Algorithm

#### **Definition:**

Merge Sort is a **Divide and Conquer** algorithm that recursively splits the array into two halves, sorts each half, and then merges the sorted halves back together. It's highly efficient with a time complexity of O(n log n), making it ideal for large datasets.

- **Divide**: The array is divided into two halves.
- **Conquer**: Each half is recursively sorted.
- **Combine**: The sorted halves are merged together.

#### **Workflow:**

1. **Divide**: Split the array into two halves.
2. **Conquer**: Recursively sort both halves.
3. **Combine**: Merge the two sorted halves into a single sorted array.

Each time you merge two sorted arrays, the merging process ensures that the result is also sorted.

#### **ASCII Art:**

```
                          [ 4, 2, 9, 7, 5, 1, 8 ]
                                       |
                       -------------------------------
                       |                             |
            [ 4, 2, 9 ]                        [ 7, 5, 1, 8 ]
                |                                    |
          --------------                     -------------------
          |            |                     |                 |
      [ 4, 2 ]      [ 9 ]               [ 7, 5 ]            [ 1, 8 ]
          |            |                     |                 |
       ---------    ---------             ---------        ---------
       |       |    |       |             |       |        |       |
     [4]     [2]   [9]     [9]           [7]     [5]      [1]     [8]
         Merging: [2, 4]   Merging: [9]   Merging: [5, 7]  Merging: [1, 8]
                |                             |
            Merge: [2, 4, 9]                Merge: [1, 5, 7, 8]
                       |                             |
                  Merge: [2, 4, 7, 9]               |
                       |                             |
                     Merge: [1, 2, 4, 5, 7, 8, 9]   Final Sorted Array
```

#### **Code:**

```python
def merge_sort(arr):
    if len(arr) > 1:
        # Find the middle of the array
        mid = len(arr) // 2
        left_half = arr[:mid]
        right_half = arr[mid:]

        # Recursively sort both halves
        merge_sort(left_half)
        merge_sort(right_half)

        # Merging the two halves
        i = j = k = 0

        # Merge the left and right halves into the original array
        while i < len(left_half) and j < len(right_half):
            if left_half[i] < right_half[j]:
                arr[k] = left_half[i]
                i += 1
            else:
                arr[k] = right_half[j]
                j += 1
            k += 1

        # If any elements are left in left_half
        while i < len(left_half):
            arr[k] = left_half[i]
            i += 1
            k += 1

        # If any elements are left in right_half
        while j < len(right_half):
            arr[k] = right_half[j]
            j += 1
            k += 1

# Example usage
arr = [4, 2, 9, 7, 5, 1, 8]
merge_sort(arr)
print(f"Sorted array: {arr}")
```

### **Explanation of the Code:**

1. **Base Case**: If the array has one or no elements, it's already sorted.
2. **Divide**: The array is split into two halves (`left_half` and `right_half`).
3. **Conquer**: The merge_sort function is called recursively to sort both halves.
4. **Merge**: The `merge` part compares elements from both halves and places them in the original array in sorted order.

#### **Metaphor:**

Imagine you are organizing a bookshelf full of books. Here's how Merge Sort would work:

- **Divide**: You start by dividing the bookshelf into two parts: one part with books on the left and the other part on the right.
- **Conquer**: You recursively split each part until each shelf only contains one book. (Each book is trivially "sorted" since there’s just one book per shelf.)
- **Combine**: Now you start organizing the shelves by comparing the books on the left shelf with those on the right. You merge them into a single shelf, but in sorted order. You repeat this process until all the shelves are merged together and you have a perfectly sorted bookshelf.

#### **Example:**

Given the array `[4, 2, 9, 7, 5, 1, 8]`:

1. **Divide**: Split into `[4, 2, 9]` and `[7, 5, 1, 8]`.
2. **Conquer**: Recursively split those into `[4, 2]`, `[9]`, `[7, 5]`, and `[1, 8]`.
3. **Merge**:
   - Merge `[4, 2]` into `[2, 4]`
   - Merge `[7, 5]` into `[5, 7]`
   - Merge `[1, 8]` into `[1, 8]`
   - Merge `[2, 4]` and `[9]` into `[2, 4, 9]`
   - Merge `[5, 7]` and `[1, 8]` into `[1, 5, 7, 8]`
4. **Final Merge**: Merge `[2, 4, 9]` and `[1, 5, 7, 8]` into the fully sorted array `[1, 2, 4, 5, 7, 8, 9]`.

### **Time Complexity:**

- **Best, Worst, and Average Case**: O(n log n)
  - The array is divided log(n) times, and each division involves merging n elements.
  
- **Space Complexity**: O(n)
  - Since Merge Sort requires additional space to store the left and right halves during the merge process.
 
  ---
  ### Quick Sort Algorithm

#### **Definition:**

Quick Sort is another **Divide and Conquer** algorithm. It selects a **pivot** element from the array, partitions the array around the pivot (placing elements smaller than the pivot on the left and larger ones on the right), and then recursively sorts the left and right subarrays.

- **Divide**: Choose a pivot and partition the array into two subarrays (elements smaller than pivot and greater than pivot).
- **Conquer**: Recursively apply the quicksort algorithm to both subarrays.
- **Combine**: Since the array is partitioned and sorted in place, no combining is needed. The array becomes sorted.

#### **Workflow:**

1. **Pivot Selection**: Select a pivot element (typically the last element).
2. **Partition**: Reorganize the array such that all elements smaller than the pivot are to its left, and all elements greater than the pivot are to its right.
3. **Recursive Sort**: Recursively apply quicksort to the left and right subarrays.

#### **ASCII Art:**

```
                        [ 4, 2, 9, 7, 5, 1, 8 ]
                                  |
                           Pivot: 8
                         Partition:
                         [ 4, 2, 7, 5, 1 ]  [ 9 ]
                                  |
                           Pivot: 1
                         Partition:
                         [ 1 ]  [ 4, 2, 7, 5 ]  [ 9 ]
                                  |
                           Pivot: 5
                         Partition:
                         [ 4, 2 ]  [ 7 ]  [ 9 ]
                                  |
                           Pivot: 2
                         Partition:
                         [ 2 ]  [ 4 ]  [ 7 ]  [ 9 ]
```

- **Pivot**: In each recursive step, a pivot element (like 8, 1, 5, 2 in this example) is chosen.
- **Partitioning**: The array is rearranged so that elements smaller than the pivot are on the left, and those greater are on the right.
- **Recursive Sort**: This process continues until the entire array is sorted.

#### **Code:**

```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[-1]
    left = [x for x in arr[:-1] if x <= pivot]
    right = [x for x in arr[:-1] if x > pivot]
    return quick_sort(left) + [pivot] + quick_sort(right)

# Example usage
arr = [4, 2, 9, 7, 5, 1, 8]
sorted_arr = quick_sort(arr)
print(f"Sorted array: {sorted_arr}")
```

### **Explanation of the Code:**

1. **Base Case**: If the array has one or zero elements, it is already sorted.
2. **Pivot Selection**: The last element of the array is selected as the pivot.
3. **Partition**: The array is split into two lists: `left` (elements less than or equal to the pivot) and `right` (elements greater than the pivot).
4. **Recursive Sort**: The function recursively sorts the `left` and `right` subarrays.
5. **Merge**: The result is the concatenation of the sorted `left`, pivot, and sorted `right` arrays.

#### **Metaphor:**

Imagine you are sorting a deck of cards and you pick one card to act as the **pivot**. You arrange the other cards into two groups: one group with cards less than the pivot (on the left) and one group with cards greater than the pivot (on the right).

Next, you repeat this process for each group: picking a new pivot for each smaller group, dividing them again, and so on until all groups have only one card, meaning they’re sorted.

#### **Example:**

For the array `[4, 2, 9, 7, 5, 1, 8]`:

1. **Pivot = 8**: Partition into `[4, 2, 7, 5, 1]` and `[9]`.
2. **Pivot = 1**: Partition into `[1]` and `[4, 2, 7, 5]`.
3. **Pivot = 5**: Partition into `[4, 2]` and `[7]`.
4. **Pivot = 2**: Partition into `[2]` and `[4]`.
5. **Combine**: The final sorted array is `[1, 2, 4, 5, 7, 8, 9]`.

### **Time and Space Complexity:**

| Complexity         | Quick Sort   |
|--------------------|--------------|
| **Best Case**       | O(n log n)   |
| **Average Case**    | O(n log n)   |
| **Worst Case**      | O(n²)        |
| **Space Complexity**| O(log n)     |

- **Best Case**: Occurs when the pivot divides the array into two roughly equal halves. 
- **Average Case**: Occurs in most random cases where the pivot divides the array reasonably evenly.
- **Worst Case**: Occurs when the pivot is the smallest or largest element, resulting in highly unbalanced partitions.
- **Space Complexity**: O(log n) due to recursion stack (in the best case). For worst case (highly unbalanced partitions), it could go up to O(n).

Quick Sort is very fast on average, but care should be taken to avoid worst-case performance.

---

### Randomized Quick Sort

**Randomized Quick Sort** is a variation of the Quick Sort algorithm where the pivot is selected randomly instead of choosing a fixed position (e.g., the last element). This helps to avoid the worst-case performance that occurs when the pivot consistently divides the array in an unbalanced manner, which typically happens when the array is already sorted or nearly sorted.

By randomizing the pivot selection, the expected time complexity remains **O(n log n)**, even in the worst case, with a very high probability.

#### **Steps for Randomized Quick Sort:**

1. **Randomized Pivot Selection**: Choose a pivot randomly from the array.
2. **Partitioning**: Partition the array into two parts — elements smaller than the pivot and elements greater than the pivot.
3. **Recursion**: Recursively apply the same process to both subarrays (left and right of the pivot).
4. **Combine**: The array is sorted in place, so no explicit merge is required.

#### **Code:**

```python
import random

def randomized_partition(arr, low, high):
    # Randomly select a pivot and swap it with the last element
    pivot_index = random.randint(low, high)
    arr[pivot_index], arr[high] = arr[high], arr[pivot_index]
    
    # Partition process: elements < pivot on left, elements > pivot on right
    pivot = arr[high]
    i = low - 1
    for j in range(low, high):
        if arr[j] <= pivot:
            i += 1
            arr[i], arr[j] = arr[j], arr[i]
    
    # Swap the pivot to the correct position
    arr[i + 1], arr[high] = arr[high], arr[i + 1]
    return i + 1

def randomized_quick_sort(arr, low, high):
    if low < high:
        # Partition the array and get the pivot index
        pi = randomized_partition(arr, low, high)
        
        # Recursively apply quick sort to the left and right subarrays
        randomized_quick_sort(arr, low, pi - 1)
        randomized_quick_sort(arr, pi + 1, high)

# Example usage:
arr = [4, 2, 9, 7, 5, 1, 8]
randomized_quick_sort(arr, 0, len(arr) - 1)
print(f"Sorted array: {arr}")
```

### **Explanation of the Code:**

1. **Randomized Pivot Selection (`randomized_partition`)**:
   - A random index `pivot_index` is selected using `random.randint(low, high)`.
   - The element at this index is swapped with the last element of the current subarray to set the pivot at the end of the subarray.
   
2. **Partitioning**:
   - The `partition` step reorders the array such that elements smaller than the pivot are on the left, and elements greater than the pivot are on the right. The pivot is then placed in its final sorted position.

3. **Recursion**:
   - After partitioning, the function is recursively called on the left and right subarrays (those to the left and right of the pivot).

4. **Base Case**:
   - The recursion stops when the subarray has one or zero elements (`low >= high`).

#### **Metaphor:**

Imagine you're organizing a stack of books, and you want to sort them alphabetically. 

- **Randomized Pivot Selection**: Instead of always picking the first or last book to compare against, you randomly choose a book from the stack.
- **Partitioning**: You then rearrange the stack so that books that come before the pivot (alphabetically) are on the left, and those that come after are on the right.
- **Recursion**: You continue the process for each side of the stack, randomly choosing a new pivot and sorting the remaining books until everything is in order.

#### **Time and Space Complexity:**

| Complexity         | Randomized Quick Sort |
|--------------------|-----------------------|
| **Best Case**       | O(n log n)            |
| **Average Case**    | O(n log n)            |
| **Worst Case**      | O(n log n) (with high probability) |
| **Space Complexity**| O(log n)              |

- **Best Case**: Occurs when the pivot divides the array into two equal halves, giving a time complexity of **O(n log n)**.
- **Average Case**: Typically, the pivot will divide the array into reasonably balanced subarrays, leading to **O(n log n)** time complexity.
- **Worst Case**: While the worst-case time complexity is still **O(n²)**, randomization significantly reduces the probability of encountering this scenario. With high probability, it behaves like **O(n log n)**.
- **Space Complexity**: The space complexity is **O(log n)** due to the recursion stack. However, if the partitioning is highly unbalanced, it could go up to **O(n)**.

### **Example:**

For the array `[4, 2, 9, 7, 5, 1, 8]`, the randomized quicksort might first choose a random pivot (e.g., `7`), partition the array, and then recursively sort the left and right subarrays. Because the pivot is chosen randomly, the chances of the algorithm running into its worst case (where the array is split in an unbalanced way) are minimized.

---
### Strassen's Matrix Multiplication

**Strassen's Algorithm** is a more efficient method for matrix multiplication than the standard approach. It divides each matrix into smaller submatrices and recursively multiplies these submatrices using fewer multiplications, achieving a time complexity of **O(n^2.81)** compared to the standard **O(n^3)**.

### **Strassen's Algorithm Steps:**

1. **Divide**: Split each matrix \(A\) and \(B\) into four submatrices of size \(n/2 \times n/2\).
2. **Calculate 7 products**: Using the submatrices, compute 7 products \(P_1\) to \(P_7\) based on a combination of the submatrices.
3. **Combine**: Combine the products \(P_1\) to \(P_7\) to form the resulting matrix \(C\).

### **Formulae for the submatrices:**

![image](https://github.com/user-attachments/assets/8ce9211f-b7d8-4afb-ac6a-dd0024ca32ac)

![image](https://github.com/user-attachments/assets/1858cbbe-33f3-46d1-ad2d-08ff42df514e)

![image](https://github.com/user-attachments/assets/49308d96-e0c9-4246-bde6-eb202460e2df)


### **Workflow:**

1. **Divide** the input matrices \(A\) and \(B\) into four submatrices each.
2. **Compute** the 7 products using the above formulas.
3. **Combine** these products to form the resulting matrix \(C\).

### **Code Implementation:**

```python
import numpy as np

def strassen(A, B):
    # Base case for 2x2 matrices
    if len(A) == 2:
        return np.dot(A, B)

    # Divide matrices into quadrants
    mid = len(A) // 2
    A11, A12, A21, A22 = A[:mid, :mid], A[:mid, mid:], A[mid:, :mid], A[mid:, mid:]
    B11, B12, B21, B22 = B[:mid, :mid], B[:mid, mid:], B[mid:, :mid], B[mid:, mid:]

    # Compute the 7 intermediate products
    M1 = strassen(A11 + A22, B11 + B22)
    M2 = strassen(A21 + A22, B11)
    M3 = strassen(A11, B12 - B22)
    M4 = strassen(A22, B21 - B11)
    M5 = strassen(A11 + A12, B22)
    M6 = strassen(A21 - A11, B11 + B12)
    M7 = strassen(A12 - A22, B21 + B22)

    # Combine the 7 products to get the result
    C11 = M1 + M4 - M5 + M7
    C12 = M3 + M5
    C21 = M2 + M4
    C22 = M1 + M3 - M2 + M6

    # Combine quadrants into the final matrix
    C = np.zeros((2*mid, 2*mid))
    C[:mid, :mid] = C11
    C[:mid, mid:] = C12
    C[mid:, :mid] = C21
    C[mid:, mid:] = C22

    return C

# Example usage
A = np.array([[4, 2], [3, 5]])
B = np.array([[1, 7], [9, 6]])

C = strassen(A, B)
print("Result of Strassen's Matrix Multiplication:")
print(C)
```

### **Explanation of the Code:**

1. **Base Case**: For \(2 \times 2\) matrices, the result is simply the direct multiplication using `np.dot`.
2. **Divide**: The input matrices \(A\) and \(B\) are divided into four submatrices.
3. **Compute the 7 intermediate products**: These products are calculated recursively by calling `strassen` on smaller submatrices.
4. **Combine**: The intermediate products are combined to form the final result matrix \(C\).
5. **Recursive Calls**: The recursion continues until the base case (matrices of size 2x2) is reached.

### **Time Complexity:**

- **Time Complexity**: \(O(n^{\log_2 7}) \approx O(n^{2.81})\)
  - Strassen's algorithm reduces the number of multiplications from \(O(n^3)\) to \(O(n^{2.81})\), which is more efficient for large matrices.
  
- **Space Complexity**: \(O(n^2)\)
  - Space complexity is higher due to the need to store the intermediate submatrices and results during the recursive process.

### **Example:**

![image](https://github.com/user-attachments/assets/9d8ac48c-5c15-4b10-8d9c-2f5199d3662c)


### **Metaphor:**

Imagine you’re multiplying large matrices like stacking multiple large sheets of paper. Instead of multiplying them directly, Strassen’s algorithm suggests cutting the paper into smaller, more manageable pieces and solving those smaller parts recursively. Once you solve these smaller pieces, you combine them to form the full solution.

This method reduces the number of calculations you need to do, speeding up the process of multiplying large matrices.

This makes Merge Sort one of the most efficient and stable sorting algorithms, especially for large data sets.


---

### **Convex Hull**

The **convex hull** of a set of points in a plane is the smallest convex polygon that contains all the points. In simpler terms, imagine stretching a rubber band around a set of points on a 2D plane, and the shape the rubber band forms is the convex hull.

### **Definitions:**
- **Convex**: A set of points is convex if, for any two points within the set, the line segment joining them also lies within the set.
- **Convex Hull**: The convex hull of a set of points is the smallest convex polygon that contains all the points in the set.

### **Applications:**
- Convex hull algorithms are used in computational geometry and have applications in areas such as computer graphics, pattern recognition, and robotics.

### **Visual Representation:**
Imagine you have a set of points like this:

```
(0,0)  (1,3)    (3,1)
   o       o      o  
   
(2,2)  (1,1)  
   o       o  
```

The **convex hull** would be the outer shape that encloses all these points. The rubber band stretched around the points would form the boundary of the convex hull.

### **Convex Hull Algorithms:**

There are several algorithms to find the convex hull of a set of points, but the most common ones are:

1. **Graham Scan Algorithm**
2. **Jarvis March (Gift Wrapping) Algorithm**
3. **QuickHull Algorithm**
4. **Chan's Algorithm**

Here, we will focus on **Graham Scan Algorithm**, which is widely used for its efficiency.

### **Graham Scan Algorithm**

#### **Steps:**
1. **Choose the lowest point**: Start by finding the point with the lowest y-coordinate (if there are ties, choose the point with the lowest x-coordinate).
2. **Sort the points**: Sort the remaining points based on the angle they make with the starting point (usually using polar coordinates).
3. **Build the hull**: Start with the lowest point and iterate over the sorted points, adding them to the convex hull. For each new point, check if it makes a right turn (clockwise) or left turn (counter-clockwise). If it's a right turn, remove the last point from the hull because it doesn't contribute to the convex boundary.

#### **Time Complexity:**
- Sorting the points takes \(O(n \log n)\), and the algorithm processes each point once, resulting in a total time complexity of **O(n log n)**.

### **Code Implementation (Graham Scan Algorithm):**

```python
import matplotlib.pyplot as plt

# Function to find the orientation of the turn (cross product)
def orientation(p, q, r):
    return (q[1] - p[1]) * (r[0] - q[0]) - (q[0] - p[0]) * (r[1] - q[1])

# Function to find the convex hull using Graham Scan
def graham_scan(points):
    # Sort the points based on x-coordinate, and then y-coordinate
    points = sorted(points)

    # Initialize the hull with the first two points
    hull = []

    for p in points:
        # Remove points that would make a non-counter-clockwise turn
        while len(hull) >= 2 and orientation(hull[-2], hull[-1], p) <= 0:
            hull.pop()
        hull.append(p)

    return hull

# Example usage
points = [(0,0), (1,3), (3,1), (2,2), (1,1)]
hull = graham_scan(points)

# Plotting the points and convex hull
x, y = zip(*points)
hx, hy = zip(*hull)

plt.figure()
plt.plot(x, y, 'bo')  # Points
plt.plot(hx + (hx[0],), hy + (hy[0],), 'r-')  # Convex Hull
plt.fill(hx + (hx[0],), hy + (hy[0],), 'r', alpha=0.3)
plt.show()

print("Convex Hull:", hull)
```

### **Explanation of the Code:**

1. **Orientation Function**:
   - This function checks whether the turn from three points \( p \), \( q \), and \( r \) is clockwise or counterclockwise. It returns a positive value for a counterclockwise turn, zero for a straight line, and a negative value for a clockwise turn.

2. **Graham Scan**:
   - The function `graham_scan` takes a list of points and sorts them by their x and y coordinates.
   - It then iterates through the sorted points and adds them to the hull, checking at each step whether the turn is counterclockwise or clockwise.

3. **Visualization**:
   - The points are plotted as blue dots, and the convex hull is drawn in red. The area inside the hull is shaded for clarity.

### **Time and Space Complexity:**

| **Complexity**       | **Graham Scan** |
|----------------------|-----------------|
| **Time Complexity**   | \(O(n \log n)\) |
| **Space Complexity**  | \(O(n)\)         |

### **Metaphor:**

Imagine you're a sculptor who needs to carve out the boundary of a shape from a pile of stones. To do this efficiently:
1. **Choose the base**: Start with the stone at the lowest position.
2. **Look for the next stone**: Select stones that move outward from the base, ensuring each new stone creates the outer edge of the shape.
3. **Avoid backtracking**: If adding a new stone creates a curve that goes inward, discard that stone and look for the next one.

This is exactly how the convex hull is formed — by gradually enclosing all points while making sure to avoid concave shapes.

### **Example:**

Consider a set of points:

```
(0,0)  (1,3)    (3,1)
   o       o      o  

(2,2)  (1,1)  
   o       o  
```

Using the **Graham Scan algorithm**, the convex hull would be the boundary formed by the points `(0,0)`, `(1,3)`, `(3,1)`, and `(2,2)`.

The final convex hull, in this case, is the quadrilateral connecting these points.


---

### **Searching Algorithms in Terms of Divide and Conquer with Code and ASCII Workflow**

Let's break down **Linear Search** and **Binary Search** with their respective **Divide and Conquer** interpretation, **code** and **ASCII workflow**.

---

### **1. Linear Search (Divide and Conquer)**

Although Linear Search doesn’t divide the problem in a traditional sense (like other divide and conquer algorithms), we can still metaphorically describe it as **divide by one**. Here's how we can visualize it:

#### **Workflow in ASCII:**

```
LinearSearch(Arr, Target):
    i = 0
    Divide: Start with the first element.
    While i < len(Arr):
        Conquer: Compare Arr[i] with Target
        If Arr[i] == Target:
            Return i  (found)
        Increment i
    Combine: If target is not found, return -1.
```

#### **Linear Search Code (Python):**

```python
def linear_search(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i  # Element found, return index
    return -1  # Element not found

# Example usage
arr = [10, 20, 30, 40, 50]
target = 30
result = linear_search(arr, target)
print(f"Element found at index: {result}" if result != -1 else "Element not found")
```

---

### **2. Binary Search (Divide and Conquer)**

Binary Search is a true **Divide and Conquer** algorithm. Here's how the array is repeatedly divided into halves until the solution is found.

#### **Workflow in ASCII:**

```
BinarySearch(Arr, Target):
    low = 0, high = len(Arr) - 1
    Divide: Start with the middle element of Arr
    While low <= high:
        mid = (low + high) // 2
        If Arr[mid] == Target:
            Return mid (found)
        Else if Arr[mid] < Target:
            Conquer: Search the right half, low = mid + 1
        Else:
            Conquer: Search the left half, high = mid - 1
    Combine: Return -1 if target is not found.
```

#### **Binary Search Code (Python):**

```python
def binary_search(arr, target):
    low = 0
    high = len(arr) - 1
    
    while low <= high:
        mid = (low + high) // 2  # Middle index
        if arr[mid] == target:
            return mid  # Element found
        elif arr[mid] < target:
            low = mid + 1  # Search the right half
        else:
            high = mid - 1  # Search the left half
    return -1  # Element not found

# Example usage
arr = [10, 20, 30, 40, 50]
target = 30
result = binary_search(arr, target)
print(f"Element found at index: {result}" if result != -1 else "Element not found")
```

---

### **Summary of Workflow:**

#### **Linear Search (Divide by 1)**

1. **Divide**: Start from the first element.
2. **Conquer**: Compare each element with the target.
3. **Combine**: If found, return the index; otherwise, return `-1`.

#### **Binary Search (Divide and Conquer)**

1. **Divide**: Divide the array into two halves by calculating the middle index.
2. **Conquer**: Based on comparison with the middle element, decide to search the left or right half.
3. **Combine**: Return the index if found, otherwise continue the search recursively until found or the range is empty.

---

### **Comparison of Linear Search and Binary Search (DAC Approach)**:

| **Search Type**        | **Linear Search**             | **Binary Search**            |
|------------------------|-------------------------------|------------------------------|
| **Divide**             | Divide by 1 (element-by-element) | Divide in half (sorted array)|
| **Conquer**            | Compare each element          | Recursively search left or right half |
| **Combine**            | Return index if found or -1   | Return index if found or recurse |

---

### **Visual Workflow Summary (ASCII Art):**

#### **Linear Search:**

```
Arr = [10, 20, 30, 40, 50]
Target = 30

Start with i = 0
i = 0: Compare 10 with 30 → Not Found
i = 1: Compare 20 with 30 → Not Found
i = 2: Compare 30 with 30 → Found at index 2
```

#### **Binary Search:**

```
Arr = [10, 20, 30, 40, 50]
Target = 30

low = 0, high = 4, mid = 2
mid = 2: Compare 30 with 30 → Found at index 2
```

In **Binary Search**, the array is halved every time until the target is found, which illustrates **Divide and Conquer** clearly.
Certainly! Below are the visual representations of **Linear Search** and **Binary Search** using **ASCII Art**:

---

### **1. Linear Search (Divide by 1)**

In **Linear Search**, we are looking for an element one by one, sequentially, without dividing the array into halves.

#### **Workflow in ASCII**:

```
Initial Array:
[ 10, 20, 30, 40, 50 ]
Target = 30

Step 1: Compare element 10 with target 30
[ X, 20, 30, 40, 50 ]
(Not Found)

Step 2: Compare element 20 with target 30
[ 10, X, 30, 40, 50 ]
(Not Found)

Step 3: Compare element 30 with target 30
[ 10, 20, X, 40, 50 ]
(Target Found at index 2)
```

#### **Explanation**:
- Start from the leftmost element.
- **Conquer**: Compare each element one by one with the target until it matches or we reach the end.
- **Combine**: Return the index if found, or `-1` if not found.

---

### **2. Binary Search (Divide and Conquer)**

In **Binary Search**, the array is **divided into two halves** repeatedly to narrow down where the target might be.

#### **Workflow in ASCII**:

```
Initial Array:
[ 10, 20, 30, 40, 50 ]
Target = 30

Step 1: Initial array, low = 0, high = 4
Middle = (0 + 4) // 2 = 2
Compare middle element (30) with target 30

[ 10, 20, X, 40, 50 ]  ← Target found at index 2
```

---

#### **Breaking it down into steps**:

```
Initial Array:
[ 10, 20, 30, 40, 50 ]
Target = 30

Step 1: low = 0, high = 4, mid = 2
    [ 10, 20, X, 40, 50 ]
    Compare 30 with 30 → Found!
```

---

#### **Next Example - If Target is 40**:

```
Initial Array:
[ 10, 20, 30, 40, 50 ]
Target = 40

Step 1: low = 0, high = 4, mid = 2
    [ 10, 20, X, 40, 50 ]
    Compare 40 with 30 → Search the right half

Step 2: low = 3, high = 4, mid = 3
    [ 10, 20, 30, X, 50 ]
    Compare 40 with 40 → Found!
```

---

### **Summary of Workflows:**

#### **Linear Search (Divide by 1)**

```
[ 10, 20, 30, 40, 50 ]
Target = 30

1. Compare 10 → No match
2. Compare 20 → No match
3. Compare 30 → Match found at index 2
```

#### **Binary Search (Divide and Conquer)**

```
[ 10, 20, 30, 40, 50 ]
Target = 30

1. Compare middle element 30 → Match found at index 2
```

---

### **Visual Summary in ASCII:**

#### **Linear Search - Sequential Search**:
```
Array = [ 10, 20, 30, 40, 50 ]
Target = 30

Start at index 0:
   [ 10, X, 30, 40, 50 ] -> Compare 10 with 30 -> No match

Move to index 1:
   [ 10, 20, X, 40, 50 ] -> Compare 20 with 30 -> No match

Move to index 2:
   [ 10, 20, 30, X, 50 ] -> Compare 30 with 30 -> Match found
```

#### **Binary Search - Divide and Conquer**:
```
Array = [ 10, 20, 30, 40, 50 ]
Target = 30

Step 1: Compare middle element 30 at index 2 -> Match found
```

In **Binary Search**, we cut the search space in half after each comparison, whereas **Linear Search** just checks each element one-by-one, making it less efficient for larger arrays.

---


### **Greedy Algorithms: Overview**

**Greedy algorithms** are algorithms that make locally optimal choices at each step with the hope of finding a global optimum. The core idea is to always pick the best available option at each step, without considering the bigger picture or looking ahead. Greedy methods are typically faster but may not always lead to the optimal solution for all problems. 

Some key properties of **Greedy Algorithms**:
- **Greedy Choice Property**: A global optimum can be arrived at by selecting a local optimum.
- **Optimal Substructure**: A problem has an optimal solution if the solutions to its subproblems are also optimal.

### **Examples of Greedy Algorithms:**

1. **Optimal Reliability Allocation (Example)**
2. **Fractional Knapsack Problem**
3. **Huffman Coding**
4. **Activity Selection Problem**

We’ll focus on **Optimal Reliability Allocation** as per your request.

---

### **Fractional Knapsack Problem with Partial Item Selection (Greedy Approach)**
## Recommend you to watch videos first 

In the **Fractional Knapsack Problem**, we can indeed **take fractional parts** of items. This means that if there is remaining space in the knapsack after taking some items, we can **fill the knapsack with a portion of the next item**, even if it doesn't fit entirely.

#### **Key Idea:**
- The **Greedy Algorithm** maximizes the value-to-weight ratio for each item and allocates them starting from the highest ratio.
- If there is **remaining capacity** in the knapsack after taking whole items, we can **take a fractional part** of the next item to fill the knapsack fully.

### **Revised Problem Setup:**
Let’s consider the same example with **fractional allocation**:

| Item  | Weight \( w_i \) | Value \( v_i \) | Value-to-Weight Ratio \( \frac{v_i}{w_i} \) |
|-------|------------------|-----------------|---------------------------------------------|
| Item 1| 2                | 40              | 20                                          |
| Item 2| 3                | 50              | 16.67                                       |
| Item 3| 5                | 100             | 20                                          |
| Item 4| 4                | 60              | 15                                          |

**Knapsack Capacity** = 7

### **Steps for the Greedy Approach**:

1. **Sort Items** based on their value-to-weight ratio (highest first).
   
2. **Allocate full items first**, starting with the highest ratio. If there’s still space left in the knapsack, **take a fraction of the next item** to fill the remaining capacity.

3. **Stop once the knapsack is full**, either with full items or a fractional part.

---

### **Detailed Example with Fractional Item Allocation:**

#### **Step 1: Sort Items by Value-to-Weight Ratio**:

```
Item 1: 20 (40/2)
Item 3: 20 (100/5)
Item 2: 16.67 (50/3)
Item 4: 15 (60/4)
```

Sorted order by value-to-weight ratio:  
`Item 1 (20), Item 3 (20), Item 2 (16.67), Item 4 (15)`

#### **Step 2: Allocate Items to the Knapsack**:

**Knapsack capacity = 7**

1. **Allocate Item 1 (Weight 2, Value 40)**:
    - Knapsack space left = 7 - 2 = 5
    - Total value = 40

2. **Allocate Item 3 (Weight 5, Value 100)**:
    - Knapsack space left = 5 - 5 = 0
    - Total value = 40 + 100 = 140

The knapsack is now **full**, and we don't need to take fractional parts of other items. Therefore, the **maximum value** is **140**.

### **Handling Fractional Allocation**:

Now let's consider if we have **less than the exact full capacity left** after taking whole items.

#### Example 2:

Assume the **Knapsack Capacity** is **6** instead of 7.

**Knapsack capacity = 6**

1. **Allocate Item 1 (Weight 2, Value 40)**:
    - Knapsack space left = 6 - 2 = 4
    - Total value = 40

2. **Allocate Item 3 (Weight 5, Value 100)**:
    - Knapsack space left = 4 - 4 = 0 (This is not enough to take the whole item)
    - We can take a fractional part of Item 3 (Remaining capacity = 4).
    
    - **Fraction of Item 3 to be taken**:  
    - Fractional value of Item 3: \( 4/5 \times 100 = 80 \)
    
    - Total value = 40 (from Item 1) + 80 (from the fractional part of Item 3) = **120**

Now, instead of having to leave out Item 3 completely, we take **4/5th of Item 3** to fill the knapsack.

---

### **Visualizing the Process with ASCII**:

#### Example 1: Knapsack Capacity = 7 (Whole Items Only)

```
Initial Capacity = 7

Step 1: Take Item 1 (Weight = 2, Value = 40)
Remaining Capacity = 7 - 2 = 5
Current Value = 40

Step 2: Take Item 3 (Weight = 5, Value = 100)
Remaining Capacity = 5 - 5 = 0
Current Value = 40 + 100 = 140
Knapsack is full.
Maximum Value = 140
```

#### Example 2: Knapsack Capacity = 6 (With Fractional Item)

```
Initial Capacity = 6

Step 1: Take Item 1 (Weight = 2, Value = 40)
Remaining Capacity = 6 - 2 = 4
Current Value = 40

Step 2: Take Item 3 (Weight = 5, Value = 100)
Remaining Capacity = 4 - 4 = 0
Current Value = 40 + (4/5) * 100 = 120
Knapsack is full.
Maximum Value = 120
```

---

### **Greedy Algorithm Code (Python)** with Fractional Allocation:

```python
class Item:
    def __init__(self, weight, value):
        self.weight = weight
        self.value = value
        self.ratio = value / weight

def fractional_knapsack(capacity, items):
    # Sort items based on value-to-weight ratio in descending order
    items.sort(key=lambda x: x.ratio, reverse=True)

    total_value = 0  # Total value in knapsack
    for item in items:
        if capacity == 0:
            break
        # Take the whole item if it fits, otherwise take the fraction
        if item.weight <= capacity:
            total_value += item.value
            capacity -= item.weight
        else:
            total_value += item.value * (capacity / item.weight)
            break  # Knapsack is full
    
    return total_value

# Example usage
items = [Item(2, 40), Item(3, 50), Item(5, 100), Item(4, 60)]
capacity = 6
max_value = fractional_knapsack(capacity, items)
print(f"Maximum value that can be obtained: {max_value}")
```

### **Explanation of Code**:
- The **Item** class calculates the value-to-weight ratio for each item.
- The **fractional_knapsack** function implements the greedy strategy.
- **Items are sorted** in descending order of value-to-weight ratio.
- The knapsack is filled with whole items first, and if there is leftover space, a fractional part of the next item is taken to maximize value.

---

### **Summary**:

In the **Fractional Knapsack Problem**, the greedy approach works by:
1. Sorting items by their value-to-weight ratio.
2. Allocating whole items to the knapsack.
3. Taking a fractional part of the next item if there is leftover capacity.

This greedy approach ensures that we **maximize the value** in the knapsack while respecting its weight constraint. This approach is optimal for the **Fractional Knapsack**, but for the **0/1 Knapsack**, a dynamic programming approach is typically used.

### **1. Optimal Reliability Allocation (Greedy Approach)**

**Problem Description:**
In **Optimal Reliability Allocation**, we are given a system with **n components**, each with a **reliability** value (probability of functioning). We want to allocate resources in a way that maximizes the overall system reliability. The idea is to **distribute resources** to the components in such a way that the total system reliability is maximized.

#### **Greedy Approach**:
1. **Sort** the components in **descending order of their individual reliability**.
2. Allocate resources to components with the highest reliability first.
3. The problem typically has a constraint, such as the total available resources or cost being limited.

#### **Example**:

Suppose we have 4 components in a system, each with a certain reliability value, and we need to allocate a total of **10 resources** to maximize the reliability of the system.

| Component | Reliability | Resources Allocated |
|-----------|-------------|----------------------|
| A         | 0.90        | 3                    |
| B         | 0.85        | 2                    |
| C         | 0.95        | 4                    |
| D         | 0.80        | 1                    |

We want to allocate the resources to maximize the system's total reliability.

#### **Steps for Greedy Allocation**:
1. **Sort the components by reliability**:  
   Sorted: C (0.95), A (0.90), B (0.85), D (0.80).
   
2. **Allocate resources to Component C** first (highest reliability), using the maximum possible allocation.

3. **Allocate remaining resources to Component A**, then B, and so on.

The total system reliability is computed as the **product** of the individual component reliabilities.

---

### **Visualizing the Greedy Approach for Optimal Reliability Allocation**:

1. **Sort components by reliability**:  
```
Original: [ (A, 0.90), (B, 0.85), (C, 0.95), (D, 0.80) ]
Sorted:   [ (C, 0.95), (A, 0.90), (B, 0.85), (D, 0.80) ]
```

2. **Allocate Resources** (Greedy):  
We have 10 units of resources and need to allocate them.

```
Allocate 4 resources to C (highest reliability) → [ (C, 0.95, 4) ]
Allocate 3 resources to A → [ (A, 0.90, 3) ]
Allocate 2 resources to B → [ (B, 0.85, 2) ]
Allocate 1 resource to D → [ (D, 0.80, 1) ]
```

3. **Total Reliability** (Assuming independence between components):
```
Total Reliability = (Reliability of C) * (Reliability of A) * (Reliability of B) * (Reliability of D)
                  = 0.95 * 0.90 * 0.85 * 0.80
                  = 0.6516
```

---

### **Greedy Algorithm Code (Python Example)**

```python
def optimal_reliability_allocation(components, total_resources):
    # Sort components by reliability in descending order
    components.sort(key=lambda x: x[1], reverse=True)

    # Initialize an empty allocation list
    allocation = []

    # Allocate resources based on sorted components
    for i in range(len(components)):
        if total_resources > 0:
            # Allocate resources to the component
            allocate = min(components[i][2], total_resources)  # Allocate max resources to the component
            allocation.append((components[i][0], allocate))
            total_resources -= allocate
        else:
            break  # No resources left to allocate

    return allocation

# Example components with (Component Name, Reliability, Max Resources Available)
components = [
    ('A', 0.90, 3),
    ('B', 0.85, 2),
    ('C', 0.95, 4),
    ('D', 0.80, 1)
]

total_resources = 10

# Run the allocation
allocation = optimal_reliability_allocation(components, total_resources)
print("Optimal Allocation:")
for comp, res in allocation:
    print(f"Component {comp}: Allocated {res} resources")
```

---

### **2. Other Greedy Algorithm Examples**

#### **Fractional Knapsack Problem**:
- You are given a set of items with values and weights, and a knapsack with a fixed capacity.
- The goal is to **maximize the total value** of the items you can carry in the knapsack.
- **Greedy approach**: Select items based on their **value-to-weight ratio**.

#### **Huffman Coding**:
- A lossless data compression algorithm.
- The idea is to assign shorter codes to more frequent characters, which minimizes the total length of the encoded message.

#### **Activity Selection Problem**:
- Given a set of activities with start and finish times, the goal is to select the maximum number of activities that don’t overlap.
- **Greedy approach**: Always select the activity with the earliest finish time that is compatible with the previously selected activity.

---

### **Summary of Greedy Algorithms**:

- **Greedy algorithms** work by making local optimal choices at each step.
- They are usually **fast** and easy to implement, but they don't guarantee an optimal solution for all problems.
- **Optimal Reliability Allocation** is a great example where **greedy approach** works well by allocating resources to components with the highest reliability to maximize the system’s overall reliability.

---
# Minimum Spanning Trees – Prim’s and Kruskal’s Algorithms
## For explanation videos are best codes are written below
### **Quick Recap:**

| Feature                 | **Prim's Algorithm**               | **Kruskal's Algorithm**          |
|-------------------------|------------------------------------|----------------------------------|
| **Approach**             | Expands MST by adding edges from the tree | Builds MST by adding edges globally |
| **Data Structure**       | Min-Heap                           | Sorting + Union-Find            |
| **Time Complexity**      | \( O(E \log V) \)                  | \( O(E \log E) \) or \( O(E \log V) \) |
| **Graph Type**           | Works on connected graphs          | Works on both connected and disconnected graphs |
| **Suitable For**         | Dense graphs                       | Sparse graphs                   |
| **Edge Selection**       | Selects edge with minimum weight connecting MST to a new vertex | Selects minimum weight edges globally |

---

### **Job Sequencing Problem in Greedy Algorithm**

The **Job Sequencing Problem** involves scheduling jobs to maximize profit, given that each job has a deadline and a profit associated with it. The goal is to determine the sequence of jobs that maximizes the total profit, while ensuring that no two jobs overlap in terms of their deadlines.

### **Problem Definition:**
- **Jobs**: A set of jobs, where each job has a deadline and a profit associated with it.
- **Objective**: Maximize the total profit by scheduling jobs such that no two jobs are scheduled at the same time.

### **Greedy Approach:**
1. **Sort the jobs** in decreasing order of profit.
2. **Iterate over the jobs** and try to schedule each job by placing it in the latest available slot before its deadline.
3. **If a slot is available**, schedule the job, otherwise, move to the next job.
4. **Stop** when all jobs are scheduled or no more slots are available.

### **Steps:**
1. Sort all jobs based on their profit in descending order.
2. Initialize an array to track whether a slot is available.
3. For each job, try to find a free slot before its deadline and schedule it.
4. Calculate the total profit from the selected jobs.

### **Example:**
Consider the following jobs:

| Job | Deadline | Profit |
| --- | -------- | ------ |
| J1  | 2        | 100    |
| J2  | 1        | 19     |
| J3  | 2        | 27     |
| J4  | 1        | 25     |
| J5  | 3        | 15     |

### **Workflow (Greedy):**

1. **Sort jobs by profit**:
   Sorted jobs: **J1 (100), J3 (27), J2 (19), J4 (25), J5 (15)**.

2. **Allocate Jobs**:
   - **J1** (Profit 100, Deadline 2): Place it in slot 2 (available).
   - **J3** (Profit 27, Deadline 2): Slot 2 is already filled, so place it in slot 1 (available).
   - **J2** (Profit 19, Deadline 1): No available slots, skip it.
   - **J4** (Profit 25, Deadline 1): No available slots, skip it.
   - **J5** (Profit 15, Deadline 3): Place it in slot 3 (available).

3. **Final Scheduled Jobs**: **J1 (Profit 100), J3 (Profit 27), J5 (Profit 15)**.

4. **Total Profit**: 100 + 27 + 15 = **142**.

### **ASCII Representation:**

```
Jobs: [J1, J2, J3, J4, J5]
Sorted Jobs by Profit: [J1, J3, J4, J2, J5]

Step 1: Slot 2 is available, place J1 (Profit 100)
Step 2: Slot 1 is available, place J3 (Profit 27)
Step 3: No available slot for J2 (Profit 19), skip it
Step 4: No available slot for J4 (Profit 25), skip it
Step 5: Slot 3 is available, place J5 (Profit 15)

Final Job Sequence: J1, J3, J5
Total Profit: 142
```

### **Code (Job Sequencing Problem in Python):**

```python
class Job:
    def __init__(self, id, deadline, profit):
        self.id = id
        self.deadline = deadline
        self.profit = profit

def job_sequencing(jobs, n):
    jobs.sort(key=lambda x: x.profit, reverse=True)

    result = [None] * n
    slot = [False] * n
    total_profit = 0

    for job in jobs:
        for j in range(min(n, job.deadline) - 1, -1, -1):
            if not slot[j]:
                slot[j] = True
                result[j] = job.id
                total_profit += job.profit
                break

    return result, total_profit

# Example jobs
jobs = [Job('J1', 2, 100), Job('J2', 1, 19), Job('J3', 2, 27), Job('J4', 1, 25), Job('J5', 3, 15)]
n = len(jobs)

sequence, profit = job_sequencing(jobs, n)

print("Job Sequence:", sequence)
print("Total Profit:", profit)
```

### **Output:**
```
Job Sequence: ['J1', 'J3', 'J5']
Total Profit: 142
```

### **Summary:**
- **Greedy Approach**: Jobs are sorted by profit, and the algorithm schedules jobs in the latest available slots before their deadlines.
- **Efficiency**: This approach ensures the maximum profit by greedily selecting jobs with the highest profit first.

---


```bash
#### Coming Up topics fo (unit 2)
1. HuffMan Coding https://www.youtube.com/watch?v=NSi75SCWzPs&list=PL1QH9gyQXfgs7foRxIbIH8wmJyDh5QzAm&index=78&pp=iAQB
2. Merge Tree https://www.youtube.com/watch?v=vgIwrm8KjNQ&list=PL1QH9gyQXfgs7foRxIbIH8wmJyDh5QzAm&index=81&pp=iAQB
3. Prims and Kruskal https://www.youtube.com/watch?v=GyTHWZB9kSw&list=PL1QH9gyQXfgs7foRxIbIH8wmJyDh5QzAm&index=85&pp=iAQB
4. Dijkistra algorithm https://www.youtube.com/watch?v=gN_VfRd5wU4&list=PL1QH9gyQXfgs7foRxIbIH8wmJyDh5QzAm&index=90&pp=iAQB
5. Bellman Ford Algorithm https://www.youtube.com/watch?v=Z62R0cZ--tY&list=PL1QH9gyQXfgs7foRxIbIH8wmJyDh5QzAm&index=94&pp=iAQB
```

### **Prim’s Algorithm Code:**
### Algorithm
![image](https://github.com/user-attachments/assets/84c99151-3968-4785-b4dc-5d57fe944a00)

### Python Code
```python
import heapq

def prim(graph, start):
    n = len(graph)
    visited = [False] * n
    min_heap = [(0, start)]
    mst_weight = 0
    mst_edges = []

    while min_heap:
        weight, u = heapq.heappop(min_heap)
        if visited[u]:
            continue
        visited[u] = True
        mst_weight += weight

        for v, w in graph[u]:
            if not visited[v]:
                heapq.heappush(min_heap, (w, v))
                mst_edges.append((u, v, w))

    return mst_weight, mst_edges

graph = [
    [(1, 1), (3, 6), (4, 5)],
    [(0, 1), (2, 4), (3, 5)],
    [(1, 4), (4, 3)],
    [(0, 6), (1, 5), (4, 6)],
    [(0, 5), (2, 3), (3, 6)],
    [(2, 3), (3, 6)]
]

start_node = 0
mst_weight, mst_edges = prim(graph, start_node)
print(f"MST Weight: {mst_weight}")
print(f"MST Edges: {mst_edges}")
```

---

### **Kruskal’s Algorithm Code:**

```python
class DisjointSet:
    def __init__(self, n):
        self.parent = list(range(n))
        self.rank = [0] * n

    def find(self, u):
        if self.parent[u] != u:
            self.parent[u] = self.find(self.parent[u])
        return self.parent[u]

    def union(self, u, v):
        root_u = self.find(u)
        root_v = self.find(v)
        if root_u != root_v:
            if self.rank[root_u] > self.rank[root_v]:
                self.parent[root_v] = root_u
            elif self.rank[root_u] < self.rank[root_v]:
                self.parent[root_u] = root_v
            else:
                self.parent[root_v] = root_u
                self.rank[root_u] += 1
            return True
        return False

def kruskal(graph, n):
    edges = []
    for u in range(n):
        for v, w in graph[u]:
            edges.append((w, u, v))
    edges.sort()

    ds = DisjointSet(n)
    mst_weight = 0
    mst_edges = []

    for weight, u, v in edges:
        if ds.union(u, v):
            mst_weight += weight
            mst_edges.append((u, v, weight))

    return mst_weight, mst_edges

graph = [
    [(1, 1), (3, 6), (4, 5)],
    [(0, 1), (2, 4), (3, 5)],
    [(1, 4), (4, 3)],
    [(0, 6), (1, 5), (4, 6)],
    [(0, 5), (2, 3), (3, 6)],
    [(2, 3), (3, 6)]
]

n = 6
mst_weight, mst_edges = kruskal(graph, n)
print(f"MST Weight: {mst_weight}")
print(f"MST Edges: {mst_edges}")
```

---


