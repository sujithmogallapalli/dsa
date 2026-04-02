## Problem
Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

## Sample
Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]

## Observations
- Use In-place algorithm
- Order of non-zero elements shouldn't be changed

## Approaches
### Approach 1 - Two pointer approach
- Initialize left = 0 to store the position of element from left with zero value
- Traverse through the array
  - check if element is non-zero
  - if the traversal is not at same index, perform swap with left pos and current pos.
  - Increment left
- Time complexity - O(n), Space Complexity - O(1)

### Approach 2 - Move non zeroes and fill it with zeroes
- Traverse through the array and move back the non-zero elements to left using a counter
- Traverse through the array from counter and fill with zeroes
- Time complexity - O(n), Space complexity - O(1)

## Codes
### Two pointer Approach
```java
public static void moveZeroes(int[] nums) {
    int left = 0; 
    for (int right = 0; right < nums.length; right++) {
        if (nums[right] != 0) {
            // Only swap if we aren't at the same index
            if (left != right) {
                nums[left] = nums[right];
                nums[right] = 0;
            }
            left++;
        }
    }
}
```
### Move non zeroes and fill it with zeroes
```java
public void moveZeroes(int[] nums) {
    int index = 0;
    for (int i = 0; i < nums.length; i++) {
        if (nums[i] != 0)
            nums[index++] = nums[i];
    }
    for (int i = index; i < nums.length; i++) {
        nums[i] = 0;
    }
}
```