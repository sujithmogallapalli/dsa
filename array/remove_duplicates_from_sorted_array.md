## Problem
Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same.

## Observations
- You can't use another array to store the non-duplicate elements.
- Return the index up-to which the distinct elements stored.

## Approaches
### Approach 1 - In Place algorithm
- Initialize the index with 0 for storing distinct elements position.
- Traverse the original array from index 1.
- Check if this is different from index - 1 element.
  - If same, continue to next element.
  - If different, increment the index that is storing distinct element position and change the element at that position.
  - Note: 1st element will not be changed and considered as distinct always as it's starting element.
  - return (index of distinct element position + 1)
- Time Complexity - O(n), Space Complexity - O(1)

## Codes
```java
public int removeDuplicates(int[] nums) {
    if (nums.length <= 1) return nums.length;
    int k = 0;
    for (int i = 1; i < nums.length; i++) {
        if (nums[i] != nums[i - 1])
            nums[++k] = nums[i];
    }
    return k + 1;
}
```

## New Learnings
- In place algorithm
