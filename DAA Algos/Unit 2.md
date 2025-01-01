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
## 1. Red-Black Tree Algorithms

### Case 1, 2, 3 for Deletion (Theory Overview)
1. **Case 1**: The node to be deleted is a leaf.
2. **Case 2**: The node to be deleted has one child.
3. **Case 3**: The node to be deleted has two children. Replace it with its in-order successor/predecessor and delete.

### Code for Deletion Fix-Up
```python
def delete_fixup(tree, x):
    while x != tree.root and x.color == 'black':
        if x == x.parent.left:
            sibling = x.parent.right
            # Case 1: Sibling is red
            if sibling.color == 'red':
                sibling.color = 'black'
                x.parent.color = 'red'
                left_rotate(tree, x.parent)
                sibling = x.parent.right

            # Case 2: Sibling's children are black
            if sibling.left.color == 'black' and sibling.right.color == 'black':
                sibling.color = 'red'
                x = x.parent
            else:
                # Case 3: Sibling's right child is black
                if sibling.right.color == 'black':
                    sibling.left.color = 'black'
                    sibling.color = 'red'
                    right_rotate(tree, sibling)
                    sibling = x.parent.right

                # Case 4: Sibling's right child is red
                sibling.color = x.parent.color
                x.parent.color = 'black'
                sibling.right.color = 'black'
                left_rotate(tree, x.parent)
                x = tree.root
        else:
            # Mirror the above code for the right subtree
            sibling = x.parent.left
            if sibling.color == 'red':
                sibling.color = 'black'
                x.parent.color = 'red'
                right_rotate(tree, x.parent)
                sibling = x.parent.left

            if sibling.right.color == 'black' and sibling.left.color == 'black':
                sibling.color = 'red'
                x = x.parent
            else:
                if sibling.left.color == 'black':
                    sibling.right.color = 'black'
                    sibling.color = 'red'
                    left_rotate(tree, sibling)
                    sibling = x.parent.left

                sibling.color = x.parent.color
                x.parent.color = 'black'
                sibling.left.color = 'black'
                right_rotate(tree, x.parent)
                x = tree.root

    x.color = 'black'
```

---

## 2. B-Tree Algorithms

### Search
```python
def btree_search(node, key):
    i = 0
    while i < len(node.keys) and key > node.keys[i]:
        i += 1

    if i < len(node.keys) and key == node.keys[i]:
        return node

    if node.leaf:
        return None

    return btree_search(node.children[i], key)
```

### Insert
```python
def btree_insert(tree, key):
    root = tree.root
    if len(root.keys) == (2 * tree.t) - 1:
        new_node = Node()
        tree.root = new_node
        new_node.children.append(root)
        split_child(new_node, 0, root)
        insert_non_full(new_node, key)
    else:
        insert_non_full(root, key)


def insert_non_full(node, key):
    i = len(node.keys) - 1
    if node.leaf:
        node.keys.append(0)
        while i >= 0 and key < node.keys[i]:
            node.keys[i + 1] = node.keys[i]
            i -= 1
        node.keys[i + 1] = key
    else:
        while i >= 0 and key < node.keys[i]:
            i -= 1
        i += 1
        if len(node.children[i].keys) == (2 * t) - 1:
            split_child(node, i, node.children[i])
            if key > node.keys[i]:
                i += 1
        insert_non_full(node.children[i], key)


def split_child(parent, i, child):
    t = len(child.keys) // 2
    new_child = Node()
    parent.children.insert(i + 1, new_child)
    parent.keys.insert(i, child.keys[t])
    new_child.keys = child.keys[t + 1:]
    child.keys = child.keys[:t]
    if not child.leaf:
        new_child.children = child.children[t + 1:]
        child.children = child.children[:t + 1]
```

---

## 3. Binomial Heap Algorithms

### Union
```python
def binomial_heap_union(h1, h2):
    new_heap = merge_heaps(h1, h2)
    if not new_heap.head:
        return new_heap

    prev, curr, next = None, new_heap.head, new_heap.head.sibling

    while next:
        if (curr.degree != next.degree or
            (next.sibling and next.sibling.degree == curr.degree)):
            prev, curr, next = curr, next, next.sibling
        else:
            if curr.key <= next.key:
                curr.sibling = next.sibling
                link_trees(curr, next)
            else:
                if not prev:
                    new_heap.head = next
                else:
                    prev.sibling = next
                link_trees(next, curr)
                curr = next
        next = curr.sibling

    return new_heap


def link_trees(min_tree, other_tree):
    other_tree.parent = min_tree
    other_tree.sibling = min_tree.child
    min_tree.child = other_tree
    min_tree.degree += 1
```

### Extract Min
```python
def binomial_heap_extract_min(heap):
    if not heap.head:
        return None

    min_prev, min_node = None, heap.head
    prev, curr = None, heap.head

    while curr:
        if curr.key < min_node.key:
            min_prev, min_node = prev, curr
        prev, curr = curr, curr.sibling

    if min_prev:
        min_prev.sibling = min_node.sibling
    else:
        heap.head = min_node.sibling

    child = reverse_list(min_node.child)
    new_heap = Heap()
    new_heap.head = child

    return min_node.key, binomial_heap_union(heap, new_heap)
```

---

## 4. Fibonacci Heap (Details follow same structure as Binomial Heap)

---

## 5. Tries (Prefix Tree)

### Search
```python
def trie_search(root, word):
    node = root
    for char in word:
        if char not in node.children:
            return False
        node = node.children[char]
    return node.is_end_of_word
```

### Insert
```python
def trie_insert(root, word):
    node = root
    for char in word:
        if char not in node.children:
            node.children[char] = TrieNode()
        node = node.children[char]
    node.is_end_of_word = True
```

---

## 6. Skip Lists

### Search
```python
def skip_list_search(header, key):
    current = header
    while current:
        while current.forward[0] and current.forward[0].key < key:
            current = current.forward[0]
        current = current.forward[1] if current.forward else None
    return current and current.key == key
