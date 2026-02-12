## Problem
Given an integer array nums and an integer val, remove all occurrences of val in nums in-place. The order of the elements may be changed. Then return the number of elements in nums which are not equal to val.

## Observations
- You can't use another array to store.
- Return the index up-to which the elements without the given element.

## Approaches
### Approach 1 - In Place algorithm
- Initialize the index with 0 for storing distinct elements position.
- Traverse the original array from index 0.
- Check if this is different from given element.
    - If same, continue to next element.
    - If different, increment the index that is storing position and change the element at that position.
    - return (index that is storing position)
- Time Complexity - O(n), Space Complexity - O(1)

## Codes
```java
public int removeElement(int[] nums, int val) {
    if (nums.length == 0) return nums.length;
    int k = 0;
    for (int i = 0; i < nums.length; i++) {
        if (nums[i] != val)
            nums[k++] = nums[i];
    }
    return k;
}
```