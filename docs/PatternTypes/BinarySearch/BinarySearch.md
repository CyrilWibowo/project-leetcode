# Binary Search Pattern

## What the problem gives you:
- Sorted array OR
- Search space with monotonic property
- Need to find target or boundary

## What the problem requires:
- Find exact value
- Find insertion position
- Find first/last occurrence
- Search in rotated array
- Minimize/maximize with constraints

## Data structures needed:
- Array (sorted or searchable space)

## Approach:
- left = 0, right = n-1
- mid = left + (right-left)//2
- Eliminate half based on comparison

## Common variations:
- Find exact: standard binary search
- Find boundary: adjust conditions
- Answer space: binary search on possible answers

**Time: O(log n) | Space: O(1)**


## Exclusively Binary Search (Pure Pattern)

### Classic Binary Search on Sorted Array

- $\color{green}{\textsf{[Easy]}}$ Binary Search (LC 704)
- $\color{green}{\textsf{[Easy]}}$ Search Insert Position (LC 35)
- $\color{green}{\textsf{[Easy]}}$ First Bad Version (LC 278)
- $\color{green}{\textsf{[Easy]}}$ Sqrt(x) (LC 69)
- $\color{green}{\textsf{[Easy]}}$ Valid Perfect Square (LC 367)
- $\color{green}{\textsf{[Easy]}}$ Guess Number Higher or Lower (LC 374)
- $\color{orange}{\textsf{[Medium]}}$ Find First and Last Position of Element in Sorted Array (LC 34)
- $\color{orange}{\textsf{[Medium]}}$ Search in Rotated Sorted Array (LC 33)
- $\color{orange}{\textsf{[Medium]}}$ Search in Rotated Sorted Array II (LC 81)
- $\color{orange}{\textsf{[Medium]}}$ Find Minimum in Rotated Sorted Array (LC 153)
- $\color{orange}{\textsf{[Medium]}}$ Find Minimum in Rotated Sorted Array II (LC 154)
- $\color{orange}{\textsf{[Medium]}}$ Find Peak Element (LC 162)
- $\color{orange}{\textsf{[Medium]}}$ Single Element in a Sorted Array (LC 540)

### Binary Search on Answer Space

- $\color{green}{\textsf{[Easy]}}$ Arranging Coins (LC 441)
- $\color{orange}{\textsf{[Medium]}}$ Capacity To Ship Packages Within D Days (LC 1011)
- $\color{orange}{\textsf{[Medium]}}$ Koko Eating Bananas (LC 875)
- $\color{orange}{\textsf{[Medium]}}$ Minimize Maximum of Array (LC 2439)
- $\color{orange}{\textsf{[Medium]}}$ Minimum Number of Days to Make m Bouquets (LC 1482)
- $\color{orange}{\textsf{[Medium]}}$ Find the Smallest Divisor Given a Threshold (LC 1283)
- $\color{orange}{\textsf{[Medium]}}$ Magnetic Force Between Two Balls (LC 1552)
- $\color{orange}{\textsf{[Medium]}}$ Divide Chocolate (LC 1231)
- $\color{red}{\textsf{[Hard]}}$ Split Array Largest Sum (LC 410)
- $\color{red}{\textsf{[Hard]}}$ Kth Smallest Number in Multiplication Table (LC 668)
- $\color{red}{\textsf{[Hard]}}$ Minimize Max Distance to Gas Station (LC 774)
- $\color{red}{\textsf{[Hard]}}$ Find K-th Smallest Pair Distance (LC 719)

### Binary Search on 2D Matrix

- $\color{green}{\textsf{[Easy]}}$ Search a 2D Matrix (LC 74)
- $\color{orange}{\textsf{[Medium]}}$ Search a 2D Matrix II (LC 240)
- $\color{orange}{\textsf{[Medium]}}$ Kth Smallest Element in a Sorted Matrix (LC 378)

### Binary Search for Position/Boundary

- $\color{green}{\textsf{[Easy]}}$ Find Smallest Letter Greater Than Target (LC 744)
- $\color{orange}{\textsf{[Medium]}}$ H-Index II (LC 275)
- $\color{orange}{\textsf{[Medium]}}$ Find Right Interval (LC 436)
- $\color{orange}{\textsf{[Medium]}}$ Time Based Key-Value Store (LC 981)

