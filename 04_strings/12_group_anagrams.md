## Problem
- Given an array of strings strs, group the anagrams together. You can return the answer in any order.

## Samples
### Sample 1
- Input: strs = ["eat","tea","tan","ate","nat","bat"]
- Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
- Explanation:
  - There is no string in strs that can be rearranged to form "bat". 
  - The strings "nat" and "tan" are anagrams as they can be rearranged to form each other. 
  - The strings "ate", "eat", and "tea" are anagrams as they can be rearranged to form each other.

## Observations
- string consist of only lowercase letters

## Approaches
### Approach 1 – Frequency Signature Hashing
- Step 1: Create a HashMap where:
  key = frequency signature of characters
  value = list of strings that share that signature.
- Step 2: For each string:
    - Create a frequency array of size 26.
- Step 3: Count occurrences of each character.
- Step 4: Convert the frequency array into a string key.
- Step 5: Insert the string into the list mapped by that key.
- Step 6: After processing all strings, return all grouped lists.
- Time Complexity: O(n * k), Space Complexity: O(n)

### Approach 2 – Sorted String Signature
- Step 1: Create a HashMap where:
  key = sorted version of the string
  value = list of anagrams.
- Step 2: For each string:
    - Convert the string into a character array.
- Step 3: Sort the characters.
- Step 4: Convert the sorted array back into a string.
- Step 5: Use this sorted string as the key in the map.
- Step 6: Insert the original string into the corresponding group.
- Step 7: Return all grouped lists.
- Time Complexity: O(n * k log k), Space Complexity: O(n)

## Codes
### Frequency Signature Hashing
```java
public List<List<String>> groupAnagrams(String[] strs) {

    Map<String, List<String>> map = new HashMap<>();

    for (String str : strs) {

        int[] freq = new int[26];

        for (char ch : str.toCharArray()) {
            freq[ch - 'a']++;
        }

        String key = Arrays.toString(freq);

        map.putIfAbsent(key, new ArrayList<>());
        map.get(key).add(str);
    }

    return new ArrayList<>(map.values());
}
```

### Sorted String Signature
```java
public List<List<String>> groupAnagrams(String[] strs) {

    Map<String, List<String>> map = new HashMap<>();

    for (String str : strs) {

        char[] arr = str.toCharArray();
        Arrays.sort(arr);

        String key = new String(arr);

        map.putIfAbsent(key, new ArrayList<>());
        map.get(key).add(str);
    }

    return new ArrayList<>(map.values());
}
```

## New Learnings
- Arrays.toString(freq) → to convert an array to string 
- map.putIfAbsent(key, new ArrayList<>()) → useful while working with hashing of array of arrays
- new ArrayList<>(map.values()) → to convert Collection<List<String>> to List<List<String>>