## Problem
- You are given a string s consisting of lowercase English letters ('a' to 'z').
- Your task is to:
  - Find the vowel (one of 'a', 'e', 'i', 'o', or 'u') with the maximum frequency.
  - Find the consonant (all other letters excluding vowels) with the maximum frequency.
- Return the sum of the two frequencies.

## Sample
- Input: s = "successes"
- Output: 6
- Explanation:
  - The vowels are: 'u' (frequency 1), 'e' (frequency 2). The maximum frequency is 2.
  - The consonants are: 's' (frequency 4), 'c' (frequency 2). The maximum frequency is 4.
  - The output is 2 + 4 = 6.

## Observations
- If multiple vowels or consonants have the same maximum frequency, you may choose any one of them. 
- If there are no vowels or no consonants in the string, consider their frequency as 0.

## Approaches
### Approach 1 - Character frequency
- Step 1: Create frequency array of size 26.
- Step 2: Traverse string:
    - Increment frequency of character.
- Step 3: If character is vowel:
    - Update maxVowel.
- Step 4: Else:
    - Update maxConsonant.
- Step 5: Return sum of both maximums.
- Time Complexity: O(n), Space Complexity: O(1)  (Fixed 26 size)

### Approach 2 – HashMap Frequency + Category Max
- Step 1: Create a HashMap to store character frequency.
- Step 2: Traverse the string.
- Step 3: Update frequency using getOrDefault().
- Step 4: If vowel → update maxVowel.
- Step 5: Else → update maxConsonant.
- Step 6: Return sum of both maximums.
- Time Complexity: O(n), Space Complexity: O(k)   // distinct characters

## Codes
### Character hashing
```java
public int maxFreqSum(String s) {

    int[] freq = new int[26];
    int maxVowel = 0;
    int maxConsonant = 0;

    for (char ch : s.toCharArray()) {

        int index = ch - 'a';
        freq[index]++;

        if (isVowel(ch)) {
            maxVowel = Math.max(maxVowel, freq[index]);
        } else {
            maxConsonant = Math.max(maxConsonant, freq[index]);
        }
    }

    return maxVowel + maxConsonant;
}

private boolean isVowel(char ch) {
    return ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u';
}
```

### HashMap Frequency + Category Max
```java
public int maxFreqSum(String s) {

    Map<Character, Integer> freqMap = new HashMap<>();

    int maxVowel = 0;
    int maxConsonant = 0;

    for (char ch : s.toCharArray()) {

        int freq = freqMap.getOrDefault(ch, 0) + 1;
        freqMap.put(ch, freq);

        if (isVowel(ch)) {
            maxVowel = Math.max(maxVowel, freq);
        } else {
            maxConsonant = Math.max(maxConsonant, freq);
        }
    }

    return maxVowel + maxConsonant;
}

private boolean isVowel(char ch) {
    return ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u';
}
```

## New Learnings
- Using individual comparing of vowels instead of checking by declaring a string