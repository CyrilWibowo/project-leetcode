# Monotonic Deque

## Creating a Monotonic Deque

```python
from collections import deque

# Monotonic deque is a deque with ordering constraint
# Key difference from monotonic stack: can remove from BOTH ends

# Monotonic Decreasing Deque (front is largest)
dq = deque()
for i, num in enumerate(nums):
    # Remove smaller elements from back
    while dq and nums[dq[-1]] < num:
        dq.pop()
    dq.append(i)
    # Remove elements outside window from front
    while dq[0] < i - k + 1:
        dq.popleft()

# Monotonic Increasing Deque (front is smallest)
dq = deque()
for i, num in enumerate(nums):
    # Remove larger elements from back
    while dq and nums[dq[-1]] > num:
        dq.pop()
    dq.append(i)
    # Remove elements outside window from front
    while dq[0] < i - k + 1:
        dq.popleft()
```

---

## Operations

| Operation | Time Complexity |
|-----------|-----------------|
| Push back | O(1) amortized |
| Pop front | O(1) |
| Pop back | O(1) |
| Get max/min | O(1) |
| Process n elements | O(n) total |
| Space | O(k) where k = window size |

*Each element is pushed and popped at most once*

### Python Implementations

#### Sliding Window Maximum - O(n)

```python
from collections import deque

def max_sliding_window(nums, k):
    result = []
    dq = deque()  # stores indices, decreasing order of values

    for i, num in enumerate(nums):
        # Remove indices outside current window
        while dq and dq[0] < i - k + 1:
            dq.popleft()

        # Remove smaller elements (they'll never be max)
        while dq and nums[dq[-1]] < num:
            dq.pop()

        dq.append(i)

        # Window is complete, add max to result
        if i >= k - 1:
            result.append(nums[dq[0]])

    return result

# Example: nums=[1,3,-1,-3,5,3,6,7], k=3
# Output: [3,3,5,5,6,7]
```

#### Sliding Window Minimum - O(n)

```python
from collections import deque

def min_sliding_window(nums, k):
    result = []
    dq = deque()  # stores indices, increasing order of values

    for i, num in enumerate(nums):
        # Remove indices outside current window
        while dq and dq[0] < i - k + 1:
            dq.popleft()

        # Remove larger elements (they'll never be min)
        while dq and nums[dq[-1]] > num:
            dq.pop()

        dq.append(i)

        # Window is complete, add min to result
        if i >= k - 1:
            result.append(nums[dq[0]])

    return result
```

#### Max/Min Queue Data Structure - O(1) per operation

```python
from collections import deque

class MaxQueue:
    def __init__(self):
        self.queue = deque()
        self.max_dq = deque()

    def push(self, val):
        self.queue.append(val)
        while self.max_dq and self.max_dq[-1] < val:
            self.max_dq.pop()
        self.max_dq.append(val)

    def pop(self):
        if self.queue:
            val = self.queue.popleft()
            if val == self.max_dq[0]:
                self.max_dq.popleft()
            return val
        return None

    def get_max(self):
        return self.max_dq[0] if self.max_dq else None


class MinQueue:
    def __init__(self):
        self.queue = deque()
        self.min_dq = deque()

    def push(self, val):
        self.queue.append(val)
        while self.min_dq and self.min_dq[-1] > val:
            self.min_dq.pop()
        self.min_dq.append(val)

    def pop(self):
        if self.queue:
            val = self.queue.popleft()
            if val == self.min_dq[0]:
                self.min_dq.popleft()
            return val
        return None

    def get_min(self):
        return self.min_dq[0] if self.min_dq else None
```

#### Longest Subarray with Bounded Difference - O(n)

```python
from collections import deque

def longest_subarray(nums, limit):
    max_dq = deque()  # decreasing
    min_dq = deque()  # increasing
    left = 0
    result = 0

    for right, num in enumerate(nums):
        # Maintain max deque
        while max_dq and nums[max_dq[-1]] < num:
            max_dq.pop()
        max_dq.append(right)

        # Maintain min deque
        while min_dq and nums[min_dq[-1]] > num:
            min_dq.pop()
        min_dq.append(right)

        # Shrink window if difference exceeds limit
        while nums[max_dq[0]] - nums[min_dq[0]] > limit:
            left += 1
            if max_dq[0] < left:
                max_dq.popleft()
            if min_dq[0] < left:
                min_dq.popleft()

        result = max(result, right - left + 1)

    return result

# Example: nums=[8,2,4,7], limit=4 -> 2
```

#### Constrained Subsequence Sum - O(n)