---

## Combined with Other Patterns

### Binary Search + Two Pointers

- $\color{orange}{\textsf{[Medium]}}$ 3Sum Closest (LC 16)
- $\color{orange}{\textsf{[Medium]}}$ Find K Closest Elements (LC 658)
- $\color{red}{\textsf{[Hard]}}$ Trapping Rain Water II (LC 407)

### Binary Search + Greedy

- $\color{orange}{\textsf{[Medium]}}$ Gas Station (LC 134)
- $\color{orange}{\textsf{[Medium]}}$ Jump Game II (LC 45)
- $\color{orange}{\textsf{[Medium]}}$ Minimum Number of Days to Make m Bouquets (LC 1482)
- $\color{red}{\textsf{[Hard]}}$ Split Array Largest Sum (LC 410)
- $\color{orange}{\textsf{[Medium]}}$ Capacity To Ship Packages Within D Days (LC 1011)
- $\color{orange}{\textsf{[Medium]}}$ Koko Eating Bananas (LC 875)

### Binary Search + DP

- $\color{red}{\textsf{[Hard]}}$ Russian Doll Envelopes (LC 354)
- $\color{orange}{\textsf{[Medium]}}$ Longest Increasing Subsequence (LC 300)
- $\color{red}{\textsf{[Hard]}}$ Number of Longest Increasing Subsequence (LC 673)

### Binary Search + Sorting

- $\color{orange}{\textsf{[Medium]}}$ Count of Smaller Numbers After Self (LC 315)
- $\color{orange}{\textsf{[Medium]}}$ Find Right Interval (LC 436)
- $\color{red}{\textsf{[Hard]}}$ Count of Range Sum (LC 327)

### Binary Search + Hash Map

- $\color{orange}{\textsf{[Medium]}}$ Random Pick with Weight (LC 528)
- $\color{red}{\textsf{[Hard]}}$ Maximum Frequency Stack (LC 895)

### Binary Search + Heap

- $\color{red}{\textsf{[Hard]}}$ Find Median from Data Stream (LC 295)
- $\color{red}{\textsf{[Hard]}}$ IPO (LC 502)

### Binary Search + Sliding Window

- $\color{red}{\textsf{[Hard]}}$ Minimum Window Substring (LC 76)
- $\color{orange}{\textsf{[Medium]}}$ Minimum Size Subarray Sum (LC 209)
- $\color{red}{\textsf{[Hard]}}$ Shortest Subarray with Sum at Least K (LC 862)

### Binary Search + Prefix Sum

- $\color{orange}{\textsf{[Medium]}}$ Random Pick with Weight (LC 528)
- $\color{orange}{\textsf{[Medium]}}$ Range Sum Query - Immutable (LC 303)
- $\color{orange}{\textsf{[Medium]}}$ Subarray Sum Equals K (LC 560)

### Binary Search + DFS/BFS

- $\color{orange}{\textsf{[Medium]}}$ Path With Minimum Effort (LC 1631)
- $\color{red}{\textsf{[Hard]}}$ Swim in Rising Water (LC 778)
- $\color{orange}{\textsf{[Medium]}}$ Minimum Time to Collect All Apples in a Tree (LC 1443)

### Binary Search + Trie

- $\color{red}{\textsf{[Hard]}}$ Maximum XOR of Two Numbers in an Array (LC 421)
- $\color{red}{\textsf{[Hard]}}$ Maximum XOR With an Element From Array (LC 1707)

### Binary Search + Union-Find

- $\color{red}{\textsf{[Hard]}}$ Minimize Malware Spread (LC 924)

### Binary Search + Math

- $\color{green}{\textsf{[Easy]}}$ Sqrt(x) (LC 69)
- $\color{orange}{\textsf{[Medium]}}$ Pow(x, n) (LC 50)
- $\color{red}{\textsf{[Hard]}}$ Nth Magical Number (LC 878)
- $\color{orange}{\textsf{[Medium]}}$ Count Complete Tree Nodes (LC 222)

### Binary Search + String

- $\color{orange}{\textsf{[Medium]}}$ Longest Duplicate Substring (LC 1044)
- $\color{red}{\textsf{[Hard]}}$ Shortest Palindrome (LC 214)

### Binary Search + Bit Manipulation

