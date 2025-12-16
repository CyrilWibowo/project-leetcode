# Fast & Slow Pointers Pattern

## What the problem gives you:
- Linked list or array
- Possible cycle
- Need to find middle
- Need to find kth from end

## What the problem requires:
- Detect cycle
- Find cycle start
- Find middle node
- Find kth from end without length

## Data structures needed:
- Two pointers (fast, slow)
- No extra space needed

## Approach:
- Fast moves 2 steps, slow moves 1 step
- If cycle: they meet
- For middle: fast at end → slow at middle

**Time: O(n) | Space: O(1)**

---

## Exclusively Fast & Slow Pointers (Pure Pattern)

### Cycle Detection

- $\color{green}{\textsf{[Easy]}}$ Linked List Cycle (LC 141)
- $\color{orange}{\textsf{[Medium]}}$ Linked List Cycle II (LC 142)
- $\color{green}{\textsf{[Easy]}}$ Happy Number (LC 202)
- $\color{orange}{\textsf{[Medium]}}$ Find the Duplicate Number (LC 287)

### Finding Middle

- $\color{green}{\textsf{[Easy]}}$ Middle of the Linked List (LC 876)
- $\color{green}{\textsf{[Easy]}}$ Palindrome Linked List (LC 234)

### Finding Kth from End

- $\color{green}{\textsf{[Easy]}}$ Remove Nth Node From End of List (LC 19)

### Detecting Patterns

- $\color{orange}{\textsf{[Medium]}}$ Circular Array Loop (LC 457)

---

## Combined with Other Patterns

### Fast & Slow + Linked List Reversal

- $\color{green}{\textsf{[Easy]}}$ Palindrome Linked List (LC 234)
- $\color{orange}{\textsf{[Medium]}}$ Reorder List (LC 143)
- $\color{red}{\textsf{[Hard]}}$ Reverse Nodes in k-Group (LC 25)

### Fast & Slow + Math/Calculation

- $\color{orange}{\textsf{[Medium]}}$ Linked List Cycle II (LC 142)
- $\color{green}{\textsf{[Easy]}}$ Happy Number (LC 202)
- $\color{orange}{\textsf{[Medium]}}$ Find the Duplicate Number (LC 287)

### Fast & Slow + Two Pointers

- $\color{orange}{\textsf{[Medium]}}$ Rotate List (LC 61)
- $\color{orange}{\textsf{[Medium]}}$ Partition List (LC 86)
- $\color{green}{\textsf{[Easy]}}$ Intersection of Two Linked Lists (LC 160)

### Fast & Slow + Array Manipulation

- $\color{orange}{\textsf{[Medium]}}$ Find the Duplicate Number (LC 287)
- $\color{red}{\textsf{[Hard]}}$ First Missing Positive (LC 41)

### Fast & Slow + Cycle Analysis

- $\color{orange}{\textsf{[Medium]}}$ Circular Array Loop (LC 457)
- $\color{orange}{\textsf{[Medium]}}$ Find All Duplicates in an Array (LC 442)

### Fast & Slow + String/Sequence

- $\color{orange}{\textsf{[Medium]}}$ Longest Substring Without Repeating Characters (LC 3)
- $\color{orange}{\textsf{[Medium]}}$ Minimum Size Subarray Sum (LC 209)

### Fast & Slow + Stack

- $\color{green}{\textsf{[Easy]}}$ Remove Nth Node From End of List (LC 19)
- $\color{red}{\textsf{[Hard]}}$ Remove Duplicates from Sorted List II (LC 82)

### Fast & Slow + Hash Set/Map

- $\color{orange}{\textsf{[Medium]}}$ Linked List Cycle II (LC 142)
- $\color{green}{\textsf{[Easy]}}$ Happy Number (LC 202)
- $\color{orange}{\textsf{[Medium]}}$ Find the Duplicate Number (LC 287)

### Fast & Slow + Dummy Node

- $\color{green}{\textsf{[Easy]}}$ Remove Linked List Elements (LC 203)
- $\color{red}{\textsf{[Hard]}}$ Remove Duplicates from Sorted List II (LC 82)
- $\color{green}{\textsf{[Easy]}}$ Merge Two Sorted Lists (LC 21)

### Fast & Slow + Recursion

- $\color{orange}{\textsf{[Medium]}}$ Swap Nodes in Pairs (LC 24)
- $\color{red}{\textsf{[Hard]}}$ Reverse Nodes in k-Group (LC 25)
- $\color{orange}{\textsf{[Medium]}}$ Sort List (LC 148)

### Fast & Slow + Sorting/Merging

- $\color{orange}{\textsf{[Medium]}}$ Sort List (LC 148)
- $\color{orange}{\textsf{[Medium]}}$ Merge In Between Linked Lists (LC 1669)

### Fast & Slow + Binary Search

- $\color{orange}{\textsf{[Medium]}}$ Find the Duplicate Number (LC 287)

### Fast & Slow + Greedy

