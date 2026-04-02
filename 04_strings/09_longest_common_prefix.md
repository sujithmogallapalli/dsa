## Problem
- Write a function to find the longest common prefix string amongst an array of strings.
- If there is no common prefix, return an empty string "".

## Samples
### Sample 1
- Input: strs = ["flower","flow","flight"]
- Output: "fl"

### Sample 2
- Input: strs = ["dog","racecar","car"]
- Output: ""
- Explanation: There is no common prefix among the input strings.

### Sample 3
- Input: strs = ["c","acc","ccc"]
- Output ""

## Approaches
### Approach 1 – Prefix Reduction (Horizontal Scanning)
- Step 1: Assume first string is the prefix.
- Step 2: Compare prefix with each string.
- Step 3: While the current string does not start with prefix:
    - Remove the last character of prefix.
- Step 4: Continue for all strings.
- Step 5: The remaining prefix is the longest common prefix.
- Time Complexity: O(n × m), Space Complexity: O(1)

### Approach 2 – Shortest String Reference (Vertical Comparison)
- Step 1: Assume the first string as the shortest reference string.
- Step 2: Traverse the array to find the actual shortest string (`minStr`).
- Step 3: Initialize `prefixLength` as the length of the shortest string.
- Step 4: Compare every other string with the shortest string:
    - Start comparing characters from index `0`.
    - Continue until characters mismatch or prefix limit is reached.
- Step 5: Update `prefixLength` to the number of matching characters.
- Step 6: After checking all strings, return the substring of `minStr`
  from `0` to `prefixLength`.
- Time Complexity: O(n × m), Space Complexity: O(1)

## Codes
###  Prefix Reduction (Horizontal Scanning)
```java
public String longestCommonPrefix(String[] strs) {
    String prefix = strs[0];
    for (int i = 1; i < strs.length; i++) {
        while (!strs[i].startsWith(prefix)) {
            prefix = prefix.substring(0, prefix.length() - 1);
        }
        if (prefix.isEmpty())
            return prefix;
    }
    return prefix;
}
```

### Shortest String Reference (Vertical Comparison)
```java
public String longestCommonPrefix(String[] strs) {

    String minStr = strs[0];

    // Find shortest string
    for (String str : strs) {
        if (str.length() < minStr.length()) {
            minStr = str;
        }
    }

    int prefixLength = minStr.length();

    for (String str : strs) {

        int j = 0;
        while (j < prefixLength && str.charAt(j) == minStr.charAt(j)) {
            j++;
        }

        prefixLength = j;
    }

    return minStr.substring(0, prefixLength);
}
```

## New Learnings
- startsWith()