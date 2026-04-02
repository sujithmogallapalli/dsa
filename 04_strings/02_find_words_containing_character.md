## Problem
- You are given a 0-indexed array of strings words and a character x.
- Return an array of indices representing the words that contain the character x.

## Sample
Input: words = ["leet","code"], x = "e"
Output: [0,1]
Explanation: "e" occurs in both words: "leet", and "code". Hence, we return indices 0 and 1.

## Observations
- Note that the returned array may be in any order.

## Approaches
### Approach 1 – Linear Scan with Early Exit
- Step 1: Traverse each word.
- Step 2: Check if character exists.
- Step 3: If found → add index to result.
- Step 4: Continue until all words processed.
- Time Complexity: O(n * m), Space Complexity: O(n)

## Codes
### Linear Scan with Early Exit
```java
public List<Integer> findWordsContaining(String[] words, char x) {

    List<Integer> result = new ArrayList<>();

    for (int i = 0; i < words.length; i++) {
        if (words[i].indexOf(x) != -1) {
            result.add(i);
        }
    }

    return result;
}
```