```python
from collections import deque

def constrained_subset_sum(nums, k):
    n = len(nums)
    dp = nums[:]  # dp[i] = max sum ending at i
    dq = deque()  # stores indices with decreasing dp values

    for i in range(n):
        # Add max from valid window
        if dq:
            dp[i] = max(dp[i], nums[i] + dp[dq[0]])

        # Maintain decreasing deque
        while dq and dp[dq[-1]] <= dp[i]:
            dq.pop()

        if dp[i] > 0:  # only add positive sums
            dq.append(i)

        # Remove elements outside window
        while dq and dq[0] <= i - k:
            dq.popleft()

    return max(dp)

# Example: nums=[10,2,-10,5,20], k=2 -> 37
```

#### Shortest Subarray with Sum at Least K - O(n)

```python
from collections import deque

def shortest_subarray(nums, k):
    n = len(nums)
    # Prefix sums
    prefix = [0] * (n + 1)
    for i in range(n):
        prefix[i + 1] = prefix[i] + nums[i]

    dq = deque()  # stores indices with increasing prefix values
    result = float('inf')

    for i in range(n + 1):
        # Check if we found a valid subarray
        while dq and prefix[i] - prefix[dq[0]] >= k:
            result = min(result, i - dq.popleft())

        # Maintain increasing deque
        while dq and prefix[i] <= prefix[dq[-1]]:
            dq.pop()

        dq.append(i)

    return result if result != float('inf') else -1

# Example: nums=[2,-1,2], k=3 -> 3
```

#### Jump Game VI - O(n)

```python
from collections import deque

def max_result(nums, k):
    n = len(nums)
    dp = [0] * n
    dp[0] = nums[0]
    dq = deque([0])  # stores indices with decreasing dp values

    for i in range(1, n):
        # Remove indices outside window
        while dq and dq[0] < i - k:
            dq.popleft()

        # Current max is at front of deque
        dp[i] = nums[i] + dp[dq[0]]

        # Maintain decreasing deque
        while dq and dp[dq[-1]] <= dp[i]:
            dq.pop()

        dq.append(i)

    return dp[-1]

# Example: nums=[1,-1,-2,4,-7,3], k=2 -> 7
```

#### Max Value of Equation - O(n)

```python
from collections import deque

def find_max_value_of_equation(points, k):
    # yi + yj + |xi - xj| where i < j
    # = yi + yj + xj - xi (since xi < xj)
    # = (yi - xi) + (yj + xj)
    # For each j, maximize (yi - xi) where xj - xi <= k

    dq = deque()  # stores (yi - xi, xi) in decreasing order
    result = float('-inf')

    for x, y in points:
        # Remove points outside window
        while dq and x - dq[0][1] > k:
            dq.popleft()

        # Calculate max with current point
        if dq:
            result = max(result, dq[0][0] + y + x)

        # Maintain decreasing deque
        val = y - x
        while dq and dq[-1][0] <= val:
            dq.pop()

        dq.append((val, x))

    return result

# Example: points=[[1,3],[2,0],[5,10],[6,-10]], k=1 -> 4
```

#### Sliding Window Median (using two deques) - O(n log k)

```python
from collections import deque
import bisect

def median_sliding_window(nums, k):
    window = sorted(nums[:k])
    result = []

    def get_median():
        if k % 2:
            return window[k // 2]
        return (window[k // 2 - 1] + window[k // 2]) / 2

    result.append(get_median())

    for i in range(k, len(nums)):
        # Remove element going out of window
        window.pop(bisect.bisect_left(window, nums[i - k]))
        # Add new element
        bisect.insort(window, nums[i])
        result.append(get_median())

    return result
```

#### Count Subarrays with Bounded Maximum - O(n)

```python
def num_subarray_bounded_max(nums, left, right):
    def count_less_equal(bound):
        result = 0
        count = 0
        for num in nums:
            if num <= bound:
                count += 1
            else:
                count = 0
            result += count
        return result

    return count_less_equal(right) - count_less_equal(left - 1)

# Example: nums=[2,1,4,3], left=2, right=3 -> 3
```

---

## Key Differences: Monotonic Stack vs Deque

| Feature | Monotonic Stack | Monotonic Deque |
|---------|-----------------|-----------------|
| Remove from | Back only | Both ends |
| Use case | Next greater/smaller | Sliding window max/min |
| Window constraint | No | Yes |
| Front access | No | Yes (for window max/min) |

## What It Provides

- Maintains order in sliding window
- Max/min in each window in O(1)

## What It Requires

- Deque with ordering constraint

## Good For

- Sliding window maximum/minimum
- When you need to remove from both ends

## Use When You Need

- Max/min in sliding window
- Maintain order while sliding
- Dynamic programming with window constraint
