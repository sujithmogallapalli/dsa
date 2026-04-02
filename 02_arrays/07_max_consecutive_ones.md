## Problem
Given a binary array nums, return the maximum number of consecutive 1's in the array.

## Sample
Input: nums = [1,1,0,1,1,1]
Output: 3
Explanation: The first two digits or the last three digits are consecutive 1s. The maximum number of consecutive 1s is 3.

## Approaches
### Approach 1 - Single pass counter
- Initialize count = 0, result = 0
- Traverse through the array
  - if element is 1, increment counter
  - if not, count = 0 and take max(count, result)
- Take max(count, result) to check last consecutive 1s count.
- Time complexity - O(n), Space complexity - O(1)

## Codes
### Single pass counter
```java
public int findMaxConsecutiveOnes(int[] nums) {
    int result = 0, count = 0;
    for (int num : nums) {
        if (num != 1) {
            result = Math.max(count, result);
            count = 0;
        } else
            count++;
    }
    result = Math.max(count, result);
    return result;
}
```
## New Learnings
- Name of this approach

## Pitfalls
- Forgetting about the last consecutive count.