## Problem
Given an alphanumeric string, find the second-largest numeric digit. 
Return -1 if it doesn’t exist.

## Observations
- Only digits (0-9) possible
- Need distinct second maximum
- Single pass solution possible

## Approaches
### Approach 1: One-pass max tracking (Optimal)
- Track max and second max
- Time: O(n), Space: O(1)

### Approach 2: Reverse digit scan using count
- Check digits from 9 → 0 using indexOf
- Time: O(n), Space: O(1)

## Code
### One-pass max tracking
```java
public int secondHighest(String s) {
    int max = -1, secondMax = -1;

    for (char c : s.toCharArray()) {
        if (Character.isDigit(c)) {
            int digit = c - '0';
            if (digit > max) {
                secondMax = max;
                max = digit;
            } else if (digit < max && digit > secondMax) {
                secondMax = digit;
            }
        }
    }
    return secondMax;
}
```
### Reverse digit scan using count
```java
public int secondHighest(String s) {
    int count = 2;
    for (char ch = '9'; ch >= '0'; ch--) {
        if (s.indexOf(ch) != -1) {
            if (--count == 0) {
                return ch - '0';
            }
        }
    }
    return -1;
}
```

## New Learnings
- Character.isDigit(char c)
  → checks if character is numeric

## Pitfalls
- Forgetting distinct digits.
- Handling the string with one letter length.

