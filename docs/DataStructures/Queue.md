# Queue (FIFO)

## Creating a Queue

```python
# Using deque (recommended - O(1) for both ends)
from collections import deque
queue = deque()

# Queue with initial values
queue = deque([1, 2, 3])  # 1 is at the front

# Using list (not recommended - O(n) for pop(0))
queue = []
```

---

## Operations

| Operation | Time Complexity |
|-----------|-----------------|
| Enqueue | O(1) |
| Dequeue | O(1) with deque |
| Peek | O(1) |
| Is Empty | O(1) |

### Python Implementations

#### Enqueue - O(1)

```python
def enqueue(queue, value):
    queue.append(value)
```

#### Dequeue - O(1)

```python
def dequeue(queue):
    if queue:
        return queue.popleft()  # use popleft() with deque
    return None
```

#### Peek - O(1)

```python
def peek(queue):
    if queue:
        return queue[0]
    return None
```

#### Is Empty - O(1)

```python
def is_empty(queue):
    return len(queue) == 0
```

#### BFS (Graph) - O(V + E)

```python
from collections import deque

def bfs(graph, start):
    visited = set([start])
    queue = deque([start])
    result = []
    while queue:
        node = queue.popleft()
        result.append(node)
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
    return result
```

#### Level-Order Traversal (Binary Tree) - O(n)

```python
from collections import deque

def level_order(root):
    if not root:
        return []
    result = []
    queue = deque([root])
    while queue:
        level = []
        for _ in range(len(queue)):
            node = queue.popleft()
            level.append(node.val)
            if node.left:
                queue.append(node.left)
            if node.right:
                queue.append(node.right)
        result.append(level)
    return result
```

#### Sliding Window Maximum (Monotonic Deque) - O(n)

```python
from collections import deque

def max_sliding_window(nums, k):
    result = []
    dq = deque()  # stores indices
    for i, num in enumerate(nums):
        # remove indices outside window
        while dq and dq[0] < i - k + 1:
            dq.popleft()
        # remove smaller elements (maintain decreasing order)
        while dq and nums[dq[-1]] < num:
            dq.pop()
        dq.append(i)
        # add to result once window is full
        if i >= k - 1:
            result.append(nums[dq[0]])
    return result
```

#### Shortest Path (Unweighted Graph) - O(V + E)

```python
from collections import deque

def shortest_path(graph, start, end):
    if start == end:
        return 0
    visited = set([start])
    queue = deque([(start, 0)])  # (node, distance)
    while queue:
        node, dist = queue.popleft()
        for neighbor in graph[node]:
            if neighbor == end:
                return dist + 1
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append((neighbor, dist + 1))
    return -1  # no path found
```

---

## What It Provides

- First In First Out ordering
- Level-by-level processing
- Fair ordering

## What It Requires

- Process in arrival order

## Good For

- BFS (level-order traversal)
- Process tasks in order
- Sliding window (with deque)
- Job scheduling

## Use When You Need

- Process oldest first
- Level-by-level exploration
- Maintain arrival order
- BFS pattern
