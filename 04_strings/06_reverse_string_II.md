## Problem
- Given a string s and an integer k, reverse the first k characters for every 2k characters counting from the start of the string.

## Sample
### Sample 1:
- Input: s = "abcdefg", k = 2
- Output: "bacdfeg"
- Example 2:

### Sample 2:
- Input: s = "abcd", k = 2
- Output: "bacd"

## Observations
- If there are fewer than k characters left, reverse all of them. 
- If there are less than 2k but greater than or equal to k characters, then reverse the first k characters and leave the other as original.

## Approaches
### Approach 1 – Segment-Based Two Pointer Reversal
- Step 1: Convert string into char array.
- Step 2: Traverse string in blocks of size 2k.
- Step 3: For each block:
    - Reverse first k characters.
- Step 4: Use two pointers (left, right) to reverse segment.
- Step 5: Move to next block by increasing index by 2k.
- Step 6: Convert array back to string.
- Time Complexity: O(n), Space Complexity: O(n)  // char array copy

## Codes
### Segment-Based Two Pointer Reversal
```java
public String reverseStr(String s, int k) {

    char[] arr = s.toCharArray();
    int n = arr.length;

    for (int i = 0; i < n; i += 2 * k) {

        int left = i;
        int right = Math.min(i + k - 1, n - 1);

        while (left < right) {
            char temp = arr[left];
            arr[left] = arr[right];
            arr[right] = temp;

            left++;
            right--;
        }
    }

    return new String(arr);
}
```