# Hash Set

## Creating a HashSet

```python
# Empty set
s = set()

# Set with initial values
s = {1, 2, 3, 4, 5}

# Set from list (removes duplicates)
s = set([1, 2, 2, 3, 3, 3])  # {1, 2, 3}

# Set from string (unique characters)
s = set("hello")  # {'h', 'e', 'l', 'o'}

# Set using comprehension
s = {x * 2 for x in range(5)}  # {0, 2, 4, 6, 8}

# Frozen set (immutable)
s = frozenset([1, 2, 3])
```

---

## Operations

| Operation | Time Complexity |
|-----------|-----------------|
| Insert | O(1) average |
| Delete | O(1) average |
| Contains | O(1) average |
| Iteration | O(n) |

### Python Implementations

#### Insert - O(1) average

```python
def insert(s, value):
    s.add(value)
```

#### Delete - O(1) average

```python
def delete(s, value):
    s.discard(value)  # no error if not found

def delete_with_error(s, value):
    s.remove(value)  # raises KeyError if not found
```

#### Contains - O(1) average

```python
def contains(s, value):
    return value in s
```

#### Iterate - O(n)

```python
def iterate(s):
    for value in s:
        print(value)
```

#### Remove Duplicates - O(n)

```python
def remove_duplicates(arr):
    return list(set(arr))
```

#### Find Duplicates - O(n)

```python
def find_duplicates(arr):
    seen = set()
    duplicates = []
    for num in arr:
        if num in seen:
            duplicates.append(num)
        seen.add(num)
    return duplicates
```

#### Union - O(n + m)

```python
def union(s1, s2):
    return s1 | s2
    # or: return s1.union(s2)
```

#### Intersection - O(min(n, m))

```python
def intersection(s1, s2):
    return s1 & s2
    # or: return s1.intersection(s2)
```

#### Difference - O(n)

```python
def difference(s1, s2):
    return s1 - s2
    # or: return s1.difference(s2)
```

#### Track Visited (Graph/Tree) - O(1) per check

```python
def bfs_with_visited(graph, start):
    visited = set()
    queue = [start]
    while queue:
        node = queue.pop(0)
        if node in visited:
            continue
        visited.add(node)
        for neighbor in graph[node]:
            if neighbor not in visited:
                queue.append(neighbor)
    return visited
```

---

## What It Provides

- Unique element storage
- Fast membership testing
- Duplicate detection

## What It Requires

- Hashable elements
- Extra O(n) space

## Good For

- Removing duplicates
- Checking existence
- Tracking visited nodes (graphs/trees)
- Finding intersection/union

## Use When You Need

- "Does this exist?"
- "Have I visited this?"
- Uniqueness guarantee
- Set operations (union, intersection)