- $\color{orange}{\textsf{[Medium]}}$ Split Linked List in Parts (LC 725)
- $\color{orange}{\textsf{[Medium]}}$ Odd Even Linked List (LC 328)

---

## Advanced/Variations

### Modified Fast & Slow

- $\color{orange}{\textsf{[Medium]}}$ Delete the Middle Node of a Linked List (LC 2095)
- $\color{orange}{\textsf{[Medium]}}$ Maximum Twin Sum of a Linked List (LC 2130)
- $\color{green}{\textsf{[Easy]}}$ Delete Node in a Linked List (LC 237)

### Triple Pointers (Fast/Mid/Slow)

- $\color{red}{\textsf{[Hard]}}$ Reverse Nodes in k-Group (LC 25)
- $\color{red}{\textsf{[Hard]}}$ Remove Duplicates from Sorted List II (LC 82)

### Fast & Slow in Arrays (Treating as Linked List)

- $\color{orange}{\textsf{[Medium]}}$ Find the Duplicate Number (LC 287)
- $\color{red}{\textsf{[Hard]}}$ First Missing Positive (LC 41)
- $\color{orange}{\textsf{[Medium]}}$ Set Mismatch (LC 645)

### Fast & Slow with Distance

- $\color{green}{\textsf{[Easy]}}$ Remove Nth Node From End of List (LC 19)
- $\color{orange}{\textsf{[Medium]}}$ Rotate List (LC 61)

### Tortoise and Hare Variations

- $\color{orange}{\textsf{[Medium]}}$ Find All Duplicates in an Array (LC 442)
- $\color{orange}{\textsf{[Medium]}}$ Find All Numbers Disappeared in an Array (LC 448)

---

## By Category

### Pure Cycle Detection

- $\color{green}{\textsf{[Easy]}}$ Linked List Cycle (LC 141)
- $\color{orange}{\textsf{[Medium]}}$ Linked List Cycle II (LC 142)
- $\color{green}{\textsf{[Easy]}}$ Happy Number (LC 202)
- $\color{orange}{\textsf{[Medium]}}$ Find the Duplicate Number (LC 287)
- $\color{orange}{\textsf{[Medium]}}$ Circular Array Loop (LC 457)

### Pure Middle Finding

- $\color{green}{\textsf{[Easy]}}$ Middle of the Linked List (LC 876)
- $\color{green}{\textsf{[Easy]}}$ Palindrome Linked List (LC 234)
- $\color{orange}{\textsf{[Medium]}}$ Delete the Middle Node of a Linked List (LC 2095)

### Pure Kth from End

- $\color{green}{\textsf{[Easy]}}$ Remove Nth Node From End of List (LC 19)

### Combined with Reversal

- $\color{green}{\textsf{[Easy]}}$ Palindrome Linked List (LC 234)
- $\color{orange}{\textsf{[Medium]}}$ Reorder List (LC 143)
- $\color{red}{\textsf{[Hard]}}$ Reverse Nodes in k-Group (LC 25)

### Combined with Merge/Sort

- $\color{orange}{\textsf{[Medium]}}$ Sort List (LC 148)
- $\color{orange}{\textsf{[Medium]}}$ Merge In Between Linked Lists (LC 1669)
- $\color{green}{\textsf{[Easy]}}$ Merge Two Sorted Lists (LC 21)

### Array as Linked List

- $\color{orange}{\textsf{[Medium]}}$ Find the Duplicate Number (LC 287)
- $\color{red}{\textsf{[Hard]}}$ First Missing Positive (LC 41)
- $\color{orange}{\textsf{[Medium]}}$ Find All Duplicates in an Array (LC 442)
- $\color{orange}{\textsf{[Medium]}}$ Find All Numbers Disappeared in an Array (LC 448)

---

## Summary by Difficulty

### Easy (Pure Fast & Slow)

- $\color{green}{\textsf{[Easy]}}$ Linked List Cycle (LC 141)
- $\color{green}{\textsf{[Easy]}}$ Happy Number (LC 202)
- $\color{green}{\textsf{[Easy]}}$ Middle of the Linked List (LC 876)
- $\color{green}{\textsf{[Easy]}}$ Remove Nth Node From End of List (LC 19)

### Easy (Combined)

- $\color{green}{\textsf{[Easy]}}$ Palindrome Linked List (LC 234)
- $\color{green}{\textsf{[Easy]}}$ Intersection of Two Linked Lists (LC 160)

### Medium (Pure Fast & Slow)

- $\color{orange}{\textsf{[Medium]}}$ Linked List Cycle II (LC 142)
- $\color{orange}{\textsf{[Medium]}}$ Find the Duplicate Number (LC 287)
- $\color{orange}{\textsf{[Medium]}}$ Circular Array Loop (LC 457)
- $\color{orange}{\textsf{[Medium]}}$ Delete the Middle Node of a Linked List (LC 2095)

### Medium (Combined)

