# Deque (Double-Ended Queue)

## Creating a Deque

```python
from collections import deque

# Empty deque
dq = deque()

# Deque with initial values
dq = deque([1, 2, 3])

# Deque with max length (auto-removes from opposite end)
dq = deque(maxlen=3)

# Deque from string
dq = deque("hello")  # deque(['h', 'e', 'l', 'l', 'o'])
```

---

## Operations

| Operation | Time Complexity |
|-----------|-----------------|
| Insert front | O(1) |
| Insert back | O(1) |
| Delete front | O(1) |
| Delete back | O(1) |
| Access front/back | O(1) |
| Access by index | O(n) |

### Python Implementations

#### Insert Front - O(1)

```python
def insert_front(dq, value):
    dq.appendleft(value)
```

#### Insert Back - O(1)

```python
def insert_back(dq, value):
    dq.append(value)
```

#### Delete Front - O(1)

```python
def delete_front(dq):
    if dq:
        return dq.popleft()
    return None
```

#### Delete Back - O(1)

```python
def delete_back(dq):
    if dq:
        return dq.pop()
    return None
```

#### Access Front - O(1)

```python
def peek_front(dq):
    if dq:
        return dq[0]
    return None
```

#### Access Back - O(1)

```python
def peek_back(dq):
    if dq:
        return dq[-1]
    return None
```

#### Sliding Window Maximum (Monotonic Deque) - O(n)

```python
from collections import deque

def max_sliding_window(nums, k):
    result = []
    dq = deque()  # stores indices, decreasing order of values
    for i, num in enumerate(nums):
        # remove indices outside window
        while dq and dq[0] < i - k + 1:
            dq.popleft()
        # remove smaller elements from back
        while dq and nums[dq[-1]] < num:
            dq.pop()
        dq.append(i)
        if i >= k - 1:
            result.append(nums[dq[0]])
    return result
```

#### Sliding Window Minimum (Monotonic Deque) - O(n)

```python
from collections import deque

def min_sliding_window(nums, k):
    result = []
    dq = deque()  # stores indices, increasing order of values
    for i, num in enumerate(nums):
        while dq and dq[0] < i - k + 1:
            dq.popleft()
        # remove larger elements from back
        while dq and nums[dq[-1]] > num:
            dq.pop()
        dq.append(i)
        if i >= k - 1:
            result.append(nums[dq[0]])
    return result
```

#### Palindrome Check - O(n)

```python
from collections import deque

def is_palindrome(s):
    dq = deque(c.lower() for c in s if c.isalnum())
    while len(dq) > 1:
        if dq.popleft() != dq.pop():
            return False
    return True
```

#### Rotate Deque - O(k)

```python
from collections import deque

def rotate_right(dq, k):
    dq.rotate(k)  # positive = right, negative = left

def rotate_left(dq, k):
    dq.rotate(-k)
```

#### Use as Both Stack and Queue

```python
from collections import deque

dq = deque()

# Use as stack (LIFO)
dq.append(1)      # push
dq.pop()          # pop

# Use as queue (FIFO)
dq.append(1)      # enqueue
dq.popleft()      # dequeue
```

---

## What It Provides

- Queue + Stack combined
- Access/modify both ends
- Sliding window optimization

## What It Requires

- Need access to both ends

## Good For

- Sliding window maximum/minimum
- Palindrome checking
- Monotonic deque patterns

## Use When You Need

- Queue but also need to remove from back
- Maintain elements in sliding window
- Both FIFO and LIFO operations
