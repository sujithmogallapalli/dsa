## Problem
Merge Sort

## Observations
- Time complexity is same for all cases is O(nlogn)
- Merging uses two-pointer approach

## Approaches
### Approach 1: Divide and Conquer
- Time: O(nlogn), Space: O(n) -> mergedArray

## Code
### Using recursion
```java
public int[] sortArray(int[] nums) {
    if (nums.length == 1) return nums;
    int mid = nums.length / 2;
    int[] left = sortArray(Arrays.copyOfRange(nums, 0, mid));
    int[] right = sortArray(Arrays.copyOfRange(nums, mid, nums.length));
    return merge(left, right);
}

private int[] merge(int[] left, int[] right) {
    int[] mergedArray = new int[left.length + right.length];
    int leftIndex = 0, rightIndex = 0, mergedArrayIndex = 0;
    while (leftIndex < left.length && rightIndex < right.length) {
        mergedArray[mergedArrayIndex++] =
                (left[leftIndex] < right[rightIndex]) ?
                        left[leftIndex++] : right[rightIndex++];
    }
    while (leftIndex < left.length) {
        mergedArray[mergedArrayIndex++] = left[leftIndex++];
    }
    while (rightIndex < right.length) {
        mergedArray[mergedArrayIndex++] = right[rightIndex++];
    }
    return mergedArray;
}
```

## New learnings
- Arrays.copyOfRange()

## Pitfalls
- Forgetting about remaining arrays in left and right arrays after merging.