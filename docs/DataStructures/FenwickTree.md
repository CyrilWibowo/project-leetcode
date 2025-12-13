# Fenwick Tree (Binary Indexed Tree)

## Creating a Fenwick Tree

```python
# Basic Fenwick Tree (1-indexed)
class FenwickTree:
    def __init__(self, n):
        self.n = n
        self.tree = [0] * (n + 1)

# Build from array
class FenwickTree:
    def __init__(self, nums):
        self.n = len(nums)
        self.tree = [0] * (self.n + 1)
        for i, num in enumerate(nums):
            self.update(i + 1, num)

# Alternative: O(n) construction
class FenwickTree:
    def __init__(self, nums):
        self.n = len(nums)
        self.tree = [0] + nums[:]  # 1-indexed copy
        for i in range(1, self.n + 1):
            j = i + (i & -i)
            if j <= self.n:
                self.tree[j] += self.tree[i]
```

---

## Operations

| Operation | Time Complexity |
|-----------|-----------------|
| Update (point) | O(log n) |
| Prefix sum query | O(log n) |
| Range sum query | O(log n) |
| Build from array | O(n) or O(n log n) |
| Space | O(n) |

### Python Implementations

#### Basic Fenwick Tree Class

```python
class FenwickTree:
    def __init__(self, n):
        self.n = n
        self.tree = [0] * (n + 1)  # 1-indexed

    def update(self, i, delta):
        """Add delta to element at index i (1-indexed)"""
        while i <= self.n:
            self.tree[i] += delta
            i += i & (-i)  # add lowest set bit

    def query(self, i):
        """Get prefix sum from index 1 to i"""
        total = 0
        while i > 0:
            total += self.tree[i]
            i -= i & (-i)  # remove lowest set bit
        return total

    def range_query(self, left, right):
        """Get sum from index left to right (inclusive, 1-indexed)"""
        return self.query(right) - self.query(left - 1)
```

#### Update (Point Update) - O(log n)

```python
def update(self, i, delta):
    """Add delta to element at index i (1-indexed)"""
    while i <= self.n:
        self.tree[i] += delta
        i += i & (-i)
```

#### Prefix Sum Query - O(log n)

```python
def query(self, i):
    """Get prefix sum from index 1 to i"""
    total = 0
    while i > 0:
        total += self.tree[i]
        i -= i & (-i)
    return total
```

#### Range Sum Query - O(log n)

```python
def range_query(self, left, right):
    """Get sum from index left to right (inclusive, 1-indexed)"""
    return self.query(right) - self.query(left - 1)
```

#### Set Value (Replace) - O(log n)

```python
def set_value(self, i, value):
    """Set element at index i to value"""
    current = self.range_query(i, i)
    self.update(i, value - current)
```

#### Fenwick Tree with 0-indexed Interface

```python
class FenwickTree:
    def __init__(self, n):
        self.n = n
        self.tree = [0] * (n + 1)

    def update(self, i, delta):
        """Add delta to element at index i (0-indexed)"""
        i += 1  # convert to 1-indexed
        while i <= self.n:
            self.tree[i] += delta
            i += i & (-i)

    def query(self, i):
        """Get prefix sum from index 0 to i (inclusive, 0-indexed)"""
        i += 1  # convert to 1-indexed
        total = 0
        while i > 0:
            total += self.tree[i]
            i -= i & (-i)
        return total

    def range_query(self, left, right):
        """Get sum from index left to right (inclusive, 0-indexed)"""
        if left == 0:
            return self.query(right)
        return self.query(right) - self.query(left - 1)
```

#### Count Inversions - O(n log n)

```python
def count_inversions(nums):
    # Coordinate compression
    sorted_nums = sorted(set(nums))
    rank = {v: i + 1 for i, v in enumerate(sorted_nums)}

    n = len(sorted_nums)
    bit = FenwickTree(n)
    inversions = 0

    for num in reversed(nums):
        r = rank[num]
        inversions += bit.query(r - 1)  # count elements smaller than current
        bit.update(r, 1)

    return inversions
```

#### Count Smaller Numbers After Self - O(n log n)

```python
def count_smaller(nums):
    sorted_nums = sorted(set(nums))
    rank = {v: i + 1 for i, v in enumerate(sorted_nums)}

    n = len(sorted_nums)
    bit = FenwickTree(n)
    result = []

    for num in reversed(nums):
        r = rank[num]
        result.append(bit.query(r - 1))
        bit.update(r, 1)

    return result[::-1]
```

#### Range Sum Query - Mutable (LeetCode 307) - O(log n)

