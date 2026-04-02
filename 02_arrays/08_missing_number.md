## Problem
Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.

## Sample
Input: nums = [3,0,1]
Output: 2
Explanation:
n = 3 since there are 3 numbers, so all numbers are in the range [0,3]. 2 is the missing number in the range since it does not appear in nums.

## Observations
- Return 0 if there is no missing number

## Approaches
### Approach 1 - Math based Approach
- Calculate the sum of range from [1, n] using math formula (n * (n + 1)) / 2
- Calculate the sum of given array
- return sumRange - sum
- Time complexity - O(n), Space complexity - O(1)

### Approach 2 - Using sort
- Sort the given array
- if 1st element is not zero, then return 0
- Traverse through the array from 1st index
  - Calculate the diff between current and previous element
  - if it's not equal to 1, return ith index value.
- if last element is missing, finally return length of array
- Time complexity - O(nlogn), Space complexity - O(1)

## Codes
### Math based Approach
```java
public int missingNumber(int[] nums) {
    int n = nums.length;
    int sumReq = n * (n + 1) / 2;
    int sum = 0;
    for (int num : nums) sum += num;
    return sumReq - sum;
}
```
### Using sort
```java
public int missingNumber(int[] nums) {
    Arrays.sort(nums);

    if (nums[0] != 0)
        return 0;
    
    for (int i = 1; i < nums.length; i++) {
        if (nums[i] - nums[i - 1] != 1)
            return i;
    }
    return nums.length;
}
```

## Pitfalls
- When using sort approach, handling the last digit as missing number