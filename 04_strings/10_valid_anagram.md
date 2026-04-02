## Problem
- Given two strings s and t, return true if t is an anagram of s, and false otherwise.

## Samples
### Sample 1
- Input: s = "anagram", t = "nagaram"
- Output: true

### Sample 2
- Input: s = "rat", t = "car"
- Output: false

### Sample 3
- InputL s = "a😊b", t = "b😊a"
- Output: true

## Observations
- String may contain unicode characters

## Approaches
### Approach 1 – Unicode Safe Frequency Counting
- Step 1: Compare number of Unicode code points in both strings.
- Step 2: Traverse first string using codePoints().
- Step 3: Store frequency of each code point in HashMap.
- Step 4: Traverse second string using codePoints().
- Step 5: Decrease frequency for each code point.
- Step 6: If any count becomes negative or missing → return false.
- Time Complexity: O(n), Space Complexity: O(k)

### Approach 2 – Frequency Counting (Not useful for unicode characters)
- Step 1: If lengths differ → return false.
- Step 2: Count frequency of characters in first string.
- Step 3: Traverse second string and decrease frequency.
- Step 4: If any count becomes negative → not an anagram.
- Step 5: If traversal finishes successfully → strings are anagrams.
- Time Complexity: O(n), Space Complexity: O(1) (using fixed-size array)

## Codes
### Unicode Safe Frequency Counting
```java
public boolean isAnagram(String s, String t) {

    if (s.codePointCount(0, s.length()) != 
        t.codePointCount(0, t.length()))
        return false;

    Map<Integer, Integer> freq = new HashMap<>();

    s.codePoints().forEach(cp ->
        freq.put(cp, freq.getOrDefault(cp, 0) + 1)
    );

    for (int cp : t.codePoints().toArray()) {

        if (!freq.containsKey(cp) || freq.get(cp) == 0)
            return false;

        freq.put(cp, freq.get(cp) - 1);
    }

    return true;
}
```
### Frequency Counting (Not useful for unicode characters)
```java
public boolean isAnagram(String s, String t) {

    if (s.length() != t.length())
        return false;

    int[] freq = new int[26];

    for (char ch : s.toCharArray())
        freq[ch - 'a']++;

    for (char ch : t.toCharArray()) {
        freq[ch - 'a']--;
        if (freq[ch - 'a'] < 0)
            return false;
    }

    return true;
}
```

## New Learnings
- s.codePointCount(0, s.length()) → to find string length with unicode characters
- s.codePoints() → return int array