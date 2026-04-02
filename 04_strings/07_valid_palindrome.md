## Problem
- A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.
- Given a string s, return true if it is a palindrome, or false otherwise.

## Sample
### Sample 1
- Input: s = "A man, a plan, a canal: Panama"
- Output: true 
- Explanation: "amanaplanacanalpanama" is a palindrome.

### Sample 2
- Input: s = " "
- Output: true 
- Explanation: s is an empty string "" after removing non-alphanumeric characters. 
  - Since an empty string reads the same forward and backward, it is a palindrome.

## Approaches
### Approach 1 – Two Pointer Skip & Compare
1. Initialize two pointers:
    - left at start
    - right at end
2. Move left pointer forward until alphanumeric.
3. Move right pointer backward until alphanumeric.
4. Compare characters (case-insensitive).
5. If mismatch → return false.
6. Move both pointers inward.
7. Continue until pointers cross.
- Time Complexity: O(n), Space Complexity: O(1)

### Approach – Filter String Then Compare Symmetrically
- Step 1: Convert the string to lowercase to ignore case differences.
- Step 2: Traverse the string and keep only alphanumeric characters.
    - Use `Character.isLetterOrDigit()` to filter valid characters.
    - Store them in a `StringBuilder`.
- Step 3: Convert the filtered characters into a new clean string.
- Step 4: Compare characters symmetrically:
    - Start from the left.
    - Compute the corresponding right index (`length - left - 1`).
- Step 5: If any pair of characters mismatch → return `false`.
- Step 6: If all pairs match → return `true`.
- Time Complexity: O(n), Space Complexity: O(n)

## Codes
### Two Pointer Skip & Compare
```java
public boolean isPalindrome(String s) {

    int left = 0;
    int right = s.length() - 1;

    while (left < right) {

        while (left < right && !Character.isLetterOrDigit(s.charAt(left))) {
            left++;
        }

        while (left < right && !Character.isLetterOrDigit(s.charAt(right))) {
            right--;
        }

        if (Character.toLowerCase(s.charAt(left)) != 
            Character.toLowerCase(s.charAt(right))) {
            return false;
        }

        left++;
        right--;
    }

    return true;
}
```

### Filter String Then Compare Symmetrically
```java
public boolean isPalindrome(String s) {

    s = s.toLowerCase();
    StringBuilder filtered = new StringBuilder();

    for (char ch : s.toCharArray()) {
        if (Character.isLetterOrDigit(ch)) {
            filtered.append(ch);
        }
    }

    String clean = filtered.toString();

    for (int left = 0; left < clean.length() / 2; left++) {
        int right = clean.length() - left - 1;

        if (clean.charAt(left) != clean.charAt(right))
            return false;
    }

    return true;
}
```

## New Learnings
- Character.isLetterOrDigit()
- Character.toLowerCase()