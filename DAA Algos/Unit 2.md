# Unit 2 Algos

```bash
Data Structures
├── Red-Black Tree
│   ├── Properties
│   │   ├── Binary Search Tree Properties
│   │   ├── Red-Black Tree Properties
│   ├── Theorem
│   │   └── h ≤ 2 * log(n + 1)
│   ├── Rotations
│   │   ├── Left Rotation
│   │   └── Right Rotation
│   ├── Insertion
│   └── Deletion
│       ├── Case 1
│       ├── Case 2
│       └── Case 3
├── B-Tree
│   ├── Properties
│   ├── Theorem
│   │   └── h ≤ log((n + 1) / 2)
│   ├── Search
│   ├── Create
│   ├── Insert
│   └── Delete
├── Binomial Heap
│   ├── Properties
│   ├── Operations
│   │   ├── Create
│   │   ├── Find
│   │   ├── Union
│   │   ├── Insert
│   │   ├── Extract (Min/Max)
│   │   ├── Decrease
│   │   └── Delete
├── Fibonacci Heap
│   ├── Properties
│   ├── Same Operations as Binomial Heap
├── Tries (Prefix Tree)
└── Skip Lists
```


## 1. Rotation (Left Rotation)
```python
class Node:
    def __init__(self, key):
        self.key = key
        self.left = None  # Left child
        self.right = None  # Right child
        self.parent = None  # Parent node
        self.color = 'red'  # New nodes are typically red in Red-Black Tree

def left_rotate(tree, x):
    """
    Perform a left rotation on the node `x` in a Red-Black Tree.
    """
    y = x.right  # Step 1: Set `y` as the right child of `x`
    x.right = y.left  # Step 2: Move `y`'s left subtree to be `x`'s right subtree
    if y.left:  # Step 3: Update parent of `y`'s left child, if it exists
        y.left.parent = x
    y.parent = x.parent  # Step 4: Link `y`'s parent to `x`'s parent
    if not x.parent:  # If `x` is the root, update the tree's root
        tree.root = y
    elif x == x.parent.left:  # If `x` is a left child, update the left pointer
        x.parent.left = y
    else:  # Otherwise, update the right pointer
        x.parent.right = y
    y.left = x  # Step 5: Make `x` the left child of `y`
    x.parent = y  # Update `x`'s parent to `y`
```


## 1. Rotation (Right Rotation) [Same as left one just little changes] 
### Tip: Replace `x` <--> `y` and `left` <--> `right` else are 90% same

```python
class Node:
    def __init__(self, key):
        self.key = key
        self.left = None  # Left child
        self.right = None  # Right child
        self.parent = None  # Parent node
        self.color = 'red'  # New nodes are typically red in Red-Black Tree

def right_rotate(tree, y):
    """
    Perform a right rotation on the node `y` in a Red-Black Tree.
    """
    x = y.left  # Step 1: Set `x` as the left child of `y`
    y.left = x.right  # Step 2: Move `x`'s right subtree to be `y`'s left subtree
    if x.right:  # Step 3: Update parent of `x`'s right child, if it exists
        x.right.parent = y
    x.parent = y.parent  # Step 4: Link `x`'s parent to `y`'s parent
    if not y.parent:  # If `y` is the root, update the tree's root
        tree.root = x
    elif y == y.parent.left:  # If `y` is a left child, update the left pointer
        y.parent.left = x
    else:  # Otherwise, update the right pointer
        y.parent.right = x
    x.right = y  # Step 5: Make `y` the right child of `x`
    y.parent = x  # Update `y`'s parent to `x`

```

## 2. Insertion (Without Fixing of nodes after voilation)

```python
def insert(tree, key):
    # Create a new node and set its color to red
    new_node = Node(key)
    new_node.color = 'red'
    new_node.left = new_node.right = tree.TNULL  # Initialize children to NIL

    parent, current = None, tree.root
    
    # Find the correct spot to insert the new node (BST insertion)
    while current != tree.TNULL:
        parent = current
        current = current.left if key < current.key else current.right

    # Set the parent of the new node
    new_node.parent = parent
    
    # If parent is None, the tree is empty, make the new node the root
    if not parent:
        tree.root = new_node
    elif key < parent.key:
        parent.left = new_node  # Insert as left child
    else:
        parent.right = new_node  # Insert as right child

```
---
## Four Algo Task
# Unit 2 [2 Jan]

## 1. RB Tree Deletion

### 1. RB Delete (Deletion)

```python

if (z.left) == Null[T] or (z.right) == Null[T]:
    y = z
else:
    y = Tree-Successor
if y.left = Null[T]:
    x = y.left
else:
    x = y.right

p[x] = p[y] 

```

### 2. Deletion Fixup

```python

while (x != root[T] and color[x] = Black):
    do if x = left[p[x]]:
        w = right[p[x]]

        if color[w] = Red:
            color[w] = Black
            color[p[x]] = Red
            Left-Rotate(T, p[x])
        w = right[p[x]]

```
---
# B-Tree
### 3. Search

```python
def B-TREE -SEARCH(x, k)

  i = 1
   while i <= x.n and k > x.keyi
    		i = i + 1
     if i .x<= n and k == x.keyi
 		 return (x,i)
 	elseif x.leaf
 		return NIL
 	else DISK-READ (x.ci)
  		return B-TREE-SEARCH(x. ci ,k)

```

### 4. Creation 

```python

def B-TREE-CREATE(T)
  	x = ALLOCATE-NODE
	x.leaf= TRUE
	x:n=0
	 DISK-WRITE(x)
	 T.root=x

```