- $\color{orange}{\textsf{[Medium]}}$ Reorder List (LC 143)
- $\color{orange}{\textsf{[Medium]}}$ Sort List (LC 148)
- $\color{orange}{\textsf{[Medium]}}$ Rotate List (LC 61)
- $\color{orange}{\textsf{[Medium]}}$ Odd Even Linked List (LC 328)
- $\color{orange}{\textsf{[Medium]}}$ Remove Duplicates from Sorted List II (LC 82)
- $\color{orange}{\textsf{[Medium]}}$ Swap Nodes in Pairs (LC 24)
- $\color{orange}{\textsf{[Medium]}}$ Split Linked List in Parts (LC 725)
- $\color{orange}{\textsf{[Medium]}}$ Maximum Twin Sum of a Linked List (LC 2130)
- $\color{orange}{\textsf{[Medium]}}$ Merge In Between Linked Lists (LC 1669)
- $\color{orange}{\textsf{[Medium]}}$ Find All Duplicates in an Array (LC 442)
- $\color{orange}{\textsf{[Medium]}}$ Find All Numbers Disappeared in an Array (LC 448)
- $\color{orange}{\textsf{[Medium]}}$ Set Mismatch (LC 645)

### Hard (Pure Fast & Slow)

- None strictly pure

### Hard (Combined)

- $\color{red}{\textsf{[Hard]}}$ Reverse Nodes in k-Group (LC 25)
- $\color{red}{\textsf{[Hard]}}$ First Missing Positive (LC 41)

---

## Quick Recognition Guide

### Use PURE Fast & Slow when:
1. **Cycle detection** in linked list or sequence
2. **Find middle** of linked list without knowing length
3. **Find kth from end** without multiple passes
4. **O(1) space** requirement for linked list problems
5. **Array treated as linked list** (nums[i] = next index)

### Use COMBINED Fast & Slow when:
1. Need middle + additional operation (reverse, merge)
2. Cycle detection + find cycle properties (start, length)
3. Array manipulation using index as pointer
4. Position finding + modification/deletion
5. Sorting linked list (find middle for merge sort)

### Key Indicators:
- "Detect cycle"
- "Find middle node"
- "Kth from end" or "nth from end"
- "Without extra space"
- "Linked list" problems
- "Happy number" or sequence cycle
- "Find duplicate" in array with constraint nums[i] in [1, n]
- "Palindrome linked list"
- "Reorder list"

### Fast vs Slow Speed:
- **Classic (2x)**: Fast moves 2 steps, slow moves 1 step
- **Gap maintaining**: Fast moves k steps ahead, then both move together
- **Custom**: Different speeds based on problem (e.g., one moves every other iteration)

### Common Variations:
1. **Floyd's Cycle Detection**: Detect cycle + find start
2. **Middle Finding**: Fast reaches end → slow at middle
3. **Gap Technique**: Maintain distance k between pointers
4. **Triple Pointers**: Sometimes need prev, slow, fast
5. **Array as List**: Use nums[i] as "next" pointer

---

## Problem Templates

### Template 1: Cycle Detection
```python
def has_cycle(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            return True
    return False
```

### Template 2: Find Middle
```python
def find_middle(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    return slow
```

### Template 3: Kth from End
```python
def remove_nth_from_end(head, n):
    fast = slow = head
    # Move fast n steps ahead
    for _ in range(n):
        fast = fast.next
    # Move both until fast reaches end
    while fast and fast.next:
        slow = slow.next
        fast = fast.next
    # slow is now at (n-1)th from end
    return slow
```

### Template 4: Find Cycle Start (Floyd's)
```python
def detect_cycle(head):
    slow = fast = head
    # Phase 1: Detect cycle
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            # Phase 2: Find start
            slow = head
            while slow != fast:
                slow = slow.next
                fast = fast.next
            return slow
    return None
```

### Template 5: Array as Linked List
```python
def find_duplicate(nums):
    slow = fast = nums[0]
    # Phase 1: Find intersection
    while True:
        slow = nums[slow]
        fast = nums[nums[fast]]
        if slow == fast:
            break
    # Phase 2: Find entrance
    slow = nums[0]
    while slow != fast:
        slow = nums[slow]
        fast = nums[fast]
    return slow
```

---

## Why Fast & Slow Works

### Mathematical Proof (Cycle Detection):
- If there's a cycle, fast will eventually lap slow inside the cycle
- Distance between them decreases by 1 each step (fast gains 1 step)
- They must meet within one cycle length

### Finding Cycle Start:
- When they meet, slow has traveled distance d
- Fast has traveled 2d
- The extra distance (d) is multiple of cycle length
- Resetting one pointer and moving both at same speed finds entrance

### Finding Middle:
- When fast reaches end (travels 2n), slow is at n (middle)
- Even length: slow at first of second half
- Odd length: slow at exact middle

### Kth from End:
- Gap of k maintained between pointers
- When fast reaches end, slow is k from end
- Only one pass needed