- $\color{orange}{\textsf{[Medium]}}$ Single Element in a Sorted Array (LC 540)
- $\color{red}{\textsf{[Hard]}}$ Maximum XOR of Two Numbers in an Array (LC 421)

### Binary Search on Rotated/Modified Arrays

- $\color{orange}{\textsf{[Medium]}}$ Search in Rotated Sorted Array (LC 33)
- $\color{orange}{\textsf{[Medium]}}$ Search in Rotated Sorted Array II (LC 81)
- $\color{orange}{\textsf{[Medium]}}$ Find Minimum in Rotated Sorted Array (LC 153)
- $\color{orange}{\textsf{[Medium]}}$ Find Minimum in Rotated Sorted Array II (LC 154)

### Binary Search + Simulation

- $\color{orange}{\textsf{[Medium]}}$ Divide Chocolate (LC 1231)
- $\color{red}{\textsf{[Hard]}}$ Minimum Number of Days to Make m Bouquets (LC 1482)

---

## By Category

### Pure Classic Binary Search
1. $\color{green}{\textsf{[Easy]}}$ Binary Search (LC 704)
2. $\color{green}{\textsf{[Easy]}}$ Search Insert Position (LC 35)
3. $\color{green}{\textsf{[Easy]}}$ First Bad Version (LC 278)
4. $\color{green}{\textsf{[Easy]}}$ Sqrt(x) (LC 69)
5. $\color{green}{\textsf{[Easy]}}$ Valid Perfect Square (LC 367)
6. $\color{green}{\textsf{[Easy]}}$ Guess Number Higher or Lower (LC 374)
7. $\color{green}{\textsf{[Easy]}}$ Find Smallest Letter Greater Than Target (LC 744)
8. $\color{orange}{\textsf{[Medium]}}$ Find First and Last Position (LC 34)
9. $\color{orange}{\textsf{[Medium]}}$ Single Element in a Sorted Array (LC 540)
10. $\color{orange}{\textsf{[Medium]}}$ H-Index II (LC 275)

### Rotated Array Binary Search
1. $\color{orange}{\textsf{[Medium]}}$ Search in Rotated Sorted Array (LC 33)
2. $\color{orange}{\textsf{[Medium]}}$ Search in Rotated Sorted Array II (LC 81)
3. $\color{orange}{\textsf{[Medium]}}$ Find Minimum in Rotated Sorted Array (LC 153)
4. $\color{orange}{\textsf{[Medium]}}$ Find Minimum in Rotated Sorted Array II (LC 154)
5. $\color{orange}{\textsf{[Medium]}}$ Find Peak Element (LC 162)

### Binary Search on Answer Space
1. $\color{green}{\textsf{[Easy]}}$ Arranging Coins (LC 441)
2. $\color{orange}{\textsf{[Medium]}}$ Capacity To Ship Packages (LC 1011)
3. $\color{orange}{\textsf{[Medium]}}$ Koko Eating Bananas (LC 875)
4. $\color{orange}{\textsf{[Medium]}}$ Minimize Maximum of Array (LC 2439)
5. $\color{orange}{\textsf{[Medium]}}$ Minimum Days to Make m Bouquets (LC 1482)
6. $\color{orange}{\textsf{[Medium]}}$ Find the Smallest Divisor (LC 1283)
7. $\color{orange}{\textsf{[Medium]}}$ Magnetic Force Between Two Balls (LC 1552)
8. $\color{orange}{\textsf{[Medium]}}$ Divide Chocolate (LC 1231)
9. $\color{red}{\textsf{[Hard]}}$ Split Array Largest Sum (LC 410)
10. $\color{red}{\textsf{[Hard]}}$ Kth Smallest in Multiplication Table (LC 668)
11. $\color{red}{\textsf{[Hard]}}$ Minimize Max Distance to Gas Station (LC 774)
12. $\color{red}{\textsf{[Hard]}}$ Find K-th Smallest Pair Distance (LC 719)

### Binary Search on 2D Matrix
1. $\color{green}{\textsf{[Easy]}}$ Search a 2D Matrix (LC 74)
2. $\color{orange}{\textsf{[Medium]}}$ Search a 2D Matrix II (LC 240)
3. $\color{orange}{\textsf{[Medium]}}$ Kth Smallest Element in Sorted Matrix (LC 378)

