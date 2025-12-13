# Binary Search Tree (BST)

## Creating a Binary Search Tree

```python
# Node class definition
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

# Create BST from sorted array (balanced)
def sorted_array_to_bst(nums):
    if not nums:
        return None
    mid = len(nums) // 2
    root = TreeNode(nums[mid])
    root.left = sorted_array_to_bst(nums[:mid])
    root.right = sorted_array_to_bst(nums[mid + 1:])
    return root

root = sorted_array_to_bst([1, 2, 3, 4, 5, 6, 7])

# Create BST by inserting values
def create_bst(values):
    if not values:
        return None
    root = TreeNode(values[0])
    for val in values[1:]:
        insert(root, val)
    return root

root = create_bst([5, 3, 7, 1, 4, 6, 8])
```

---

## Operations

| Operation | Time Complexity (Average) | Time Complexity (Worst) |
|-----------|---------------------------|-------------------------|
| Search | O(log n) | O(n) |
| Insert | O(log n) | O(n) |
| Delete | O(log n) | O(n) |
| Find Min/Max | O(log n) | O(n) |
| Inorder Traversal | O(n) | O(n) |

### Python Implementations

#### Search - O(log n) average

```python
def search(root, val):
    if not root:
        return None
    if val == root.val:
        return root
    elif val < root.val:
        return search(root.left, val)
    else:
        return search(root.right, val)

# Iterative
def search_iterative(root, val):
    while root:
        if val == root.val:
            return root
        elif val < root.val:
            root = root.left
        else:
            root = root.right
    return None
```

#### Insert - O(log n) average

```python
def insert(root, val):
    if not root:
        return TreeNode(val)
    if val < root.val:
        root.left = insert(root.left, val)
    else:
        root.right = insert(root.right, val)
    return root

# Iterative
def insert_iterative(root, val):
    new_node = TreeNode(val)
    if not root:
        return new_node
    curr = root
    while True:
        if val < curr.val:
            if not curr.left:
                curr.left = new_node
                break
            curr = curr.left
        else:
            if not curr.right:
                curr.right = new_node
                break
            curr = curr.right
    return root
```

#### Delete - O(log n) average

```python
def delete(root, val):
    if not root:
        return None
    if val < root.val:
        root.left = delete(root.left, val)
    elif val > root.val:
        root.right = delete(root.right, val)
    else:
        # Node found
        if not root.left:
            return root.right
        if not root.right:
            return root.left
        # Node has two children: find inorder successor
        min_node = find_min(root.right)
        root.val = min_node.val
        root.right = delete(root.right, min_node.val)
    return root
```

#### Find Minimum - O(log n) average

```python
def find_min(root):
    if not root:
        return None
    while root.left:
        root = root.left
    return root
```

#### Find Maximum - O(log n) average

```python
def find_max(root):
    if not root:
        return None
    while root.right:
        root = root.right
    return root
```

#### Validate BST - O(n)

```python
def is_valid_bst(root):
    def validate(node, min_val, max_val):
        if not node:
            return True
        if node.val <= min_val or node.val >= max_val:
            return False
        return (validate(node.left, min_val, node.val) and
                validate(node.right, node.val, max_val))
    return validate(root, float('-inf'), float('inf'))

# Using inorder traversal (should be sorted)
def is_valid_bst_inorder(root):
    prev = [float('-inf')]
    def inorder(node):
        if not node:
            return True
        if not inorder(node.left):
            return False
        if node.val <= prev[0]:
            return False
        prev[0] = node.val
        return inorder(node.right)
    return inorder(root)
```

#### Inorder Successor - O(log n) average

```python
def inorder_successor(root, p):
    successor = None
    while root:
        if p.val < root.val:
            successor = root
            root = root.left
        else:
            root = root.right
    return successor
```

#### Inorder Predecessor - O(log n) average

```python
def inorder_predecessor(root, p):
    predecessor = None
    while root:
        if p.val > root.val:
            predecessor = root
            root = root.right
        else:
            root = root.left
    return predecessor
```

#### Lowest Common Ancestor - O(log n) average

```python
def lca(root, p, q):
    while root:
        if p.val < root.val and q.val < root.val:
            root = root.left
        elif p.val > root.val and q.val > root.val:
            root = root.right
        else:
            return root
    return None
```

#### Kth Smallest Element - O(n)

```python
def kth_smallest(root, k):
    stack = []
    curr = root
    count = 0
    while curr or stack:
        while curr:
            stack.append(curr)
            curr = curr.left
        curr = stack.pop()
        count += 1
        if count == k:
            return curr.val
        curr = curr.right
    return -1
```

#### Kth Largest Element - O(n)

```python
def kth_largest(root, k):
    stack = []
    curr = root
    count = 0
    while curr or stack:
        while curr:
            stack.append(curr)
            curr = curr.right  # reverse inorder
        curr = stack.pop()
        count += 1
        if count == k:
            return curr.val
        curr = curr.left
    return -1
```

#### Range Sum - O(n)

```python
def range_sum(root, low, high):
    if not root:
        return 0
    if root.val < low:
        return range_sum(root.right, low, high)
    if root.val > high:
        return range_sum(root.left, low, high)
    return (root.val +
            range_sum(root.left, low, high) +
            range_sum(root.right, low, high))
```

#### Find Closest Value - O(log n) average

```python
def closest_value(root, target):
    closest = root.val
    while root:
        if abs(root.val - target) < abs(closest - target):
            closest = root.val
        if target < root.val:
            root = root.left
        else:
            root = root.right
    return closest
```

#### Floor (Largest <= target) - O(log n) average

```python
def floor(root, target):
    result = None
    while root:
        if root.val == target:
            return root.val
        elif root.val < target:
            result = root.val
            root = root.right
        else:
            root = root.left
    return result
```

#### Ceiling (Smallest >= target) - O(log n) average

```python
def ceiling(root, target):
    result = None
    while root:
        if root.val == target:
            return root.val
        elif root.val > target:
            result = root.val
            root = root.left
        else:
            root = root.right
    return result
```

#### Convert BST to Sorted Doubly Linked List - O(n)

```python
def bst_to_dll(root):
    if not root:
        return None

    first = [None]
    last = [None]

    def inorder(node):
        if not node:
            return
        inorder(node.left)
        if last[0]:
            last[0].right = node
            node.left = last[0]
        else:
            first[0] = node
        last[0] = node
        inorder(node.right)

    inorder(root)
    # Make circular (optional)
    first[0].left = last[0]
    last[0].right = first[0]
    return first[0]
```

---

## BST Property

For every node:
- All values in left subtree < node value
- All values in right subtree > node value

## What It Provides

- Sorted order maintenance
- Logarithmic search
- Range queries

## What It Requires

- Left < Parent < Right property
- Balanced for O(log n) guarantees

## Good For

- Maintaining sorted data
- Range queries
- Floor/ceiling operations
- Ordered statistics

## Use When You Need

- Dynamic sorted structure
- Better than O(n) search
- In-order traversal gives sorted output
