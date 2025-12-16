# Valid Palindrome
# Leetcode 125

A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string s, return true if it is a palindrome, or false otherwise.



Example 1:

Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.

Example 2:

Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.

Example 3:

Input: s = " "
Output: true
Explanation: s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.



Constraints:

    1 <= s.length <= 2 * 105
    s consists only of printable ASCII characters.




# Input is a string (can be treated as an array)
# Recognise for palindromes we need to compare the front and the end with a specific condition (==)
# -> Two pointers

# Notes
# Capital doesnt matter
# Only Alphanumeric

class Solution(object):
    def isPalindrome(self, s):
        l, r = 0, len(s) - 1
        while l < r:
            # Increment left
            while not s[l].isalnum() and l < r:
                l += 1
            # Increment right
            while not s[r].isalnum() and l < r:
                r -= 1
            # Check false
            if s[l].lower() != s[r].lower():
                return False

            l += 1
            r -= 1
        return True