### Binary Search + DP/LIS
1. $\color{orange}{\textsf{[Medium]}}$ Longest Increasing Subsequence (LC 300)
2. $\color{red}{\textsf{[Hard]}}$ Russian Doll Envelopes (LC 354)
3. $\color{red}{\textsf{[Hard]}}$ Number of Longest Increasing Subsequence (LC 673)

### Binary Search + Greedy
1. $\color{orange}{\textsf{[Medium]}}$ Capacity To Ship Packages (LC 1011)
2. $\color{orange}{\textsf{[Medium]}}$ Koko Eating Bananas (LC 875)
3. $\color{red}{\textsf{[Hard]}}$ Split Array Largest Sum (LC 410)
4. $\color{orange}{\textsf{[Medium]}}$ Minimize Maximum of Array (LC 2439)

### Binary Search + Graph/DFS/BFS
1. $\color{orange}{\textsf{[Medium]}}$ Path With Minimum Effort (LC 1631)
2. $\color{red}{\textsf{[Hard]}}$ Swim in Rising Water (LC 778)

---

## Summary by Difficulty

### Easy (Pure Binary Search)

- $\color{green}{\textsf{[Easy]}}$ Binary Search (LC 704)
- $\color{green}{\textsf{[Easy]}}$ Search Insert Position (LC 35)
- $\color{green}{\textsf{[Easy]}}$ First Bad Version (LC 278)
- $\color{green}{\textsf{[Easy]}}$ Sqrt(x) (LC 69)
- $\color{green}{\textsf{[Easy]}}$ Valid Perfect Square (LC 367)
- $\color{green}{\textsf{[Easy]}}$ Guess Number Higher or Lower (LC 374)
- $\color{green}{\textsf{[Easy]}}$ Find Smallest Letter Greater Than Target (LC 744)
- $\color{green}{\textsf{[Easy]}}$ Arranging Coins (LC 441)
- $\color{green}{\textsf{[Easy]}}$ Search a 2D Matrix (LC 74)

### Medium (Pure Binary Search)

- $\color{orange}{\textsf{[Medium]}}$ Find First and Last Position (LC 34)
- $\color{orange}{\textsf{[Medium]}}$ Search in Rotated Sorted Array (LC 33)
- $\color{orange}{\textsf{[Medium]}}$ Search in Rotated Sorted Array II (LC 81)
- $\color{orange}{\textsf{[Medium]}}$ Find Minimum in Rotated Sorted Array (LC 153)
- $\color{orange}{\textsf{[Medium]}}$ Find Minimum in Rotated Sorted Array II (LC 154)
- $\color{orange}{\textsf{[Medium]}}$ Find Peak Element (LC 162)
- $\color{orange}{\textsf{[Medium]}}$ Single Element in a Sorted Array (LC 540)
- $\color{orange}{\textsf{[Medium]}}$ H-Index II (LC 275)
- $\color{orange}{\textsf{[Medium]}}$ Search a 2D Matrix II (LC 240)

### Medium (Answer Space Binary Search)

- $\color{orange}{\textsf{[Medium]}}$ Capacity To Ship Packages (LC 1011)
- $\color{orange}{\textsf{[Medium]}}$ Koko Eating Bananas (LC 875)
- $\color{orange}{\textsf{[Medium]}}$ Minimize Maximum of Array (LC 2439)
- $\color{orange}{\textsf{[Medium]}}$ Minimum Days to Make m Bouquets (LC 1482)
- $\color{orange}{\textsf{[Medium]}}$ Find the Smallest Divisor (LC 1283)
- $\color{orange}{\textsf{[Medium]}}$ Magnetic Force Between Two Balls (LC 1552)
- $\color{orange}{\textsf{[Medium]}}$ Divide Chocolate (LC 1231)
- $\color{orange}{\textsf{[Medium]}}$ Kth Smallest Element in Sorted Matrix (LC 378)

### Medium (Combined)

