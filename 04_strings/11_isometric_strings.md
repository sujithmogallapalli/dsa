## Problem
- Given two strings s and t, determine if they are isomorphic.
- Two strings s and t are isomorphic if the characters in s can be replaced to get t.

## Samples
### Sample 1
- Input: s = "egg", t = "add"
- Output: true
- Explanation:
  - The strings s and t can be made identical by:
  - Mapping 'e' to 'a'.
  - Mapping 'g' to 'd'.

### Sample 2
- Input: s = "f11", t = "b23"
- Output: false
- Explanation:
  - The strings s and t can not be made identical as '1' needs to be mapped to both '2' and '3'.

### Sample 3
- Input: s = "bbbaaaba", t = "aaabbbba"
- Output: false

## Observations
- All occurrences of a character must be replaced with another character while preserving the order of characters. 
- No two characters may map to the same character, but a character may map to itself.

## Approaches
### Approach 1 – Last Seen Index Pattern
- Step 1: Create two arrays to track the last seen index of characters.
- Step 2: Traverse both strings simultaneously.
- Step 3: For each character pair:
    - Compare last seen index values.
- Step 4: If they differ → mapping conflict → return false.
- Step 5: Update last seen index for both characters.
- Step 6: If traversal completes → strings are isomorphic.
- Time Complexity: O(n), Space Complexity: O(1)

### Approach 2 – Bidirectional Character Mapping
- Step 1: If the string lengths differ → return false.
- Step 2: Maintain two mappings:
  - mapST → character mapping from s → t
  - mapTS → character mapping from t → s
- Step 3: Traverse both strings simultaneously.
- Step 4: For each index:
  - If an existing mapping conflicts → return false.
- Step 5: Otherwise store the mapping.
- Step 6: If traversal finishes → strings are isomorphic.
- Time Complexity: O(n), Space Complexity: O(k)

## Codes
### Last Seen Index Pattern
```java
public boolean isIsomorphic(String s, String t) {

    int[] mapS = new int[256];
    int[] mapT = new int[256];

    for (int i = 0; i < s.length(); i++) {

        char c1 = s.charAt(i);
        char c2 = t.charAt(i);

        if (mapS[c1] != mapT[c2])
            return false;

        mapS[c1] = i + 1;
        mapT[c2] = i + 1;
    }

    return true;
}
```
### Bidirectional Character Mapping
```java
  public boolean isIsomorphic(String s, String t) {

      if (s.length() != t.length())
          return false;

      Map<Character, Character> mapST = new HashMap<>();
      Map<Character, Character> mapTS = new HashMap<>();

      for (int i = 0; i < s.length(); i++) {

          char c1 = s.charAt(i);
          char c2 = t.charAt(i);

          if (mapST.containsKey(c1) && mapST.get(c1) != c2)
              return false;

          if (mapTS.containsKey(c2) && mapTS.get(c2) != c1)
              return false;

          mapST.put(c1, c2);
          mapTS.put(c2, c1);
      }

      return true;
  }
```

## Edge cases
- Counting only characters and deciding.
- s = "abcd", t = "abab"

## New Learnings
- Storing last index