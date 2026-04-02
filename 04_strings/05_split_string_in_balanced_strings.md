## Problem
- Balanced strings are those that have an equal quantity of 'L' and 'R' characters. 
- Given a balanced string s, split it into some number of substrings such that:
    - Each substring is balanced.
- Return the maximum number of balanced strings you can obtain.

## Sample
### Sample 1
- Input: s = "RLRRLLRLRL"
- Output: 4
- Explanation: s can be split into "RL", "RRLL", "RL", "RL", each substring contains same number of 'L' and 'R'.

### Sample 2
- Input: s = "RLRRRLLRLL"
- Output: 2 
- Explanation: s can be split into "RL", "RRRLLRLL", each substring contains same number of 'L' and 'R'. 
  - Note that s cannot be split into "RL", "RR", "RL", "LR", "LL", because the 2nd and 5th substrings are not balanced.

## Observations
- s is a balanced string.

## Approaches
### Approach 1 – Greedy Balance Tracking
- Step 1: Initialize balance = 0.
- Step 2: Traverse the string.
- Step 3: If 'R' → balance++
- Step 4: If 'L' → balance--
- Step 5: Whenever balance becomes 0:
    - One balanced substring found.
    - Increment count.
- Step 6: Return count.
- Time Complexity: O(n), Space Complexity: O(1)

## Codes
### Greedy Balance Tracking
```java
public int balancedStringSplit(String s) {

    int balance = 0;
    int count = 0;

    for (char ch : s.toCharArray()) {

        if (ch == 'R')
            balance++;
        else
            balance--;

        if (balance == 0)
            count++;
    }

    return count;
}
```

## New Learnings
- Using balance counter instead of having two counters