```python
class NumArray:
    def __init__(self, nums):
        self.nums = nums
        self.n = len(nums)
        self.tree = [0] * (self.n + 1)
        for i, num in enumerate(nums):
            self._update(i + 1, num)

    def _update(self, i, delta):
        while i <= self.n:
            self.tree[i] += delta
            i += i & (-i)

    def _query(self, i):
        total = 0
        while i > 0:
            total += self.tree[i]
            i -= i & (-i)
        return total

    def update(self, index, val):
        delta = val - self.nums[index]
        self.nums[index] = val
        self._update(index + 1, delta)

    def sumRange(self, left, right):
        return self._query(right + 1) - self._query(left)
```

#### Find Kth Smallest Element - O(log² n)

```python
def find_kth(self, k):
    """Find kth smallest element (1-indexed k)"""
    pos = 0
    total = 0
    log_n = self.n.bit_length()

    for i in range(log_n, -1, -1):
        next_pos = pos + (1 << i)
        if next_pos <= self.n and total + self.tree[next_pos] < k:
            total += self.tree[next_pos]
            pos = next_pos

    return pos + 1
```

#### 2D Fenwick Tree - O(log n * log m)

```python
class FenwickTree2D:
    def __init__(self, rows, cols):
        self.rows = rows
        self.cols = cols
        self.tree = [[0] * (cols + 1) for _ in range(rows + 1)]

    def update(self, row, col, delta):
        """Add delta to element at (row, col) (1-indexed)"""
        i = row
        while i <= self.rows:
            j = col
            while j <= self.cols:
                self.tree[i][j] += delta
                j += j & (-j)
            i += i & (-i)

    def query(self, row, col):
        """Get sum from (1,1) to (row, col)"""
        total = 0
        i = row
        while i > 0:
            j = col
            while j > 0:
                total += self.tree[i][j]
                j -= j & (-j)
            i -= i & (-i)
        return total

    def range_query(self, r1, c1, r2, c2):
        """Get sum in rectangle from (r1,c1) to (r2,c2)"""
        return (self.query(r2, c2)
                - self.query(r1 - 1, c2)
                - self.query(r2, c1 - 1)
                + self.query(r1 - 1, c1 - 1))
```

#### Range Update, Point Query - O(log n)

```python
class FenwickTreeRangeUpdate:
    def __init__(self, n):
        self.n = n
        self.tree = [0] * (n + 1)

    def _update(self, i, delta):
        while i <= self.n:
            self.tree[i] += delta
            i += i & (-i)

    def range_update(self, left, right, delta):
        """Add delta to all elements from left to right (1-indexed)"""
        self._update(left, delta)
        self._update(right + 1, -delta)

    def point_query(self, i):
        """Get value at index i (1-indexed)"""
        total = 0
        while i > 0:
            total += self.tree[i]
            i -= i & (-i)
        return total
```

#### Range Update, Range Query - O(log n)

```python
class FenwickTreeRangeUpdateRangeQuery:
    def __init__(self, n):
        self.n = n
        self.tree1 = [0] * (n + 1)  # stores delta
        self.tree2 = [0] * (n + 1)  # stores delta * i

    def _update(self, tree, i, delta):
        while i <= self.n:
            tree[i] += delta
            i += i & (-i)

    def _query(self, tree, i):
        total = 0
        while i > 0:
            total += tree[i]
            i -= i & (-i)
        return total

    def range_update(self, left, right, delta):
        """Add delta to all elements from left to right (1-indexed)"""
        self._update(self.tree1, left, delta)
        self._update(self.tree1, right + 1, -delta)
        self._update(self.tree2, left, delta * (left - 1))
        self._update(self.tree2, right + 1, -delta * right)

    def prefix_query(self, i):
        """Get prefix sum from 1 to i"""
        return self._query(self.tree1, i) * i - self._query(self.tree2, i)

    def range_query(self, left, right):
        """Get sum from left to right (1-indexed)"""
        return self.prefix_query(right) - self.prefix_query(left - 1)
```

---

## How It Works

The key insight is using the lowest set bit:
- `i & (-i)` gives the lowest set bit of i
- Update: move to next responsible node by adding lowest set bit
- Query: accumulate values by removing lowest set bit

```
Index:  1  2  3  4  5  6  7  8
Binary: 1 10 11 100 101 110 111 1000

tree[1] = arr[1]
tree[2] = arr[1] + arr[2]
tree[3] = arr[3]
tree[4] = arr[1] + arr[2] + arr[3] + arr[4]
...
```

## What It Provides

- Prefix sum queries
- Point updates
- Simpler than segment tree for sums

## What It Requires

- Summation operation
- Array-based data

## Good For

- Range sum queries
- Inversion counting
- Dynamic cumulative frequency

## Use When You Need

- Range sum queries with updates
- Simpler than segment tree
- Only care about sums (not min/max)
