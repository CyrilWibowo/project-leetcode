# Array/List

## Creating an Array

```python
# Empty array
arr = []

# Array with initial values
arr = [1, 2, 3, 4, 5]

# Array of fixed size with default value
arr = [0] * 10  # [0, 0, 0, 0, 0, 0, 0, 0, 0, 0]

# 2D array (matrix)
matrix = [[0] * cols for _ in range(rows)]

# Array from range
arr = list(range(5))  # [0, 1, 2, 3, 4]

# Array using list comprehension
arr = [i * 2 for i in range(5)]  # [0, 2, 4, 6, 8]
```

---

## Operations

| Operation | Time Complexity |
|-----------|-----------------|
| Access by index | O(1) |
| Insert/delete at end | O(1) amortized |
| Insert/delete at position | O(n) |
| Search (unsorted) | O(n) |
| Search (sorted) | O(log n) - binary search |

### Python Implementations

#### Access by Index - O(1)

```python
def access(arr, index):
    if 0 <= index < len(arr):
        return arr[index]
    return None
```

#### Insert at End - O(1) amortized

```python
def insert_end(arr, value):
    arr.append(value)
```

#### Delete at End - O(1)

```python
def delete_end(arr):
    if arr:
        return arr.pop()
    return None
```

#### Insert at Position - O(n)

```python
def insert_at(arr, index, value):
    arr.insert(index, value)
```

#### Delete at Position - O(n)

```python
def delete_at(arr, index):
    if 0 <= index < len(arr):
        return arr.pop(index)
    return None
```

#### Linear Search (Unsorted) - O(n)

```python
def linear_search(arr, target):
    for i, val in enumerate(arr):
        if val == target:
            return i
    return -1
```

#### Binary Search (Sorted) - O(log n)

```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1
```

---

## What It Provides

- Random access to elements
- Contiguous memory for cache efficiency
- Simple iteration

## What It Requires

- Known or dynamic size
- Elements of same type

## Good For

- Sequential data
- Index-based access
- Foundation for other structures
- Dynamic programming tables

## Use When You Need

- Direct access by position
- Preserve insertion order
- Iterate through all elements
