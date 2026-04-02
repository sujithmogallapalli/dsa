## Problem
Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.

## Sample
Input: nums = [4,1,2,1,2]
Output: 4

## Observations
- If array size is 1, then return 0th element

## Approaches
### Approach 1 - Using XOR
- Assign singleNumber = 0
- Traverse through array
  - Assign singleNumber xor ith element to singleNumber
- return singleNumber
- Time complexity - O(n), Space complexity - O(1)

### Approach 2 - Brute force approach using HashMap
- Initialize a hashMap
- Traverse through array and maintain count using hashing technique
- Traverse through hashMap and return the key with count as 1
- Time Complexity: O(n), Space Complexity: O(n)

## Codes
### Using XOR
```java
public int singleNumber(int[] nums) {
    int singleNum = 0;
    for (int num : nums)
        singleNum = (singleNum ^ num);
    return singleNum;
}
```
### Brute force approach using HashMap
```java
public int singleNumber(int[] nums) {
    Map<Integer, Integer> hashes = new HashMap<>();
    for (int num : nums) {
        hashes.put(num, hashes.getOrDefault(num, 0) + 1);
    }
    return hashes.entrySet().stream()
                .filter(ele -> ele.getValue() == 1)
                .findFirst()
                .get()
                .getKey();
}
```

## New Learnings
- XOR operator of same numbers gives 0
- getOrDefault(num, defaultValue);
- Map iteration using stream
  - hashes.entrySet().stream()
    .filter(ele -> ele.getValue() == 1)
    .findFirst()
    .get()
    .getKey()