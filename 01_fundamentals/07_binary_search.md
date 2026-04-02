## Problem
Given an array of integers in ascending order, search the given target using binary search.

## Observations
- Array should be sorted.
- Return -1 if not found
- If we got unsorted array, time complexity will be O(nlogn)

## Approaches
### Approach 1: Using recursion
- Time: O(logn), Space: O(logn)

### Approach 2: Using while loop
- Time: O(logn), Space: O(1)

## Code
### Using recursion
```java
public int search(int[] nums, int target) {
    return search(nums, target, 0, nums.length - 1);
}
private int search(int[] arr, int target, int start, int end) {
    int mid = (start + end) / 2;
    if (arr[mid] == target) return mid;
    if (start == end) return -1;
    if (arr[mid] < target)
        return search(arr, target, mid + 1, end);
    return search(arr, target, start, mid);
}
```
### Using while loop
```java
public int search(int[] nums, int target) {
    int low = 0, high = nums.length - 1;
    while (low <= high) {
        int mid = (low + high) / 2;
        if (nums[mid] == target)
            return mid;
        if (nums[mid] < target) {
            low = mid + 1;
        }
        else {
            high = mid - 1;
        }
    }
    return -1;
}
```
## New learnings
- Recursive calls results in space complexity.

## Pitfalls
- Handle the not found case clearly in recursive approach.