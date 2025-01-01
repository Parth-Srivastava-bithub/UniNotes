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


## Deletion 
```bash
Their are three cases padh lo bas theory me, code me dimag kharab hoga
```
