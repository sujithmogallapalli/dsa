## Problem
You are given two integer arrays nums1 and nums2, sorted in non-decreasing order, and two integers m and n, representing the number of elements in nums1 and nums2 respectively.

Merge nums1 and nums2 into a single array sorted in non-decreasing order.

The final sorted array should not be returned by the function, but instead be stored inside the array nums1. To accommodate this, nums1 has a length of m + n, where the first m elements denote the elements that should be merged, and the last n elements are set to 0 and should be ignored. nums2 has a length of n.

## Observations
- Don't introduce any new array to store

## Approaches
### Approach 1 - Reverse Two-pointer method
- Start traversing from reverse order (index = m + n -1) and compare values on two arrays.
  - Compare both the values and keep larger one at last.
- Traverse the remaining arrays if the other one is exhausted.
- Time complexity - O(m + n), Space complexity - O(1).

### Approach 2 - Brute force
- Start traversing from beginning (i = 0, j = 0).
  - Compare values and replace the value in 1st array with 2nd array element if it's less than 1st one.
  - Sort the second array.
  - Move pointers accordingly.
- Time complexity - O(n ^ 2), Space complexity - O(1)

## Codes
### Reverse Two-pointer method
```java
public void merge(int[] nums1, int m, int[] nums2, int n) {
    int i = m - 1, j = n - 1, index = m + n - 1;
    while (i >= 0 && j >= 0) {
        if (nums1[i] < nums2[j]) {
            nums1[index--] = nums2[j--];
        }
        else {
            nums1[index--] = nums1[i--];
        }
    }
    while (i >= 0) {
        nums1[index--] = nums1[i--];
    }
    while (j >= 0) {
        nums1[index--] = nums2[j--];
    }
}
```
### Brute force
```java
public void merge(int[] nums1, int m, int[] nums2, int n) {
    int i = 0, j = 0;
    while (i < nums1.length && j < n) {
        if (i >= m) {
            nums1[i] = nums2[j++];
        }
        else if (nums1[i] > nums2[j]) {
            int temp = nums1[i];
            nums1[i] = nums2[j];
            nums2[j] = temp;
            Arrays.sort(nums2);
        }
        i++;
    }
}
```

## New Learnings
- Reverse two pointer approach

## Pitfalls
- Not taking care of filling remaining arrays after one array is exhausted in main loop.