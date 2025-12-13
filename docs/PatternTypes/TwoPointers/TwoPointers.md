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

- ![Easy](https://img.shields.io/badge/Easy-green) Two Sum II - Input Array Is Sorted (LC 167)
- ![Easy](https://img.shields.io/badge/Easy-green) Valid Palindrome (LC 125)
- ![Easy](https://img.shields.io/badge/Easy-green) Move Zeroes (LC 283)
- ![Easy](https://img.shields.io/badge/Easy-green) Remove Duplicates from Sorted Array (LC 26)
- ![Easy](https://img.shields.io/badge/Easy-green) Remove Element (LC 27)
- ![Easy](https://img.shields.io/badge/Easy-green) Reverse String (LC 344)
- ![Easy](https://img.shields.io/badge/Easy-green) Squares of a Sorted Array (LC 977)
- ![Medium](https://img.shields.io/badge/Medium-orange) 3Sum (LC 15)
- ![Medium](https://img.shields.io/badge/Medium-orange) Container With Most Water (LC 11)
- ![Medium](https://img.shields.io/badge/Medium-orange) Remove Duplicates from Sorted Array II (LC 80)
- ![Medium](https://img.shields.io/badge/Medium-orange) Sort Colors (LC 75) - Dutch National Flag
- ![Medium](https://img.shields.io/badge/Medium-orange) Partition List (LC 86)
- ![Medium](https://img.shields.io/badge/Medium-orange) Reverse Words in a String (LC 151)
- ![Medium](https://img.shields.io/badge/Medium-orange) Rotate Array (LC 189)
- ![Medium](https://img.shields.io/badge/Medium-orange) Backspace String Compare (LC 844)
- ![Medium](https://img.shields.io/badge/Medium-orange) Boats to Save People (LC 881)
- ![Hard](https://img.shields.io/badge/Hard-red) Trapping Rain Water (LC 42)
- ![Hard](https://img.shields.io/badge/Hard-red) 4Sum (LC 18)