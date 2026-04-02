## Problem
Given a signed 32-bit integer, return it with its digits reversed. 
If reversing causes the value to go outside the signed 32-bit integer range [-2^31, 2^31 - 1], then return 0.

## Observations
- Reversed value shouldn't be below Integer.MIN_VALUE and not above Integer.MAX_VALUE
- Input value should be 32-bit integer.

## Approaches
### Approach 1: Threshold-based overflow check
- Validates the reverse number on each pass using threshold values
  - Integer.MAX_VALUE / 10, Integer.MIN_VALUE / 10
- Time Complexity: O(n), Space Complexity: O(1)

### Approach 2: Handling NumberFormatException
- Uses NumberFormatException to handle the overflow values.
- Time Complexity: O(n), Space Complexity: O(n) -> storing chars in StringBuilder

### Approach 3: long-based overflow check (Not valid approach according to given condition)
- Uses long datatype to store the reverse integer and checks directly with MAX_VALUE or MIN_VALUE
- Time Complexity: O(n), Space Complexity: O(1)

## Codes
### Threshold-based overflow check
```java
public int reverse(int x) {
    int maxBeforeOverflow = Integer.MAX_VALUE / 10;
    int minBeforeUnderflow = Integer.MIN_VALUE / 10;

    int revNum = 0;
    while (x != 0) {
        int lastDigit = x % 10;
        if (revNum < minBeforeUnderflow || revNum > maxBeforeOverflow)
            return 0;

        revNum = revNum * 10 + lastDigit;
        x /= 10;
    }
    return revNum;
}
```
### Handling NumberFormatException
```java
public int reverse(int x) {
    String orgNumInString = String.valueOf(Math.abs(x));
    StringBuilder revNumInString = new StringBuilder();
    int revNum;
    try{
        for (int i = orgNumInString.length() - 1; i >= 0 ; i--) {
            revNumInString.append(orgNumInString.charAt(i));
        }
        revNum = Integer.parseInt(revNumInString.toString());
        if (x < 0)
            revNum = -revNum;
    }
    catch (NumberFormatException ex) {
        return 0;
    }
    return revNum;
}
```
### long-based overflow check (Not valid approach according to given condition)
```java
public int reverse(int x) {
    int orgNum = Math.abs(x);
    long revNum = 0;
    while (orgNum > 0) {
        revNum = (revNum * 10) + orgNum % 10;
        orgNum = orgNum / 10;
    }
    if (x < 0)
        revNum = -revNum;
    if (revNum < Integer.MIN_VALUE || revNum > Integer.MAX_VALUE)
        return 0;
    return (int) revNum;
}
```

## New Learnings
- Using thresholds to check the 32-bit signed or not.
- Math.abs() → ease of use for negative values
- NumberFormatException → Occurs while converting a integer if it exceeds MAX or MIN values