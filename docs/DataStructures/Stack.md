# Stack (LIFO)

## Creating a Stack

```python
# Using a list as a stack
stack = []

# Stack with initial values
stack = [1, 2, 3]  # 3 is at the top

# Using deque (slightly faster for large stacks)
from collections import deque
stack = deque()
```

---

## Operations

| Operation | Time Complexity |
|-----------|-----------------|
| Push | O(1) |
| Pop | O(1) |
| Peek/Top | O(1) |
| Is Empty | O(1) |

### Python Implementations

#### Push - O(1)

```python
def push(stack, value):
    stack.append(value)
```

#### Pop - O(1)

```python
def pop(stack):
    if stack:
        return stack.pop()
    return None
```

#### Peek/Top - O(1)

```python
def peek(stack):
    if stack:
        return stack[-1]
    return None
```

#### Is Empty - O(1)

```python
def is_empty(stack):
    return len(stack) == 0
```

#### Valid Parentheses - O(n)

```python
def is_valid_parentheses(s):
    stack = []
    pairs = {')': '(', '}': '{', ']': '['}
    for char in s:
        if char in '({[':
            stack.append(char)
        elif char in ')}]':
            if not stack or stack[-1] != pairs[char]:
                return False
            stack.pop()
    return len(stack) == 0
```

#### DFS with Stack - O(V + E)

```python
def dfs_iterative(graph, start):
    visited = set()
    stack = [start]
    result = []
    while stack:
        node = stack.pop()
        if node in visited:
            continue
        visited.add(node)
        result.append(node)
        for neighbor in graph[node]:
            if neighbor not in visited:
                stack.append(neighbor)
    return result
```

#### Monotonic Stack (Next Greater Element) - O(n)

```python
def next_greater_element(nums):
    n = len(nums)
    result = [-1] * n
    stack = []  # stores indices
    for i in range(n):
        while stack and nums[i] > nums[stack[-1]]:
            idx = stack.pop()
            result[idx] = nums[i]
        stack.append(i)
    return result
```

#### Evaluate Reverse Polish Notation - O(n)

```python
def eval_rpn(tokens):
    stack = []
    ops = {
        '+': lambda a, b: a + b,
        '-': lambda a, b: a - b,
        '*': lambda a, b: a * b,
        '/': lambda a, b: int(a / b)
    }
    for token in tokens:
        if token in ops:
            b, a = stack.pop(), stack.pop()
            stack.append(ops[token](a, b))
        else:
            stack.append(int(token))
    return stack[0]
```

---

## What It Provides

- Last In First Out ordering
- Backtracking capability
- Nested structure handling

## What It Requires

- Only need access to most recent element

## Good For

- Parentheses/bracket matching
- Function call simulation (DFS)
- Undo operations
- Expression evaluation
- Monotonic stack problems
- Backtracking

## Use When You Need

- Process most recent first
- Match opening/closing pairs
- Track nested levels
- "What was the previous element?"
