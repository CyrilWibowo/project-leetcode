# Monotonic Stack

## Creating a Monotonic Stack

```python
# Monotonic stack is just a regular stack with a constraint
# The constraint is maintained during push operations

# Monotonic Decreasing Stack (top is smallest)
stack = []
for num in nums:
    while stack and stack[-1] < num:
        stack.pop()
    stack.append(num)

# Monotonic Increasing Stack (top is largest)
stack = []
for num in nums:
    while stack and stack[-1] > num:
        stack.pop()
    stack.append(num)

# Usually store indices instead of values
stack = []  # stores indices
for i, num in enumerate(nums):
    while stack and nums[stack[-1]] < num:
        stack.pop()
    stack.append(i)
```

---

## Operations

| Operation | Time Complexity |
|-----------|-----------------|
| Push | O(1) amortized |
| Pop | O(1) |
| Process n elements | O(n) total |
| Space | O(n) |

*Each element is pushed and popped at most once*

### Python Implementations

#### Next Greater Element - O(n)

```python
def next_greater(nums):
    n = len(nums)
    result = [-1] * n
    stack = []  # stores indices

    for i in range(n):
        while stack and nums[i] > nums[stack[-1]]:
            idx = stack.pop()
            result[idx] = nums[i]
        stack.append(i)

    return result

# Example: [2,1,2,4,3] -> [4,2,4,-1,-1]
```

#### Next Smaller Element - O(n)

```python
def next_smaller(nums):
    n = len(nums)
    result = [-1] * n
    stack = []

    for i in range(n):
        while stack and nums[i] < nums[stack[-1]]:
            idx = stack.pop()
            result[idx] = nums[i]
        stack.append(i)

    return result

# Example: [2,1,2,4,3] -> [1,-1,-1,3,-1]
```

#### Previous Greater Element - O(n)

```python
def previous_greater(nums):
    n = len(nums)
    result = [-1] * n
    stack = []

    for i in range(n):
        while stack and nums[stack[-1]] <= nums[i]:
            stack.pop()
        if stack:
            result[i] = nums[stack[-1]]
        stack.append(i)

    return result

# Example: [2,1,2,4,3] -> [-1,2,2,-1,4]
```

#### Previous Smaller Element - O(n)

```python
def previous_smaller(nums):
    n = len(nums)
    result = [-1] * n
    stack = []

    for i in range(n):
        while stack and nums[stack[-1]] >= nums[i]:
            stack.pop()
        if stack:
            result[i] = nums[stack[-1]]
        stack.append(i)

    return result

# Example: [2,1,2,4,3] -> [-1,-1,1,2,2]
```

#### Next Greater Element (Circular Array) - O(n)

```python
def next_greater_circular(nums):
    n = len(nums)
    result = [-1] * n
    stack = []

    # Process array twice for circular behavior
    for i in range(2 * n):
        idx = i % n
        while stack and nums[idx] > nums[stack[-1]]:
            result[stack.pop()] = nums[idx]
        if i < n:
            stack.append(i)

    return result

# Example: [1,2,1] -> [2,-1,2]
```

#### Daily Temperatures - O(n)

```python
def daily_temperatures(temperatures):
    n = len(temperatures)
    result = [0] * n
    stack = []

    for i in range(n):
        while stack and temperatures[i] > temperatures[stack[-1]]:
            idx = stack.pop()
            result[idx] = i - idx
        stack.append(i)

    return result

# Example: [73,74,75,71,69,72,76,73] -> [1,1,4,2,1,1,0,0]
```

#### Largest Rectangle in Histogram - O(n)

```python
def largest_rectangle_histogram(heights):
    stack = []
    max_area = 0
    heights = heights + [0]  # sentinel to pop remaining

    for i, h in enumerate(heights):
        start = i
        while stack and stack[-1][1] > h:
            idx, height = stack.pop()
            width = i - idx
            max_area = max(max_area, height * width)
            start = idx
        stack.append((start, h))

    return max_area

# Alternative using indices
def largest_rectangle_histogram_v2(heights):
    stack = [-1]  # sentinel
    max_area = 0

    for i, h in enumerate(heights):
        while stack[-1] != -1 and heights[stack[-1]] >= h:
            height = heights[stack.pop()]
            width = i - stack[-1] - 1
            max_area = max(max_area, height * width)
        stack.append(i)

    while stack[-1] != -1:
        height = heights[stack.pop()]
        width = len(heights) - stack[-1] - 1
        max_area = max(max_area, height * width)

    return max_area
```

#### Maximal Rectangle in Binary Matrix - O(m * n)

```python
def maximal_rectangle(matrix):
    if not matrix:
        return 0

    rows, cols = len(matrix), len(matrix[0])
    heights = [0] * cols
    max_area = 0

    for row in matrix:
        for j in range(cols):
            heights[j] = heights[j] + 1 if row[j] == '1' else 0

        # Use largest rectangle in histogram
        max_area = max(max_area, largest_rectangle_histogram(heights))

    return max_area
```

