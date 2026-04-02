## Problem
- Given a string s consisting of words and spaces, return the length of the last word in the string.

## Sample
Input: s = "   fly me   to   the moon  "
Output: 4
Explanation: The last word is "moon" with length 4.

## Approaches
### Approach 1 – Reverse Traversal (Backward Scan)
- Step 1: Start from end of string.
- Step 2: Skip trailing spaces.
- Step 3: Count characters until:
    - Start of string OR
    - A space is found.
- Step 4: Return count.
- Time Complexity: O(n), Space Complexity: O(1)

## Codes
### Reverse Traversal (Backward Scan)
```java
public int lengthOfLastWord(String s) {

    int length = 0;
    int i = s.length() - 1;

    // Skip trailing spaces
    while (i >= 0 && s.charAt(i) == ' ') {
        i--;
    }

    // Count last word characters
    while (i >= 0 && s.charAt(i) != ' ') {
        length++;
        i--;
    }

    return length;
}
```

## Pitfalls
- Handling when the string is having only one word or with only spaces