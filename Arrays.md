# 1.  Count inversions in an array
**Problem Statement:** Given an array of N integers, count the inversion of the array (using [merge-sort](https://takeuforward.org/data-structure/merge-sort-algorithm/)).

What is an inversion of an array? Definition: for all i & j < size of array, if i < j then you have to find pair (A[i],A[j]) such that A[j] < A[i].

**Example 1:**
**Input Format**: N = 5, array[] = {1,2,3,4,5}
**Result**: 0
**Explanation**: we have a sorted array and the sorted array has 0 inversions as for i < j you will never find a pair such that A[j] < A[i]. More clear example: 2 has index 1 and 5 has index 4 now 1 < 5 but 2 < 5 so this is not an inversion.

**Example 2:**
**Input Format**: N = 5, array[] = {5,3,2,1,4}
**Result**: 7
**Explanation**: There are 7 pairs (5,1), (5,3), (5,2), (5,4),(3,2), (3,1), (2,1) and we have left 2 pairs (2,4) and (1,4) as both are not satisfy our condition.


**Solution**:

Brute force approach:
- Compare every element with all the subsequent elements and keep increasing the count if found such a pair (a[i] > a[j] for i < j).
- Time complexity: O(n^2)

Optimal approach:
- Intuition to remember: If there are 2 sorted subarrays {2,3,5} & {1,4} (example 2), we can take 2 pointers i & j, "i" pointing to 1st element of arr1 and "j" pointing to 1st element of arr2.
- Since both arrays are sorted, we can infer that if arr1[i] > arr2[j] then all elements subsequent to arr1[i] will be bigger than arr2[j] and hence we do not need to compare those elements individually with arr2[j]. (We can increase the count by n1-i here & then move j)