- $\color{orange}{\textsf{[Medium]}}$ Find K Closest Elements (LC 658) - with two pointers
- $\color{orange}{\textsf{[Medium]}}$ Longest Increasing Subsequence (LC 300) - with DP
- $\color{orange}{\textsf{[Medium]}}$ Random Pick with Weight (LC 528) - with prefix sum
- $\color{orange}{\textsf{[Medium]}}$ Minimum Size Subarray Sum (LC 209) - with prefix sum
- $\color{orange}{\textsf{[Medium]}}$ Count of Smaller Numbers After Self (LC 315) - with sorting
- $\color{orange}{\textsf{[Medium]}}$ Find Right Interval (LC 436) - with sorting
- $\color{orange}{\textsf{[Medium]}}$ Time Based Key-Value Store (LC 981) - with hash map
- $\color{orange}{\textsf{[Medium]}}$ Path With Minimum Effort (LC 1631) - with BFS
- $\color{orange}{\textsf{[Medium]}}$ Pow(x, n) (LC 50) - with math
- $\color{orange}{\textsf{[Medium]}}$ Count Complete Tree Nodes (LC 222) - with tree traversal

### Hard (Answer Space Binary Search)

- $\color{red}{\textsf{[Hard]}}$ Split Array Largest Sum (LC 410)
- $\color{red}{\textsf{[Hard]}}$ Kth Smallest in Multiplication Table (LC 668)
- $\color{red}{\textsf{[Hard]}}$ Minimize Max Distance to Gas Station (LC 774)
- $\color{red}{\textsf{[Hard]}}$ Find K-th Smallest Pair Distance (LC 719)

### Hard (Combined)

- $\color{red}{\textsf{[Hard]}}$ Russian Doll Envelopes (LC 354) - with DP/LIS
- $\color{red}{\textsf{[Hard]}}$ Number of Longest Increasing Subsequence (LC 673) - with DP
- $\color{red}{\textsf{[Hard]}}$ Swim in Rising Water (LC 778) - with BFS
- $\color{red}{\textsf{[Hard]}}$ Maximum XOR of Two Numbers (LC 421) - with Trie
- $\color{red}{\textsf{[Hard]}}$ Longest Duplicate Substring (LC 1044) - with hashing
- $\color{red}{\textsf{[Hard]}}$ Count of Range Sum (LC 327) - with sorting
- $\color{red}{\textsf{[Hard]}}$ Nth Magical Number (LC 878) - with math

---

## Quick Recognition Guide

### Use PURE Binary Search when:
1. **Sorted array** and need to find/insert element
2. **Monotonic function** (if f(x) is true, f(x+1) is also true)
3. **Find boundary** (first/last occurrence of condition)
4. **O(log n)** time complexity required
5. **Search space has order** (can eliminate half)

### Use ANSWER SPACE Binary Search when:
1. "Minimize the maximum" or "maximize the minimum"
2. "Find minimum X such that condition is satisfied"
3. "Allocate/distribute resources optimally"
4. Can **validate** if a value works in O(n) or O(n log n)
5. Answer has a **range** [min, max] to search

### Use COMBINED Binary Search when:
1. Need optimal subsequence → Binary Search + DP (LIS)
2. Need to validate with graph → Binary Search + BFS/DFS
3. Need weighted random → Binary Search + Prefix Sum
4. Need position and expansion → Binary Search + Two Pointers
5. Complex validation logic → Binary Search + appropriate structure

### Key Indicators:
- "Sorted array/list"
- "Find in O(log n)"
- "Rotated sorted array"
- "Minimize maximum" or "maximize minimum"
- "First/last occurrence"
- "Peak element"
- "Kth smallest/largest" (in sorted matrix)
- "Find position to insert"
- "Binary search" explicitly mentioned
- "Allocate" or "distribute" with constraints
- "Minimum days/time/capacity to..."

### Common Patterns:

**Pattern 1: Find Exact Value**
```python
while left <= right:
    mid = left + (right - left) // 2
    if arr[mid] == target:
        return mid
    elif arr[mid] < target:
        left = mid + 1
    else:
        right = mid - 1
return -1
```

**Pattern 2: Find Left Boundary (First Occurrence)**
```python
result = -1
while left <= right:
    mid = left + (right - left) // 2
    if arr[mid] >= target:
        result = mid  # potential answer
        right = mid - 1  # search left
    else:
        left = mid + 1
return result
```

**Pattern 3: Find Right Boundary (Last Occurrence)**
```python
result = -1
while left <= right:
    mid = left + (right - left) // 2
    if arr[mid] <= target:
        result = mid  # potential answer
        left = mid + 1  # search right
    else:
        right = mid - 1
return result
```

