# Sliding Window Pattern

## What the problem gives you:
- Array or string
- Need to examine subarrays/substrings
- Usually contiguous elements

## What the problem requires:
- Find max/min/longest/shortest subarray with property
- All subarrays of size k
- Substring with certain characters

## Data structures needed:
- Hash map (for character/element counts)
- Deque (for min/max in window)
- Variables (for window state)

## Approach:
- Expand right pointer to grow window
- Shrink left pointer when condition violated
- Track best result

## Common variations:
- Fixed: window size is given
- Variable: find optimal size

**Time: O(n) | Space: O(k) for hash map**

---

## Exclusively Sliding Window (Pure Pattern)
These problems use ONLY the sliding window technique as the main solution approach.

### Fixed Window Size

- $\color{green}{\textsf{[Easy]}}$ Maximum Average Subarray I (LC 643)
- $\color{orange}{\textsf{[Medium]}}$ Grumpy Bookstore Owner (LC 1052)
- $\color{orange}{\textsf{[Medium]}}$ Maximum Points You Can Obtain from Cards (LC 1423)
- $\color{orange}{\textsf{[Medium]}}$ Find All Anagrams in a String (LC 438)
- $\color{orange}{\textsf{[Medium]}}$ Permutation in String (LC 567)
- $\color{red}{\textsf{[Hard]}}$ Sliding Window Maximum (LC 239)
- $\color{red}{\textsf{[Hard]}}$ Minimum Window Subsequence (LC 727)

### Variable Window Size

- $\color{green}{\textsf{[Easy]}}$ Maximum Sum of Distinct Subarrays With Length K (LC 2461)
- $\color{orange}{\textsf{[Medium]}}$ Longest Substring Without Repeating Characters (LC 3)
- $\color{orange}{\textsf{[Medium]}}$ Longest Repeating Character Replacement (LC 424)
- $\color{orange}{\textsf{[Medium]}}$ Max Consecutive Ones III (LC 1004)
- $\color{orange}{\textsf{[Medium]}}$ Fruit Into Baskets (LC 904)
- $\color{orange}{\textsf{[Medium]}}$ Subarray Product Less Than K (LC 713)
- $\color{orange}{\textsf{[Medium]}}$ Number of Substrings Containing All Three Characters (LC 1358)
- $\color{orange}{\textsf{[Medium]}}$ Longest Substring with At Most K Distinct Characters (LC 340)
- $\color{orange}{\textsf{[Medium]}}$ Longest Substring with At Most Two Distinct Characters (LC 159)
- $\color{orange}{\textsf{[Medium]}}$ Get Equal Substrings Within Budget (LC 1208)
- $\color{orange}{\textsf{[Medium]}}$ Count Number of Nice Subarrays (LC 1248)
- $\color{orange}{\textsf{[Medium]}}$ Binary Subarrays With Sum (LC 930)
- $\color{red}{\textsf{[Hard]}}$ Subarrays with K Different Integers (LC 992)

---

## Combined with Other Patterns

### Sliding Window + Hash Map

- $\color{green}{\textsf{[Easy]}}$ Contains Duplicate II (LC 219)
- $\color{orange}{\textsf{[Medium]}}$ Minimum Window Substring (LC 76)
- $\color{orange}{\textsf{[Medium]}}$ Find All Anagrams in a String (LC 438)
- $\color{orange}{\textsf{[Medium]}}$ Longest Substring Without Repeating Characters (LC 3)
- $\color{orange}{\textsf{[Medium]}}$ Longest Repeating Character Replacement (LC 424)
- $\color{orange}{\textsf{[Medium]}}$ Fruit Into Baskets (LC 904)
- $\color{orange}{\textsf{[Medium]}}$ Longest Substring with At Most K Distinct Characters (LC 340)
- $\color{orange}{\textsf{[Medium]}}$ Subarrays with K Different Integers (LC 992)
- $\color{orange}{\textsf{[Medium]}}$ Subarray Sum Equals K (LC 560)
- $\color{red}{\textsf{[Hard]}}$ Substring with Concatenation of All Words (LC 30)
- $\color{red}{\textsf{[Hard]}}$ Minimum Window Substring (LC 76)

### Sliding Window + Two Pointers

- $\color{orange}{\textsf{[Medium]}}$ Container With Most Water (LC 11)
- $\color{orange}{\textsf{[Medium]}}$ Longest Mountain in Array (LC 845)
- $\color{orange}{\textsf{[Medium]}}$ 3Sum (LC 15)
- $\color{orange}{\textsf{[Medium]}}$ 4Sum (LC 18)
- $\color{red}{\textsf{[Hard]}}$ Trapping Rain Water (LC 42)

### Sliding Window + Deque (Monotonic Queue)

- $\color{orange}{\textsf{[Medium]}}$ Longest Continuous Subarray With Absolute Diff Less Than or Equal to Limit (LC 1438)
- $\color{red}{\textsf{[Hard]}}$ Sliding Window Maximum (LC 239)
- $\color{red}{\textsf{[Hard]}}$ Shortest Subarray with Sum at Least K (LC 862)
- $\color{red}{\textsf{[Hard]}}$ Constrained Subsequence Sum (LC 1425)

### Sliding Window + Prefix Sum

