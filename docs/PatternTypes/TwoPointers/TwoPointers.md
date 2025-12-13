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

<span style="color:green">[Easy]</span> Two Sum II - Input Array Is Sorted (LC 167)
<span style="color:green">[Easy]</span> Valid Palindrome (LC 125)
<span style="color:green">[Easy]</span> Move Zeroes (LC 283)
<span style="color:green">[Easy]</span> Remove Duplicates from Sorted Array (LC 26)
<span style="color:green">[Easy]</span> Remove Element (LC 27)
<span style="color:green">[Easy]</span> Reverse String (LC 344)
<span style="color:green">[Easy]</span> Squares of a Sorted Array (LC 977)
<span style="color:orange">[Medium]</span> 3Sum (LC 15)
<span style="color:orange">[Medium]</span> Container With Most Water (LC 11)
<span style="color:orange">[Medium]</span> Remove Duplicates from Sorted Array II (LC 80)
<span style="color:orange">[Medium]</span> Sort Colors (LC 75) - Dutch National Flag
<span style="color:orange">[Medium]</span> Partition List (LC 86)
<span style="color:orange">[Medium]</span> Reverse Words in a String (LC 151)
<span style="color:orange">[Medium]</span> Rotate Array (LC 189)
<span style="color:orange">[Medium]</span> Backspace String Compare (LC 844)
<span style="color:orange">[Medium]</span> Boats to Save People (LC 881)
<span style="color:red">[Hard]</span> Trapping Rain Water (LC 42)
<span style="color:red">[Hard]</span> 4Sum (LC 18)