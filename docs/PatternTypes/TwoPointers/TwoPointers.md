# Two Pointers Pattern

## What the problem gives you:
- Array or string
- Often sorted or need to sort
- Need to find pairs/triplets
- Or need to partition/rearrange

## What the problem requires:
- Find pair with property
- Remove duplicates in-place
- Partition around condition
- Reverse or rearrange

## Data structures needed:
- Array (given)
- Maybe hash set for duplicates

## Approach:
- Set left = 0, right = n-1 (or both at 0)
- Move pointers based on condition
- Shrink window or expand as needed

## Common variations:
- Opposite ends (Two Sum II)
- Same direction (Remove duplicates)
- Fast/slow (Linked list cycle)

**Time: O(n) | Space: O(1)**

---

## Exclusively Two Pointers (Pure Pattern)
These problems use ONLY the two pointer technique as the main solution approach.

- $\color{green}{\textsf{[Easy]}}$ Two Sum II - Input Array Is Sorted (LC 167)
- $\color{green}{\textsf{[Easy]}}$ Valid Palindrome (LC 125)
- $\color{green}{\textsf{[Easy]}}$ Move Zeroes (LC 283)
- $\color{green}{\textsf{[Easy]}}$ Remove Duplicates from Sorted Array (LC 26)
- $\color{green}{\textsf{[Easy]}}$ Remove Element (LC 27)
- $\color{green}{\textsf{[Easy]}}$ Reverse String (LC 344)
- $\color{green}{\textsf{[Easy]}}$ Squares of a Sorted Array (LC 977)
- $\color{orange}{\textsf{[Medium]}}$ 3Sum (LC 15)
- $\color{orange}{\textsf{[Medium]}}$ Container With Most Water (LC 11)
- $\color{orange}{\textsf{[Medium]}}$ Remove Duplicates from Sorted Array II (LC 80)
- $\color{orange}{\textsf{[Medium]}}$ Sort Colors (LC 75) - Dutch National Flag
- $\color{orange}{\textsf{[Medium]}}$ Partition List (LC 86)
- $\color{orange}{\textsf{[Medium]}}$ Reverse Words in a String (LC 151)
- $\color{orange}{\textsf{[Medium]}}$ Rotate Array (LC 189)
- $\color{orange}{\textsf{[Medium]}}$ Backspace String Compare (LC 844)
- $\color{orange}{\textsf{[Medium]}}$ Boats to Save People (LC 881)
- $\color{red}{\textsf{[Hard]}}$ Trapping Rain Water (LC 42)
- $\color{red}{\textsf{[Hard]}}$ 4Sum (LC 18)