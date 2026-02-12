## Problem
Write a function that reverses a string. The input string is given as an array of characters s.

## Observations
- You can't use another array to store.

## Approaches
### Approach 1 - In Place algorithm using two pointer approach
- Traverse the array from index 0 to n / 2;
- For each increment
  - store the ith index to temp
  - replace ith index char with (n - i)th index char
  - replace (n - i)th index with temp value
- Time Complexity - O(n), Space Complexity - O(1)

## Codes
```java
public void reverseString(char[] s) {
    if (s.length <= 1) return;
    int k = 0;
    for (int i = 0; i < s.length / 2; i++) {
        char temp = s[i];
        s[i] = s[s.length - i - 1];
        s[s.length - i - 1] = temp;
    }
}
```