- $\color{orange}{\textsf{[Medium]}}$ Subarray Sum Equals K (LC 560)
- $\color{orange}{\textsf{[Medium]}}$ Continuous Subarray Sum (LC 523)
- $\color{orange}{\textsf{[Medium]}}$ Subarray Sums Divisible by K (LC 974)
- $\color{orange}{\textsf{[Medium]}}$ Maximum Size Subarray Sum Equals k (LC 325)
- $\color{orange}{\textsf{[Medium]}}$ Minimum Size Subarray Sum (LC 209)

### Sliding Window + String Matching

- $\color{orange}{\textsf{[Medium]}}$ Find All Anagrams in a String (LC 438)
- $\color{orange}{\textsf{[Medium]}}$ Permutation in String (LC 567)
- $\color{orange}{\textsf{[Medium]}}$ Repeated DNA Sequences (LC 187)
- $\color{red}{\textsf{[Hard]}}$ Minimum Window Substring (LC 76)
- $\color{red}{\textsf{[Hard]}}$ Substring with Concatenation of All Words (LC 30)

### Sliding Window + Greedy

- $\color{orange}{\textsf{[Medium]}}$ Gas Station (LC 134)
- $\color{orange}{\textsf{[Medium]}}$ Jump Game II (LC 45)
- $\color{orange}{\textsf{[Medium]}}$ Partition Labels (LC 763)
- $\color{orange}{\textsf{[Medium]}}$ Maximum Number of Vowels in a Substring of Given Length (LC 1456)

### Sliding Window + Binary Search

- $\color{orange}{\textsf{[Medium]}}$ Minimum Size Subarray Sum (LC 209)
- $\color{red}{\textsf{[Hard]}}$ Kth Smallest Subarray Sum (LC 1918)
- $\color{red}{\textsf{[Hard]}}$ Maximum Number of Robots Within Budget (LC 2398)

### Sliding Window + Stack

- $\color{orange}{\textsf{[Medium]}}$ Sum of Subarray Minimums (LC 907)
- $\color{orange}{\textsf{[Medium]}}$ Sum of Subarray Ranges (LC 2104)
- $\color{red}{\textsf{[Hard]}}$ Largest Rectangle in Histogram (LC 84)

### Sliding Window + DP

- $\color{orange}{\textsf{[Medium]}}$ Longest Turbulent Subarray (LC 978)
- $\color{red}{\textsf{[Hard]}}$ Distinct Subsequences II (LC 940)
- $\color{red}{\textsf{[Hard]}}$ Number of Subarrays with Bounded Maximum (LC 795)

### Sliding Window + Bit Manipulation

- $\color{orange}{\textsf{[Medium]}}$ Maximum XOR of Two Numbers in an Array (LC 421)
- $\color{orange}{\textsf{[Medium]}}$ Bitwise ORs of Subarrays (LC 898)

### Sliding Window + Sorting

- $\color{green}{\textsf{[Easy]}}$ Max Consecutive Ones (LC 485)
- $\color{orange}{\textsf{[Medium]}}$ Longest Continuous Increasing Subsequence (LC 674)
- $\color{orange}{\textsf{[Medium]}}$ Max Consecutive Ones II (LC 487)

### Sliding Window + Counting

- $\color{green}{\textsf{[Easy]}}$ Valid Palindrome (LC 125)
- $\color{orange}{\textsf{[Medium]}}$ Longest Substring with At Least K Repeating Characters (LC 395)
- $\color{orange}{\textsf{[Medium]}}$ Replace the Substring for Balanced String (LC 1234)
- $\color{orange}{\textsf{[Medium]}}$ Count Complete Subarrays in an Array (LC 2799)

### Sliding Window + Matrix/2D

- $\color{orange}{\textsf{[Medium]}}$ Maximal Square (LC 221)
- $\color{red}{\textsf{[Hard]}}$ Max Sum of Rectangle No Larger Than K (LC 363)

---

## Special Variations

### Sliding Window with Multiple Conditions

- $\color{red}{\textsf{[Hard]}}$ Minimum Number of K Consecutive Bit Flips (LC 995)
- $\color{red}{\textsf{[Hard]}}$ Minimum Number of Flips to Make Binary String Alternating (LC 1888)

### Sliding Window with Optimization

- $\color{orange}{\textsf{[Medium]}}$ Maximize the Confusion of an Exam (LC 2024)
- $\color{orange}{\textsf{[Medium]}}$ Frequency of the Most Frequent Element (LC 1838)
- $\color{orange}{\textsf{[Medium]}}$ Longest Nice Subarray (LC 2401)

### Caterpillar/Two-Pass Sliding Window

- $\color{orange}{\textsf{[Medium]}}$ Bags of Tokens (LC 948)
- $\color{orange}{\textsf{[Medium]}}$ Minimum Swaps to Group All 1's Together (LC 1151)
- $\color{orange}{\textsf{[Medium]}}$ Minimum Swaps to Group All 1's Together II (LC 2134)

---

## Quick Recognition Guide

### Use PURE Sliding Window when:
- Fixed or variable window size problems
- Need to track contiguous subarray/substring
- Can expand/shrink window with simple conditions
- O(n) time with window pointer movements

### Use COMBINED Sliding Window when:
- Need to track frequency/counts → Add Hash Map
- Need min/max in window → Add Deque/Monotonic Queue
- Window condition involves sums → Add Prefix Sum
- Multiple pointers needed → Add Two Pointers
- Need to optimize window size → Add Binary Search
- Complex validation logic → Add appropriate data structure

### Key Indicators:
- "Longest/shortest subarray/substring"
- "All subarrays with property X"
- "At most k" or "Exactly k"
- "Contiguous"
- "Window of size k"
- "Maximum/minimum in each window"
