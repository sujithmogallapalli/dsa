## Problem
- You're given strings jewels representing the types of stones that are jewels, and stones representing the stones you have. 
- Each character in stones is a type of stone you have. You want to know how many of the stones you have are also jewels.

## Sample
Input: jewels = "aA", stones = "aAAbbbb"
Output: 3

## Observations
- Letters are case-sensitive, so "a" is considered a different type of stone from "A".

## Approaches
### Approach 1 - Boolean Array frequency
- Step 1: Create boolean array of fixed size (ASCII range).
- Step 2: Mark all jewel characters as true.
- Step 3: Traverse stones:
    - If lookup[ch] is true → increment count.
- Step 4: Return count.
- Time Complexity: O(n + m), Space Complexity: O(1)  (Fixed size 128)

### Approach 2 - Brute Force
- Step 1: Iterate through each character in stones.
- Step 2: For each character:
  - Check if it exists in jewels using indexOf().
- Step 3: If yes → increment count.
- Step 4: Return total count.
- Time Complexity: O(n * m), Space Complexity: O(1)

## Codes
### Boolean Array Hashing
```java
public int numJewelsInStones(String jewels, String stones) {

    boolean[] lookup = new boolean[128];  // ASCII size

    // Mark jewels
    for (char ch : jewels.toCharArray()) {
        lookup[ch] = true;
    }

    int count = 0;

    // Count matching stones
    for (char ch : stones.toCharArray()) {
        if (lookup[ch]) {
            count++;
        }
    }

    return count;
}
```
### Brute force
```java
public int numJewelsInStones(String jewels, String stones) {

    int count = 0;

    for (char ch : stones.toCharArray()) {
        if (jewels.indexOf(ch) != -1) {
            count++;
        }
    }

    return count;
}
```

## New Learnings
- Boolean hashing