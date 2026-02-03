## Problem
Given an integer n, return true if it is a power of two. Otherwise, return false.

## Observations
- 2^k can't be negative, so it's always false
- n == 0, return false;

## Approaches
### Approach 1: Using bit manipulation
- As 2^k numbers always have single '1', n & n-1 will be 0 always
- Time Complexity: O(1), Space Complexity: O(1)

### Approach 2: Using recursion
- Base Case: n == 1 → true
  Invalid Case: n < 1 or n % 2 != 0 → false
  Recursive Case: isPowerOfTwo(n / 2)
- Time Complexity: O(logn), Space complexity: O(logn) (recursive calls)

## Code
### Using bit manipulation
```java
public boolean isPowerOfTwo(int n) {
    return n > 0 && (n & (n - 1)) == 0;
}
```
### Using recursion
```java
public boolean isPowerOfTwo(int n) {
     if (n <= 0) 
        return false;
    if (n %2 != 0 && n != 1)
        return false;
    else if 
        (n == 1) return true;
    return isPowerOfTwo(n / 2);
}
```

## New Learnings
- Bit manipulation of power of two integers

## Pitfalls
- Not handling negative numbers
- Handling 0 and 1 numbers in recursion