#### Trapping Rain Water - O(n)

```python
def trap(height):
    stack = []
    water = 0

    for i, h in enumerate(height):
        while stack and h > height[stack[-1]]:
            bottom = stack.pop()
            if not stack:
                break
            width = i - stack[-1] - 1
            bounded_height = min(h, height[stack[-1]]) - height[bottom]
            water += width * bounded_height
        stack.append(i)

    return water

# Alternative: Two pointer approach
def trap_two_pointer(height):
    if not height:
        return 0

    left, right = 0, len(height) - 1
    left_max = right_max = 0
    water = 0

    while left < right:
        if height[left] < height[right]:
            if height[left] >= left_max:
                left_max = height[left]
            else:
                water += left_max - height[left]
            left += 1
        else:
            if height[right] >= right_max:
                right_max = height[right]
            else:
                water += right_max - height[right]
            right -= 1

    return water
```

#### Stock Span - O(n)

```python
class StockSpanner:
    def __init__(self):
        self.stack = []  # (price, span)

    def next(self, price):
        span = 1
        while self.stack and self.stack[-1][0] <= price:
            span += self.stack.pop()[1]
        self.stack.append((price, span))
        return span

# Example: [100,80,60,70,60,75,85]
# Spans:   [1,  1, 1, 2, 1, 4, 6]
```

#### Remove K Digits - O(n)

```python
def remove_k_digits(num, k):
    stack = []

    for digit in num:
        while k > 0 and stack and stack[-1] > digit:
            stack.pop()
            k -= 1
        stack.append(digit)

    # Remove remaining from end
    stack = stack[:-k] if k else stack

    # Remove leading zeros
    return ''.join(stack).lstrip('0') or '0'

# Example: "1432219", k=3 -> "1219"
```

#### 132 Pattern - O(n)

```python
def find_132_pattern(nums):
    if len(nums) < 3:
        return False

    stack = []
    third = float('-inf')  # the "2" in 132 pattern

    for i in range(len(nums) - 1, -1, -1):
        if nums[i] < third:
            return True
        while stack and stack[-1] < nums[i]:
            third = stack.pop()
        stack.append(nums[i])

    return False
```

#### Sum of Subarray Minimums - O(n)

```python
def sum_subarray_mins(arr):
    MOD = 10**9 + 7
    n = len(arr)

    # Previous less element indices
    prev_less = [-1] * n
    stack = []
    for i in range(n):
        while stack and arr[stack[-1]] >= arr[i]:
            stack.pop()
        prev_less[i] = stack[-1] if stack else -1
        stack.append(i)

    # Next less element indices
    next_less = [n] * n
    stack = []
    for i in range(n - 1, -1, -1):
        while stack and arr[stack[-1]] > arr[i]:
            stack.pop()
        next_less[i] = stack[-1] if stack else n
        stack.append(i)

    # Calculate contribution of each element
    result = 0
    for i in range(n):
        left_count = i - prev_less[i]
        right_count = next_less[i] - i
        result = (result + arr[i] * left_count * right_count) % MOD

    return result
```

#### Sum of Subarray Maximums - O(n)

```python
def sum_subarray_maxs(arr):
    MOD = 10**9 + 7
    n = len(arr)

    # Previous greater element indices
    prev_greater = [-1] * n
    stack = []
    for i in range(n):
        while stack and arr[stack[-1]] <= arr[i]:
            stack.pop()
        prev_greater[i] = stack[-1] if stack else -1
        stack.append(i)

    # Next greater element indices
    next_greater = [n] * n
    stack = []
    for i in range(n - 1, -1, -1):
        while stack and arr[stack[-1]] < arr[i]:
            stack.pop()
        next_greater[i] = stack[-1] if stack else n
        stack.append(i)

    result = 0
    for i in range(n):
        left_count = i - prev_greater[i]
        right_count = next_greater[i] - i
        result = (result + arr[i] * left_count * right_count) % MOD

    return result
```

---

## Pattern Summary

| Problem Type | Stack Order | Comparison |
|--------------|-------------|------------|
| Next Greater | Decreasing | `>` |
| Next Smaller | Increasing | `<` |
| Previous Greater | Decreasing | `<=` |
| Previous Smaller | Increasing | `>=` |

## What It Provides

- Maintains increasing/decreasing order
- "Next greater/smaller" in O(n)

## What It Requires

- Stack with ordering constraint

## Good For

- Next greater element
- Next smaller element
- Largest rectangle in histogram
- Trapping rain water

## Use When You Need

- "What's the next greater/smaller?"
- Remove elements that won't matter
- O(n) solution to "next X" problems
