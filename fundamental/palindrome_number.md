## Problem
Given an integer, return true if it is palindrome, and false otherwise

## Observations
- Don't convert the integer into String
- if the number is negative and if it's multiples of 10, then it's no palindrome

## Approaches
### Approach 1: Reverse Half + Two-Pointer (Number Version) (Optimal)
- Validates if orgNum is greater than revNum
- Time: O(n), Space: O(1)

### Approach 2: One-pass to process the palindrome
- Takes remainder in reverse and process the palindrome
- Time: O(n), Space: O(1)

## Code
### Reverse Half + Two-Pointer (Number Version)
```java
public boolean isPalindrome(int x) {
    if (x < 0 || (x % 10 == 0 && x!= 0))
        return false;

    int orgNum = x;
    int revNum = 0;
    while (orgNum > revNum) {
        revNum = (revNum * 10) + (orgNum%10);
        orgNum = orgNum/10;
    }

    return (orgNum == revNum || (orgNum == (revNum/10)));
}
```
### One-pass to process the palindrome
```java
public boolean isPalindrome(int x) {
    if (x < 0)
        return false;

    int orgNum = x;
    int revNum = 0;
    while (x > 0) {
        revNum = (revNum * 10) + (x%10);
        x = x/10;
    }

    return orgNum == revNum;
}
```

## Pitfalls
- 0 is a multiple of 10 and also a palindrome