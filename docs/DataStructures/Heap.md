# Heap / Priority Queue

## Creating a Heap

```python
import heapq

# Empty heap (min heap by default in Python)
heap = []

# Heapify existing list - O(n)
arr = [3, 1, 4, 1, 5, 9]
heapq.heapify(arr)  # converts in-place

# Create heap by pushing elements
heap = []
for num in [3, 1, 4, 1, 5]:
    heapq.heappush(heap, num)

# Max heap (negate values)
max_heap = []
for num in [3, 1, 4, 1, 5]:
    heapq.heappush(max_heap, -num)

# Heap with tuples (priority, value)
heap = []
heapq.heappush(heap, (priority, value))
```

---

## Operations

| Operation | Time Complexity |
|-----------|-----------------|
| Insert (push) | O(log n) |
| Extract min/max (pop) | O(log n) |
| Peek min/max | O(1) |
| Heapify array | O(n) |

### Python Implementations

#### Push - O(log n)

```python
import heapq

def push(heap, value):
    heapq.heappush(heap, value)
```

#### Pop (Extract Min) - O(log n)

```python
import heapq

def pop(heap):
    if heap:
        return heapq.heappop(heap)
    return None
```

#### Peek Min - O(1)

```python
def peek(heap):
    if heap:
        return heap[0]
    return None
```

#### Push and Pop (more efficient) - O(log n)

```python
import heapq

def push_pop(heap, value):
    return heapq.heappushpop(heap, value)  # push then pop

def pop_push(heap, value):
    return heapq.heapreplace(heap, value)  # pop then push
```

#### Max Heap Operations

```python
import heapq

def max_push(heap, value):
    heapq.heappush(heap, -value)

def max_pop(heap):
    if heap:
        return -heapq.heappop(heap)
    return None

def max_peek(heap):
    if heap:
        return -heap[0]
    return None
```

#### Top K Smallest - O(n log k)

```python
import heapq

def top_k_smallest(nums, k):
    return heapq.nsmallest(k, nums)

# Manual implementation
def top_k_smallest_manual(nums, k):
    heapq.heapify(nums)
    return [heapq.heappop(nums) for _ in range(k)]
```

#### Top K Largest - O(n log k)

```python
import heapq

def top_k_largest(nums, k):
    return heapq.nlargest(k, nums)

# Using max heap (more efficient for streaming)
def top_k_largest_manual(nums, k):
    min_heap = []
    for num in nums:
        heapq.heappush(min_heap, num)
        if len(min_heap) > k:
            heapq.heappop(min_heap)
    return sorted(min_heap, reverse=True)
```

#### Kth Largest Element - O(n log k)

```python
import heapq

def kth_largest(nums, k):
    min_heap = []
    for num in nums:
        heapq.heappush(min_heap, num)
        if len(min_heap) > k:
            heapq.heappop(min_heap)
    return min_heap[0]
```

#### Kth Smallest Element - O(n log k)

```python
import heapq

def kth_smallest(nums, k):
    max_heap = []
    for num in nums:
        heapq.heappush(max_heap, -num)
        if len(max_heap) > k:
            heapq.heappop(max_heap)
    return -max_heap[0]
```

#### Merge K Sorted Lists - O(n log k)

```python
import heapq

def merge_k_sorted(lists):
    heap = []
    for i, lst in enumerate(lists):
        if lst:
            heapq.heappush(heap, (lst[0], i, 0))

    result = []
    while heap:
        val, list_idx, elem_idx = heapq.heappop(heap)
        result.append(val)
        if elem_idx + 1 < len(lists[list_idx]):
            next_val = lists[list_idx][elem_idx + 1]
            heapq.heappush(heap, (next_val, list_idx, elem_idx + 1))
    return result
```

#### Running Median (Two Heaps) - O(log n) per insert

```python
import heapq

class MedianFinder:
    def __init__(self):
        self.small = []  # max heap (negated)
        self.large = []  # min heap

    def add_num(self, num):
        heapq.heappush(self.small, -num)
        heapq.heappush(self.large, -heapq.heappop(self.small))
        if len(self.large) > len(self.small):
            heapq.heappush(self.small, -heapq.heappop(self.large))

    def find_median(self):
        if len(self.small) > len(self.large):
            return -self.small[0]
        return (-self.small[0] + self.large[0]) / 2
```

---

## What It Provides

- Always access to min or max element
- Partial ordering (not fully sorted)
- Dynamic sorting

## What It Requires

- Only need min/max, not full sort
- Extra O(n) space

## Good For

- Top K elements
- Kth largest/smallest
- Merge K sorted lists
- Running median
- Dijkstra's algorithm
- Task scheduling by priority

## Use When You Need

- "Give me the smallest/largest"
- Dynamic min/max as elements change
- Avoid full O(n log n) sort
- Process by priority
