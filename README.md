# Find-the-First-Missing-Positive-Integer
Given an unsorted array of integers nums, return the smallest missing positive integer.  You must solve this problem in O(n) time and use O(1) extra space.
Explanation: First Missing Positive Integer (Cyclic Sort Approach)
Understanding the Problem
We need to find the smallest missing positive integer in an unsorted array while maintaining an O(n) time complexity and O(1) space complexity.

Observations
The missing number must be between 1 and n+1, where n is the array size.

If all numbers from 1 to n exist in the array, the answer is n+1.
Otherwise, the missing number is the first missing one in the range [1, n].
We can ignore negative numbers and numbers greater than n because they do not affect the answer.

Approach: Cyclic Sort
We rearrange the numbers so that each number is placed at its correct index (i.e., nums[i] = i + 1 if possible).

Steps to Solve the Problem
Iterate through the array:

If nums[i] is in the range [1, n] and not already at its correct position (nums[nums[i] - 1] != nums[i]), swap it with nums[nums[i] - 1].
Repeat swapping until every valid number is in its correct place.
Find the missing positive number:

Scan the array. If nums[i] != i + 1, return i + 1.
If all numbers are in the correct position, return n + 1.

Example 1
Input:
nums = [3, 4, -1, 1]
Step 1: Rearranging using swaps

makefile
Initial:   [3, 4, -1, 1]
Swap 3 ↔ -1 → [-1, 4, 3, 1]
Swap 1 ↔ -1 → [1, 4, 3, -1]
Swap 4 ↔ -1 → [1, -1, 3, 4]
Now, numbers 1 and 3 are in the correct place, but 2 is missing.

Step 2: Identify the missing positive

Index:   0  1  2  3
Nums:    1 -1  3  4
nums[1] ≠ 2 → Missing number is 2.
Output: 2

Time and Space Complexity Analysis
Time Complexity: O(n)
Each number is swapped at most once, leading to O(n).
Space Complexity: O(1)
We sort the array in-place without extra space.
