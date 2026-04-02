## Problem
- You are given a string num, representing a large integer. Return the largest-valued odd integer (as a string) that is a non-empty substring of num, or an empty string "" if no odd integer exists.

## Sample
### Sample 1
- Input: num = "52"
- Output: "5"
- Explanation: The only non-empty substrings are "5", "2", and "52". "5" is the only odd number.

### Sample 2
- Input: num = "4206"
- Output: ""
- Explanation: There are no odd numbers in "4206".

### Sample 3
- Input: num = "35427"
- Output: "35427"
- Explanation: "35427" is already an odd number.

## Approaches
### Approach 1 – Reverse Scan for Rightmost Valid Digit
- Step 1: Start scanning the string from the last character.
- Step 2: Convert the character to a digit.
- Step 3: Check if the digit is odd.
- Step 4: If odd:
    - Return substring from start to that index.
- Step 5: If even:
    - Continue scanning left.
- Step 6: If no odd digit found:
    - Return empty string.
- Time Complexity: O(n), Space Complexity: O(1)

## Codes
### Reverse Scan for Rightmost Valid Digit
```java
public String largestOddNumber(String num) {

    for (int i = num.length() - 1; i >= 0; i--) {
        if ((num.charAt(i) - '0') % 2 != 0) {
            return num.substring(0, i + 1);
        }
    }

    return "";
}
```