**Pattern 4: Binary Search on Answer Space**
```python
def is_valid(mid):
    # Check if 'mid' satisfies the condition
    # Usually involves greedy check in O(n)
    pass

left, right = min_possible, max_possible
result = -1
while left <= right:
    mid = left + (right - left) // 2
    if is_valid(mid):
        result = mid
        # Depending on problem:
        right = mid - 1  # try to minimize
        # OR
        left = mid + 1   # try to maximize
    else:
        # Adjust search space
        pass
return result
```

**Pattern 5: Rotated Array**
```python
while left <= right:
    mid = left + (right - left) // 2

    # Only needed if duplicates
    if nums[l] == nums[mid]:
        l += 1 
        continue

    # Check which half is sorted
    if arr[left] <= arr[mid]:
        # Left half is sorted
        if arr[left] <= target < arr[mid]:
            right = mid - 1
        else:
            left = mid + 1
    else:
        # Right half is sorted
        if arr[mid] < target <= arr[right]:
            left = mid + 1
        else:
            right = mid - 1
```

---

## Binary Search Variations

### 1. Classic Binary Search
- Find exact element in sorted array
- Time: O(log n), Space: O(1)

### 2. Find Boundary
- First/last occurrence of element
- Lower bound / upper bound
- Time: O(log n), Space: O(1)

### 3. Rotated Array Search
- Find element or minimum in rotated sorted array
- Identify sorted half, then search
- Time: O(log n), Space: O(1)

### 4. Binary Search on Answer Space
- Search in range [min_answer, max_answer]
- Validate each mid with O(n) or O(n log n) check
- Time: O(n log(max-min)), Space: O(1)

### 5. Binary Search on 2D
- Treat as 1D: mid → [mid/n][mid%n]
- Or search row then column
- Time: O(log(m×n)), Space: O(1)

### 6. Binary Search + DP
- LIS with binary search: O(n log n) instead of O(n²)
- Maintain array of smallest tail values
- Time: O(n log n), Space: O(n)

### 7. Peak Finding
- Compare mid with neighbors
- Move toward higher value
- Time: O(log n), Space: O(1)

### 8. Binary Search on Implicit Array
- Array not given explicitly (e.g., First Bad Version)
- Use function calls instead of array access
- Time: O(log n), Space: O(1)

---

## Common Pitfalls

### 1. Integer Overflow
❌ `mid = (left + right) / 2`
✅ `mid = left + (right - left) // 2`

### 2. Infinite Loop
- Make sure search space shrinks
- Check boundary conditions (left = mid vs left = mid + 1)

### 3. Off-by-One Errors
- Be clear: inclusive or exclusive boundaries?
- `while left <= right` vs `while left < right`

### 4. Condition Logic
- Be precise about what you're searching for
- First occurrence vs last occurrence vs any occurrence

### 5. Answer Space Range
- Determine correct min and max for answer space
- Consider edge cases (0, 1, max_value)

### 6. Validation Function
- Ensure validation is correct and efficient
- Should be monotonic for binary search to work

---

## Problem-Solving Framework

### Step 1: Identify if Binary Search Applies
- Is data sorted? Or can it be sorted?
- Is there a monotonic property?
- Can I eliminate half the search space?

### Step 2: Determine Search Space
- **Array binary search**: [0, n-1]
- **Answer space**: [minimum_possible, maximum_possible]
- **Value range**: [min_value, max_value]

### Step 3: Define the Condition
- What am I searching for exactly?
- First/last occurrence?
- Minimum value that satisfies condition?
- Maximum value that satisfies condition?

### Step 4: Choose the Template
- Exact match
- Left boundary
- Right boundary
- Answer space with validation

### Step 5: Implement and Test
- Test with edge cases
- Empty array, single element
- Target not found
- All elements same
- Min/max values

---

## When NOT to Use Binary Search

1. **Unsorted data** (unless you can sort first and it's worth it)
2. **No monotonic property** (can't eliminate half reliably)
3. **Small dataset** (O(n) might be simpler and fast enough)
4. **Linked list** (no O(1) random access)
5. **Need all occurrences** (unless you find boundaries)
6. **Dynamic data** (frequently changing, might need other structures)
